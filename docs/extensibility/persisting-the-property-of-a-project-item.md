---
title: 프로젝트 항목의 속성 유지 | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02055e4e9f25f98193e8b27d42326589aef47762
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336112"
---
# <a name="persist-the-property-of-a-project-item"></a>프로젝트 항목의 속성 유지
프로젝트 항목, 소스 파일의 작성자와 같은 추가 속성을 유지 하려는 경우. 프로젝트 파일에서 속성을 저장 하 여이 수행할 수 있습니다.

 프로젝트의 계층 구조를 가져올 프로젝트 파일에서 속성을 유지 하는 첫 번째 단계는는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 인터페이스입니다. Automation을 사용 하거나 사용 하 여이 인터페이스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>합니다. 인터페이스를 가져온 후에 현재 선택한 프로젝트 항목을 확인 하려면 사용할 수 있습니다. 프로젝트 항목 ID를 만든 후 사용할 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 속성을 추가 합니다.

 다음 절차에서는 유지를 *VsPkg.cs* 속성 `Author` 값을 사용 하 여 `Tom` 프로젝트 파일에서 합니다.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE 개체를 사용 하 여 프로젝트 계층 구조를 가져오려면

1. VSPackage에 다음 코드를 추가 합니다.

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>DTE 개체를 사용 하 여 프로젝트 항목 속성을 유지 하려면

1. 이전 절차의 메서드에 지정 된 코드에 다음 코드를 추가 합니다.

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>IVsMonitorSelection를 사용 하 여 프로젝트 계층 구조를 가져오려면

1. VSPackage에 다음 코드를 추가 합니다.

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>프로젝트 계층 구조에 선택한 프로젝트 항목 속성을 유지 하려면

1. 이전 절차의 메서드에 지정 된 코드에 다음 코드를 추가 합니다.

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>속성은 유지 되도록 확인 하려면

1. 시작 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 다음 열거나 솔루션을 만듭니다.

2. 프로젝트 선택 항목에서 VsPkg.cs **솔루션 탐색기**합니다.

3. 중단점을 사용 하거나의 VSPackage를 로드 하 고 SetItemAttribute 실행 되는지 확인 합니다.

   > [!NOTE]
   > UI 컨텍스트에서 VSPackage를 자동 로드 하면 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>합니다. 자세한 내용은 [부하 Vspackage](../extensibility/loading-vspackages.md)합니다.

4. 닫기 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트 파일을 메모장에서 엽니다. 표시는 \<작성자 > Tom 값을 사용 하 여 태그를 다음과 같이 합니다.

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>참고자료

- [사용자 지정 도구](../extensibility/internals/custom-tools.md)