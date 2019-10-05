---
title: Vspackage를 로드 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439775"
---
# <a name="loading-vspackages"></a>VSPackage 로드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage는 해당 기능이 필요한 경우에 Visual Studio에 로드 됩니다. 예를 들어, Visual Studio 프로젝트 팩터리 또는 VSPackage 구현 하는 서비스를 사용 하는 경우 VSPackage가 로드 됩니다. 이 기능은 성능 향상을 위해 가능할 때마다 사용 되는 지연 된 로드를 라고 합니다.  
  
> [!NOTE]
> Visual Studio에는 VSPackage를 로드 하지 않고, VSPackage에서 제공 하는 명령 등과 같이 특정 VSPackage 정보를 확인할 수 있습니다.  
  
 Vspackage 설정할 수 있습니다 특정 사용자 인터페이스 (UI) 컨텍스트에서 자동 로드 하려면 예를 들어 솔루션이 열려 있는 경우. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 특성이이 컨텍스트를 설정 합니다.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>특정 컨텍스트에서 VSPackage 자동 로드  
  
- 추가 된 `ProvideAutoLoad` VSPackage 특성에 특성:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     열거형된 필드를 참조 하세요. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> UI 컨텍스트 및 GUID 값의 목록에 대 한 합니다.  
  
- 중단점을 설정 합니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드.  
  
- VSPackage를 빌드 및 디버깅을 시작 합니다.  
  
- 솔루션을 로드 하거나 새로 만드십시오.  
  
     VSPackage 로드 하 고 중단점에서 중지 됩니다.  
  
## <a name="forcing-a-vspackage-to-load"></a>로드 하기 위해 VSPackage를 강제 적용  
 일부 상황에서 VSPackage 강제 로드 되도록 다른 VSPackage 해야 할 수 있습니다. 예를 들어, 간단한 VSPackage를 CMDUIContext으로 사용할 수 없는 컨텍스트에서 큰 VSPackage를 로드할 수 있습니다.  
  
 사용할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> 강제로 VSPackage를 로드 하는 방법입니다.  
  
- 이 코드를 삽입 합니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 강제로 다른 VSPackage를 로드 하는 VSPackage의 메서드:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     강제로 VSPackage를 초기화할 때 `PackageToBeLoaded` 를 로드 합니다.  
  
     강제 로드 VSPackage 통신용 쓰일 수 없습니다. 사용 하 여 [사용 및 제공 서비스](../extensibility/using-and-providing-services.md) 대신 합니다.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>사용자 지정 특성을 사용 하 여 VSPackage 등록  
 특정 한 경우 확장 프로그램에 대해 새 등록 특성을 만드는 해야 합니다. 새 레지스트리 키를 추가 하거나 기존 키를 새 값을 추가 하려면 등록 특성을 사용할 수 있습니다. 새 특성에서 파생 되어야 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 및 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 메서드.  
  
## <a name="creating-a-registry-key"></a>레지스트리 키 만들기  
 다음 코드에서는 사용자 지정 특성 만듭니다는 **사용자 지정** 등록 되는 VSPackage에 대 한 키 아래 하위 키입니다.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>기존 레지스트리 키 아래에 새 값 만들기  
 기존 키를 사용자 지정 값을 추가할 수 있습니다. 다음 코드를 VSPackage 등록 키를 새 값을 추가 하는 방법을 보여 줍니다.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [VSPackage](../extensibility/internals/vspackages.md)
