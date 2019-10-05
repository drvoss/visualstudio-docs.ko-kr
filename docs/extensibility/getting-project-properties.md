---
title: 프로젝트 속성 가져오기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f766be25015081338b887a5b08413e77f5f17f9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342521"
---
# <a name="get-project-properties"></a>프로젝트 속성 가져오기

이 연습에서는 도구 창에서 프로젝트 속성을 표시 하는 방법입니다.

## <a name="prerequisites"></a>전제 조건

Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX 프로젝트를 만들고 도구 창 추가

1. 모든 Visual Studio 확장 확장 자산을 포함 하는 VSIX 배포 프로젝트를 시작 합니다. 만들기는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트 `ProjectPropertiesExtension`합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** "vsix"를 검색 하 여 대화 상자.

2. 명명 된 사용자 지정 도구 창을 항목 템플릿을 추가 하 여 도구 창을 추가 `ProjectPropertiesToolWindow`합니다. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 에 **새 항목 추가 대화 상자**로 이동 하세요 **Visual C# 항목** > **확장성** 선택한 **사용자 지정 도구 창을**합니다. 에 **이름을** 대화 상자의 맨 아래에 있는 필드에 파일 이름을 `ProjectPropertiesToolWindow.cs`입니다. 사용자 지정 도구 창을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [도구 창으로 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.

3. 솔루션을 빌드하고 오류 없이 컴파일되는지 확인합니다.

### <a name="to-display-project-properties-in-a-tool-window"></a>도구 창에서 프로젝트 속성을 표시 하려면

1. ProjectPropertiesToolWindowCommand.cs 파일에 다음 추가 문을 사용 하 여 합니다.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. *ProjectPropertiesToolWindowControl.xaml*, 기존 단추를 제거 하 고 도구 상자에서 TreeView를 추가 합니다. 클릭 이벤트 처리기를 제거할 수도 있습니다는 *ProjectPropertiesToolWindowControl.xaml.cs* 파일입니다.

3. *ProjectPropertiesToolWindowCommand.cs*를 사용 하 여는 `ShowToolWindow()` 프로젝트를 열고 해당 속성을 읽는 방법이 TreeView에 다음 속성을 추가 합니다. ShowToolWindow에 대 한 코드는 다음과 같이 표시 됩니다.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 표시 됩니다.

5. 실험적 인스턴스에서 프로젝트를 엽니다.

6. 에 **뷰** > **기타 Windows** 클릭 **ProjectPropertiesToolWindow**합니다.

  트리 컨트롤 및 모든 프로젝트 속성의 첫 번째 프로젝트의 이름과 함께 도구 창에 표시 됩니다.