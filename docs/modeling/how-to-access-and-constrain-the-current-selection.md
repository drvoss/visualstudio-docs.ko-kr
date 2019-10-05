---
title: '방법: 현재 선택 항목 액세스 및 제약'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cc93f276dae3caeec08a21a74e3bdcaa365fee9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993461"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>방법: 현재 선택 항목 액세스 및 제약

도메인 특정 언어에 대 한 명령 또는 제스처 처리기를 작성 하는 경우 사용자를 마우스 오른쪽 단추로 클릭 하는 요소를 확인할 수 있습니다. 또한 일부 셰이프나 필드 선택에서 방지할 수 있습니다. 예를 들어, 사용자는 아이콘 decorator가 때 모양을 포함 하는 대신 선택 되도록 정렬할 수 있습니다. 이 방식으로 선택 제한 작성 해야 하는 처리기의 수를 줄입니다. 또한 쉽게 decorator를 방지 하지 않고도 셰이프에서 아무 곳 이나 클릭 수 있는 사용자에 대 한 합니다.

## <a name="access-the-current-selection-from-a-command-handler"></a>명령 처리기에서 현재 선택 영역에 액세스

도메인 특정 언어에 대 한 명령 집합 클래스에 사용자 지정 명령에 대 한 명령 처리기를 포함합니다. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> , 도메인 특정 언어에 대 한 명령 집합 클래스 파생 되는 클래스, 현재 선택 영역에 액세스 하기 위한 몇 명의 멤버를 제공 합니다.

명령에 따라 명령 처리기는 모델 디자이너, 모델 탐색기 또는 활성 창에 선택을 해야 합니다.

### <a name="to-access-selection-information"></a>선택 정보에 액세스 하려면

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 클래스는 현재 선택 영역에 액세스 하는 다음 멤버를 정의 합니다.

    |멤버|설명|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 메서드|반환 `true` 모델 디자이너에서 선택한 요소 중 하나라도 구획 모양을;이 고, 그렇지 `false`합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 메서드|반환 `true` 다이어그램이 모델 디자이너에서 선택 되었으면이 고, 그렇지 않은 경우 `false`합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 메서드|반환 `true` 정확히 한 개의 요소가 고, 그렇지 않으면 모델 디자이너에서 선택한 `false`합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 메서드|반환 `true` 정확히 한 개의 요소가 고, 그렇지 않으면 현재 창에서 선택한 `false`합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 속성|모델 디자이너에서 선택한 요소의 읽기 전용 컬렉션을 가져옵니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 속성|활성 창에서 선택한 요소의 읽기 전용 컬렉션을 가져옵니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 속성|모델 디자이너에서 선택 항목의 기본 요소를 가져옵니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 속성|활성 창에 있는 선택 항목의 기본 요소를 가져옵니다.|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> 의 속성을 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 클래스에 대 한 액세스를 제공는 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> 모델 디자이너 창을 나타내는 모델 디자이너에서 선택한 요소에 추가 액세스를 제공 하는 개체.

3. 또한 생성된 된 코드 탐색기 도구 창 속성을 정의 하 고 명령에는 속성 탐색기 선택 도메인 특정 언어에 대 한 클래스를 설정 합니다.

    - 탐색기 도구 창 속성 도메인별 언어 탐색기 도구 창 클래스의 인스턴스를 반환 합니다. 탐색기 도구 창 클래스에서 파생 되는 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> 클래스 및 도메인 특정 언어에 대 한 모델 탐색기를 나타냅니다.

    - `ExplorerSelection` 속성 도메인 특정 언어에 대 한 모델 탐색기 창에서 선택한 요소를 반환 합니다.

## <a name="determine-which-window-is-active"></a>어떤 창이 활성 창인지 확인

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 인터페이스 포함 shell에서 현재 선택 상태에 대 한 액세스를 제공 하는 멤버를 정의 합니다. 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 패키지 클래스 또는 통해 도메인 특정 언어에 대 한 명령 집합 클래스에서 개체를 `MonitorSelection` 각각의 기본 클래스에 정의 된 속성입니다. 패키지 클래스에서 파생 되는 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> 클래스 및 명령 집합 클래스에서 파생 되는 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 클래스입니다.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>어떤 유형의 창이 활성 명령 처리기에서 확인 하려면

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> 의 속성을 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 반환 클래스는 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> shell에서 현재 선택 상태에 대 한 액세스를 제공 하는 개체입니다.

2. 합니다 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> 의 속성을 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 인터페이스 활성 창에서 다를 수 있는 활성 선택 영역 컨테이너를 가져옵니다.

3. 명령에는 설정 클래스를 활성 창 유형을 확인 하려면 도메인 특정 언어를 추가 합니다.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>선택 영역을 제한 합니다.

선택 규칙을 추가 하 여 사용자가 모델에서 요소를 선택할 때에 요소가 선택 되어 제어할 수 있습니다. 예를 들어, 사용자 수의 요소를 하나의 단위로 처리할 수 있도록 선택 규칙을 사용할 수 있습니다.

### <a name="to-create-a-selection-rule"></a>선택 규칙을 만들려면

1. DSL 프로젝트에 사용자 지정 코드 파일을 만듭니다

2. 파생 되는 선택 규칙 클래스를 정의 합니다 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> 클래스입니다.

3. 재정의 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> 선택 조건을 적용할 선택 규칙 클래스의 메서드.

4. 사용자 지정 코드 파일에 ClassDiagram 클래스에 대 한 partial 클래스 정의 추가 합니다.

     합니다 `ClassDiagram` 클래스에서 파생 되는 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> 클래스 및 생성 된 코드 파일에서 Diagram.cs, DSL 프로젝트에서 정의 됩니다.

5. 재정의 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 의 속성을 `ClassDiagram` 사용자 지정 선택 규칙을 반환 하는 클래스입니다.

     기본 구현 된 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 속성 선택 영역을 수정 하지 않는 선택 규칙 개체를 가져옵니다.

### <a name="example"></a>예제

다음 코드 파일에는 처음에 선택 된 도메인 도형의 모든 인스턴스를 포함 하도록 선택을 확장 선택 규칙을 만듭니다.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>참고자료

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>