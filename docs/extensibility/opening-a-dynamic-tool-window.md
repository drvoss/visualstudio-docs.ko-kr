---
title: 동적 도구 창 열기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfb00665caae499c0088f4ba5163c85ffacdbd85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336254"
---
# <a name="open-a-dynamic-tool-window"></a>동적 도구 창을 열려면
도구 창은 일반적으로 메뉴에는 해당 하는 바로 가기 명령에서 열립니다. 그러나 때때로 특정 UI 컨텍스트의 적용 되며, UI 컨텍스트가 더 이상 적용 되 면 닫습니다 때마다 열리는 도구 창을 해야 할 수 없습니다. 이러한 유형의 도구 창 이라고 *동적* 하거나 *자동 표시*합니다.

> [!NOTE]
> 미리 정의 된 UI 컨텍스트가 목록은 참조 하세요. <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>합니다.

 경우 시작 시 동적 도구 창을 열려면 및 실패를 만들 때 수를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> 인터페이스 및 오류 조건을 테스트 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> 메서드. 시작 시 열려야 하는 동적 도구 창 있다는 것을 아는 셸에 대 한 순서 대로 추가 해야 합니다는 `SupportsDynamicToolOwner` 패키지 등록 (1로 설정) 값입니다. 이 값은 표준의 일부가 아닙니다. <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>이므로 추가 사용자 지정 특성을 만들어야 합니다. 사용자 지정 특성에 대 한 자세한 내용은 참조 하세요. [사용자 지정 등록 특성을 사용 하 여 확장명 등록](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)합니다.

 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 도구 창을 엽니다. 필요에 따라 도구 창이 생성 됩니다.

> [!NOTE]
> 사용자가 동적 도구 창을 닫을 수 있습니다. 사용자 도구 창을 다시 열 수 있도록 메뉴 명령을 만들려면 하려는 경우 메뉴 명령과 도구 창 및 사용 안 함이 고 그렇지 열리는 동일한 UI 컨텍스트에서 설정 되어야 합니다.

## <a name="to-open-a-dynamic-tool-window"></a>동적 도구 창을 열려면

1. 라는 VSIX 프로젝트를 만듭니다 **DynamicToolWindow** 라는 도구 창 항목 템플릿을 추가 하 고 *DynamicWindowPane.cs*합니다. 자세한 내용은 [도구 창으로 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.

2. 에 *DynamicWindowPanePackage.cs* 파일, DynamicWindowPanePackage 선언을 찾습니다. 추가 된 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 고 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> 도구 창을 등록 하는 특성입니다.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     위의 특성에는 Visual Studio를 닫았다가 경우 지속 되지 않는 일시적인 창으로 DynamicWindowPane 라는 도구 창을 등록 합니다. DynamicWindowPane 열릴 때마다 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> 적용 되며, 그렇지 않으면 닫힙니다.

3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 표시 됩니다. 도구 창이 표시 되지 됩니다.

4. 실험적 인스턴스에서 프로젝트를 엽니다. 도구 창이 표시 됩니다.