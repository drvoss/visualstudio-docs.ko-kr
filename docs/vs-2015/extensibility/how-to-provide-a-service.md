---
title: '방법: 서비스를 제공 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435918"
---
# <a name="how-to-provide-a-service"></a>방법: 서비스 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage는 다른 Vspackage에서 사용할 수 있는 서비스를 제공할 수 있습니다. 서비스를 제공 하는 VSPackage에 서비스 Visual Studio를 등록 하 고 서비스를 추가 해야 합니다.  
  
 합니다 <xref:Microsoft.VisualStudio.Shell.Package> 둘 다 클래스 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 및 <xref:System.ComponentModel.Design.IServiceContainer>합니다. <xref:System.ComponentModel.Design.IServiceContainer> 주문형 서비스를 제공 하는 콜백 메서드를 포함 합니다.  
  
 서비스에 대 한 자세한 내용은 참조 하세요. [Service Essentials](../extensibility/internals/service-essentials.md) 합니다.  
  
> [!NOTE]
> VSPackage 약 언로드되려고 할 때 Visual Studio는 VSPackage가 제공 하는 서비스에 대 한 모든 요청 배달 될 때까지 대기 합니다. 이러한 서비스에 대 한 새 요청을 허용 하지는 않습니다. 명시적으로 호출 하지 않아야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 언로드할 때 서비스를 취소 하는 방법입니다.  
  
#### <a name="implementing-a-service"></a>서비스 구현  
  
1. VSIX 프로젝트를 만듭니다 (**파일 / 새로 만들기 / 프로젝트 / Visual C# / 확장성 / VSIX 프로젝트**).  
  
2. VSPackage 프로젝트에 추가 합니다. 프로젝트 노드를 선택 합니다 **솔루션 탐색기** 클릭 **추가 / 새 항목 / Visual C# 항목 / 확장성 / Visual Studio 패키지**합니다.  
  
3. 서비스를 구현 하려면 세 가지 형식을 만들 필요 합니다.  
  
   - 서비스를 설명 하는 인터페이스입니다. 이러한 인터페이스의 대부분은 빈, 즉, 이러한 방법이 없습니다.  
  
   - 서비스 인터페이스를 설명 하는 인터페이스입니다. 이 인터페이스 메서드를 구현할 수를 포함 합니다.  
  
   - 서비스와 서비스 인터페이스를 구현 하는 클래스입니다.  
  
     다음 예제에서는 세 가지 형식의 매우 기본적인 구현을 보여 줍니다. 서비스 클래스의 생성자는 서비스 공급자를 설정 해야 합니다.  
  
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
  
### <a name="registering-a-service"></a>서비스 등록  
  
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
  
### <a name="adding-a-service"></a>서비스 추가  
  
1. 1.  VSPackage 이니셜라이저에서 서비스를 추가 하 고 서비스를 만드는 콜백 메서드를 추가 합니다. 있도록 변경 된 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. 만들기 및 서비스를 반환 하거나 만들 수 없는 경우 null 해야 하는 콜백 메서드를 구현 합니다.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio 서비스를 제공 하는 요청을 거부할 수 있습니다. 다른 VSPackage 이미 서비스를 제공 하는 경우 그렇게 수행 합니다.  
  
3. 이제 서비스를 가져올 수 있으며 해당 메서드를 사용할 수 있습니다. 이니셜라이저를에서이 보여 주지만 서비스를 사용 하려는 서비스 든 가져올 수 있습니다.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     변수의 `helloString` "Hello" 이어야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)   
 [사용 하 고 서비스를 제공 합니다.](../extensibility/using-and-providing-services.md)   
 [서비스 필수 항목](../extensibility/internals/service-essentials.md)
