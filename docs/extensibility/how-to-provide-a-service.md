---
title: '방법: 서비스를 제공 합니다. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a752e05e5a7c91e0e9f3d3c21f8542014a053245
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324975"
---
# <a name="how-to-provide-a-service"></a>방법: 서비스를 제공 합니다.
VSPackage는 다른 Vspackage에서 사용할 수 있는 서비스를 제공할 수 있습니다. 서비스를 제공 하는 VSPackage에 서비스 Visual Studio를 등록 하 고 서비스를 추가 해야 합니다.

 합니다 <xref:Microsoft.VisualStudio.Shell.Package> 둘 다 클래스 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 및 <xref:System.ComponentModel.Design.IServiceContainer>합니다. <xref:System.ComponentModel.Design.IServiceContainer> 주문형 서비스를 제공 하는 콜백 메서드를 포함 합니다.

 서비스에 대 한 자세한 내용은 참조 하세요. [essentials 서비스](../extensibility/internals/service-essentials.md) 합니다.

> [!NOTE]
> VSPackage 약 언로드되려고 할 때 Visual Studio는 VSPackage가 제공 하는 서비스에 대 한 모든 요청 배달 될 때까지 대기 합니다. 이러한 서비스에 대 한 새 요청을 허용 하지는 않습니다. 명시적으로 호출 하지 않아야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 언로드할 때 서비스를 취소 하는 방법입니다.

## <a name="implement-a-service"></a>서비스 구현

1. VSIX 프로젝트를 만듭니다 (**파일** > **새로 만들기** > **프로젝트** > **Visual C#**  >  **확장성** > **VSIX 프로젝트**).

2. VSPackage 프로젝트에 추가 합니다. 프로젝트 노드를 선택 합니다 **솔루션 탐색기** 누릅니다 **추가** > **새 항목** > **Visual C# 항목**  >  **확장성** > **Visual Studio 패키지**합니다.

3. 서비스를 구현 하려면 세 가지 형식을 만들 필요 합니다.

   - 서비스를 설명 하는 인터페이스입니다. 이러한 인터페이스의 대부분은 빈, 즉, 이러한 방법이 없습니다.

   - 서비스 인터페이스를 설명 하는 인터페이스입니다. 이 인터페이스 메서드를 구현할 수를 포함 합니다.

   - 서비스와 서비스 인터페이스를 구현 하는 클래스입니다.

     다음 예제에서는 세 가지 종류의 기본 구현을 보여 줍니다. 서비스 클래스의 생성자는 서비스 공급자를 설정 해야 합니다.

   ```csharp
   public class MyService : SMyService, IMyService
   {
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;
       private string myString;
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)
       {
           Trace.WriteLine(
                  "Constructing a new instance of MyService");
           serviceProvider = sp;
       }
       public void Hello()
       {
           myString = "hello";
       }
       public string Goodbye()
       {
          return "goodbye";
       }
   }
   public interface SMyService
   {
   }
   public interface IMyService
   {
       void Hello();
       string Goodbye();
   }

   ```

### <a name="register-a-service"></a>서비스 등록

1. 서비스를 등록 하려면 추가 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 서비스를 제공 하는 VSPackage를 합니다. 예를 들면 다음과 같습니다.

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     이 특성을 등록 `SMyService` Visual Studio를 사용 하 여 합니다.

    > [!NOTE]
    > 이름이 같은 다른 서비스를 대체 하는 서비스에 등록 하려면 사용 된 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>합니다. 참고 서비스의 재정의 하는 하나만 허용 됩니다.

### <a name="add-a-service"></a>서비스 추가

1. VSPackage 이니셜라이저에서 서비스를 추가 하 고 서비스를 만드는 콜백 메서드를 추가 합니다. 있도록 변경 된 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. 만들기 및 서비스를 반환 하거나 만들 수 없는 경우 null 해야 하는 콜백 메서드를 구현 합니다.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio 서비스를 제공 하는 요청을 거부할 수 있습니다. 다른 VSPackage 이미 서비스를 제공 하는 경우 그렇게 수행 합니다.

3. 이제 서비스를 가져올 수 있으며 해당 메서드를 사용할 수 있습니다. 아래 예제에서는 서비스를 사용 하 여 이니셜라이저에서 있지만 서비스를 사용 하려는 서비스 든 가져올 수 있습니다.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     변수의 `helloString` "Hello" 이어야 합니다.

## <a name="see-also"></a>참고자료
- [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)
- [사용 하 고 서비스를 제공 합니다.](../extensibility/using-and-providing-services.md)
- [서비스 필수 항목](../extensibility/internals/service-essentials.md)
