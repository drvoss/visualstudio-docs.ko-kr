---
title: Vspackage를 로드 합니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c7c2a558abc928524813419df6b7848d34f0f3e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309567"
---
# <a name="load-vspackages"></a>Vspackage를 로드 합니다.
Vspackage는 해당 기능이 필요한 경우에 Visual Studio에 로드 됩니다. 예를 들어, Visual Studio 프로젝트 팩터리 또는 VSPackage 구현 하는 서비스를 사용 하는 경우 VSPackage가 로드 됩니다. 이 기능은 성능 향상을 위해 가능할 때마다 사용 되는 지연 된 로드를 라고 합니다.

> [!NOTE]
> Visual Studio에는 VSPackage를 로드 하지 않고, VSPackage에서 제공 하는 명령 등과 같이 특정 VSPackage 정보를 확인할 수 있습니다.

 Vspackage 설정할 수 있습니다 특정 사용자 인터페이스 (UI) 컨텍스트에서 자동 로드 하려면 예를 들어 솔루션이 열려 있는 경우. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 특성이이 컨텍스트를 설정 합니다.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>특정 컨텍스트에서 VSPackage 자동 로드

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

## <a name="force-a-vspackage-to-load"></a>강제 로드 하는 VSPackage
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

     강제 로드 VSPackage 통신용 쓰일 수 없습니다. 사용 하 여 [사용 하 여 서비스를 제공 하 고](../extensibility/using-and-providing-services.md) 대신 합니다.

## <a name="see-also"></a>참고자료
- [VSPackage](../extensibility/internals/vspackages.md)
