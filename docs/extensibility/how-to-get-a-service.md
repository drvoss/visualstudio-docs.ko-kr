---
title: '방법: 서비스 가져오기 | Microsoft Docs'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3da08f41566e5b6d2a501a9e020d589b85988016
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351941"
---
# <a name="how-to-get-a-service"></a>방법: 서비스 가져오기

다른 기능에 액세스 하려면 Visual Studio 서비스를 가져올 해야 합니다. 일반적으로 Visual Studio 서비스를 사용할 수 있는 하나 이상의 인터페이스를 제공 합니다. VSPackage에서 대부분의 서비스를 가져올 수 있습니다.

파생 되는 모든 VSPackage <xref:Microsoft.VisualStudio.Shell.Package> 는 요소가 올바르게 배치 된 및 모든 글로벌 서비스를 요청할 수 있습니다. 때문에 합니다 `Package` 클래스 구현 <xref:System.IServiceProvider>에서 파생 되는 모든 VSPackage `Package` 서비스 공급자 이기도 합니다.

Visual Studio에서 로드 하는 경우는 <xref:Microsoft.VisualStudio.Shell.Package>, 전달는 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 메서드 초기화 하는 동안. 이 이라고 *사이 팅* VSPackage입니다. 합니다 `Package` 클래스를이 서비스 공급자를 래핑하며 제공를 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 서비스를 가져오기 위한 방법입니다.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>초기화는 VSPackage에서 서비스 가져오기

1. 모든 Visual Studio 확장 확장 자산을 포함 하는 VSIX 배포 프로젝트를 시작 합니다. 만들기는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트 `GetServiceExtension`합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** "vsix"를 검색 하 여 대화 상자.

2. 이제 라는 사용자 지정 명령 항목 서식 파일을 추가할 **GetServiceCommand**합니다. 에 **새 항목 추가** 대화 상자에서로 이동 **Visual C#**  > **확장성** 선택한 **사용자 지정 명령**입니다. 에 **이름을** 창의 맨 아래에 있는 필드에 명령 파일 이름을 *GetServiceCommand.cs*합니다. 사용자 지정 명령인을 만드는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-menu-command.md)

3. *GetServiceCommand.cs*의 본문을 제거는 `MenuItemCommand` 메서드 다음 코드를 추가 합니다.

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    이 코드는 SVsActivityLog 서비스를 가져오고 캐스팅을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 인터페이스를 활동 로그에 쓰는 데 사용할 수 있습니다. 예는 [방법: 활동 로그를 사용 하 여](../extensibility/how-to-use-the-activity-log.md)입니다.

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.

5. 에 **도구** 실험적 인스턴스의 메뉴 찾기는 **GetServiceCommand 호출** 단추입니다. 이 단추를 클릭 하면 표시 되어야 했다는 메시지 상자가 **활동 로그를 찾을 수 있습니다.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>도구 창 또는 컨트롤 컨테이너에서 서비스 가져오기

경우에 따라 도구 창에서 서비스 가져오기 또는 배치 되지 않습니다. 그러지 않으면 요소가 서비스를 알지 못하는 서비스 공급자를 사용 하 여 배치 된 컨테이너를 제어 해야 합니다. 예를 들어, 다음 컨트롤 내에서 활동 로그에 작성 하는 것이 좋습니다.

정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드는 모든 VSPackage에서 파생 된 처음으로 초기화 되는 캐시 된 서비스 공급자 사용 <xref:Microsoft.VisualStudio.Shell.Package> 배치 됩니다.

VSPackage는 배치 하기 전에 VSPackage 생성자가 호출 되므로 전역 서비스를 VSPackage 생성자 내에서 일반적으로 사용할 수 없습니다. [방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md) 해결 방법에 대 한 합니다.

도구 창이 나 다른 비 VSPackage 요소에서 서비스 가져오기 방법의 예는 다음과 같습니다.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>DTE 개체에서 서비스 가져오기

서비스를 가져올 수도 있습니다 <xref:EnvDTE.DTEClass> 개체입니다. 그러나 가져와야 DTE 개체를 서비스로 또는 정적 호출 하 여 VSPackage에서 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드.

DTE 개체 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>를 사용할 수 있는 사용 하 여 서비스에 대 한 쿼리 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>합니다.

DTE 개체에서 서비스를 이동 하는 방법은 다음과 같습니다.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>참고자료

- [방법: 서비스를 제공 합니다.](../extensibility/how-to-provide-a-service.md)
- [사용 하 고 서비스를 제공 합니다.](../extensibility/using-and-providing-services.md)
- [서비스 필수 항목](../extensibility/internals/service-essentials.md)