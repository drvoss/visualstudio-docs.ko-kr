---
title: Creating an Extension with VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b66aef72d9af1ef40a061d1a82d18161a416586
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345356"
---
# <a name="create-an-extension-with-a-vspackage"></a>VSPackage를 사용 하 여 확장 만들기

이 연습에서는 VSIX 프로젝트를 만들고 VSPackage 프로젝트 항목을 추가 하는 방법을 보여 줍니다. 메시지 상자를 표시 하려면 UI 셸 서비스를 가져오려는 VSPackage 사용 됩니다.

## <a name="prerequisites"></a>전제 조건

Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-vspackage"></a>VSPackage를 만듭니다

1. 라는 VSIX 프로젝트를 만듭니다 **FirstPackage**합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** "vsix"를 검색 하 여 대화 상자.

2. 프로젝트를 열면 라는 Visual Studio 패키지 항목 템플릿을 추가 **FirstPackage**합니다. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 에 **새 항목 추가** 대화 상자에서로 이동 **Visual C#**  > **확장성** 선택한 **Visual Studio 패키지**합니다. 에 **이름을** 창의 맨 아래에 있는 필드에 명령 파일 이름을 *FirstPackage.cs*합니다.

3. 프로젝트를 빌드하고 디버깅을 시작합니다.

    Visual Studio의 실험적 인스턴스가 표시 됩니다. 실험적 인스턴스에 대 한 자세한 내용은 참조 하세요. [실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다.

4. 실험적 인스턴스를 엽니다는 **도구가** > **확장 및 업데이트** 창입니다. 표시 되어야 합니다 **FirstPackage** 에서 확장 합니다. (열면 **확장 및 업데이트** Visual Studio 인스턴스에서 작업을 표시 되지 않습니다 **FirstPackage**).

## <a name="load-the-vspackage"></a>VSPackage를 로드 합니다.

이 시점에서 확장을 로드 하는 아무 것도 있기 때문에 로드 되지 않습니다. (도구 창 열기 메뉴 명령이 클릭), 해당 UI를 사용 하 여 또는 특정 UI 컨텍스트에서 VSPackage를 로드 해야 함을 지정 하 여 상호 작용할 때 일반적으로 확장을 로드할 수 있습니다. Vspackage 및 UI 컨텍스트를 로드 하는 방법에 대 한 자세한 내용은 참조 하세요. [Vspackage 로드](../extensibility/loading-vspackages.md)합니다. 이 절차에서는 솔루션을 열 때 VSPackage를 로드 하는 방법을 살펴보겠습니다.

1. 엽니다는 *FirstPackage.cs* 파일입니다. 선언에 대 한 확인을 `FirstPackage` 클래스입니다. 다음 특성을 가진 기존 특성을 바꿉니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. VSPackage 로드는 알 수 있는 메시지를 추가 해 보겠습니다. 사용 하 여 VSPackage의 `Initialize()` VSPackage 요소가 배치 된 후에 Visual Studio를 얻을 수 있으므로이 작업을 수행 하는 방법 services. (서비스를 시작 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md).) 대체는 `Initialize()` 메서드의 `FirstPackage` 가져오는 코드를 사용 하 여 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 서비스를 가져옵니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스를 호출 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 메서드.

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.

4. 실험적 인스턴스에서 솔루션을 엽니다. 했다는 메시지 상자가 나타나야 **첫 번째 패키지 내에서 initialize ()** 합니다.
