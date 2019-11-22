---
title: Edit UML models and diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00ac30cc7e9ee3aff0dd64f015a4b4954972c09a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295529"
---
# <a name="edit-uml-models-and-diagrams"></a>UML 모델 및 다이어그램 편집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

여러 다른 형식의 다이어그램에서 제공하는 뷰를 통해 UML 모델을 만들고 편집할 수 있습니다. 이러한 다이어그램은 시스템에 대한 여러 관점을 제공하여 해당 디자인 및 요구 사항의 다양한 측면을 이해하고 논의하는 데 도움을 줍니다. Visual Studio는 가장 자주 사용되는 형식의 UML 다이어그램 중 5가지에 대한 템플릿을 제공합니다.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 이 항목에서는 다양한 다이어그램 형식에서 공통된 모델을 편집하는 기술에 대해 설명합니다. For more information that is specific to particular types of diagrams, see [Create models for your app](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>이 항목의 내용

- [UML Diagrams are Views of a UML Model](#Views)

- [Creating UML Modeling Diagrams](#Creating)

- [Drawing UML Modeling Diagrams](#Drawing)

- [Editing Shapes and Connectors](#Editing)

- [Undoing Changes to the Model](#Undo)

- [Sharing Elements between Diagrams](#Sharing)

- [Copying Elements and Groups of Related Elements](#Copying)

- [Deleting a Model Element or its Views](#Deleting)

- [Searching text in a diagram](#Searching)

- [Preparing a Diagram for Presentation](#presentation)

- [Extending the UML Designers](#extensions)

## <a name="Views"></a> UML Diagrams are Views of a UML Model
 모델링 프로젝트에서만 UML 다이어그램을 만들고 사용할 수 있습니다. For more information about how to create diagrams and projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

- 모델링 프로젝트에는 단일 UML 모델이 포함됩니다. 프로젝트의 모든 UML 다이어그램은 UML 모델의 뷰입니다.

- You can see the model in **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

- 다이어그램의 각 모양은 모델의 요소 뷰입니다. 다이어그램에 새 모양을 배치하면 모델에 새 요소가 생성됩니다.

- When you save any diagram, Visual Studio saves the whole model, all its diagrams, and the modeling project file.

## <a name="Creating"></a> Creating UML Modeling Diagrams

1. On the **Architecture** menu in Visual Studio, click **New UML or Layer Diagram**.

2. 다이어그램을 선택하고 이름을 지정합니다.

3. In **Add to modeling project**, select an existing modeling project, or select **Create a new modeling project**.

   > [!NOTE]
   > 모델링 다이어그램은 모델링 프로젝트 내에 있어야 합니다.

   솔루션 탐색기에서 기존 모델링 프로젝트에 다이어그램을 추가할 수도 있습니다. Right-click the modeling project, point to **Add**, and then click **New Item**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>빈 UML 모델링 프로젝트를 만들려면

- On the **File** menu, point to **New**, click **Project**, and in the **New Project** dialog box, double-click **Modeling Projects**.

  For more information about how to manage modeling projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="Drawing"></a> Drawing UML Modeling Diagrams
 모델링 다이어그램에는 관계로 연결된 모델 요소 컬렉션이 표시됩니다. 각 요소는 모양으로 표시되고 각 관계는 두 모양 간의 연결선으로 표시됩니다.

 요소와 관계에 대해 하나씩, 두 종류의 도구가 있습니다. For example, in the UML class diagram Toolbox, **Class** is an element tool, and **Association** is a relationship tool.

> [!NOTE]
> If you want information that is specific to particular diagram types, see [Create models for your app](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>UML 모델링 다이어그램에서 요소 및 관계를 만들려면

1. 모델 요소를 만들려면 도구 상자에서 요소 도구를 클릭한 다음 표시할 다이어그램을 클릭합니다. 요소를 만든 후 해당 핸들을 끌어 크기와 모양을 조정합니다.

    다른 요소 안에 새 요소를 배치할 수 있는 경우도 있습니다. 예를 들어 UML 클래스 다이어그램에서 패키지 안에 클래스를 배치할 수 있습니다.

   > [!NOTE]
   > If you cannot see the toolbox, click **Toolbox** on the **View** menu.

2. 관계를 만들려면 관계 도구를 클릭하고 관계를 시작할 요소를 클릭한 다음 관계를 끝낼 요소를 클릭합니다.

    각 형식의 관계는 서로 다른 형식의 요소에서 시작하거나 끝날 수 있습니다. 예를 들어 UML 클래스 다이어그램에서 연결 관계는 주석 요소에서 시작하거나 끝날 수 없습니다.

   > [!NOTE]
   > 동일한 도구를 여러 번 사용하려면 해당 도구를 두 번 클릭합니다. When you have finished, click the **Pointer** tool.

   일부 종류의 다이어그램에서는 단순 도형을 그릴 수도 있습니다. 이러한 모양은 모델의 일부가 아니라 다이어그램의 일부로 관심을 끌거나 다양한 영역으로 나누는 데 사용할 수 있습니다.

## <a name="Editing"></a> Editing Shapes and Connectors
 모양의 크기 또는 색을 조정하거나 연결선을 바꾸는 경우 기본 모델에는 영향을 주지 않습니다. 그러나 다이어그램 또는 UML 모델 탐색기에서 모양의 이름을 바꾸는 경우 UML 모델 탐색기 및 해당 요소를 표시하는 다른 모든 다이어그램에서 요소의 이름이 바뀝니다.

> [!NOTE]
> 선택한 속성으로 요소 그룹 또는 요소를 만들 수 있는 새 도구 상자 항목을 만드는 간단한 방법이 있습니다. For more information, see [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

 다음 그림에서는 모양의 크기나 이름을 변경하는 방법을 보여 줍니다.

 ![Adjusting a model element](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> 기본 제공 명령은 모양을 깔끔하게 맞추는 명령을 포함하지 않습니다. However, you can easily create your own alignment command by copying the code in the example in [Display a UML model on diagrams](../modeling/display-a-uml-model-on-diagrams.md).

 다음 그림에서는 연결선이나 해당 레이블의 경로와 위치를 조정하는 방법을 보여 줍니다.

 ![Adjusting a connector](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>연결선의 한쪽 끝을 다른 모양으로 이동하려면

1. 다음 작업 중 하나를 수행합니다.

   - Press **CTRL** and move the end.

     \- 또는 -

   - Right-click the connector and then click **Reconnect**.

2. 이동할 연결선의 끝을 클릭합니다.

3. 연결선을 이동할 모양을 클릭합니다.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>요소, 관계 또는 다이어그램의 색이나 기타 속성을 변경하려면

- Click the element and set the fields in the **Properties** window.

     If you cannot see the **Properties** window, right-click the element, and then click **Properties.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>모델링 다이어그램을 확대/축소하려면

- Press and hold the **CTRL** key while you rotate the mouse wheel.

     \- 또는 -

- Press and hold **CTRL+SHIFT**, and then click the left or right mouse button.

     \- 또는 -

- On the **Architecture Designers** toolbar, click the plus sign ( **+** ) or minus sign ( **-** ), or choose a zoom level.

## <a name="Searching"></a> Searching in a Diagram
 빠른 찾기 함수는 다이어그램에서 항목을 찾습니다. You must set **Look in:** to **Current Document**.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>모델링 다이어그램에서 텍스트를 검색하려면

1. Press **CTRL+F**.

     \- 또는 -

     On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find**.

    > [!NOTE]
    > In the **Find and Replace** dialog box, you must leave the **Look in** field set to **Current Document**. 다른 옵션은 지원되지 않습니다.

2. Type the text that you want to find, and then click **Find Next**.

    > [!NOTE]
    > 찾으려는 텍스트가 축소된 모양 안에 있으면 모양이 강조 표시됩니다. Expand the shape, and then click **Find Next** again.

## <a name="Undo"></a> Undoing Changes to the Model
 You can undo and redo changes that you have made to the model and diagrams by using the **Undo** and **Redo** commands on the **Edit** menu.

 **Each modeling project has a single stack of changes.** 모델 및 다이어그램에 수행한 모든 변경 내용이 이 스택에 유지됩니다. 스택에는 다이어그램 간의 포커스 변경도 포함됩니다. 실행 취소 명령은 이 스택의 변경 내용을 취소합니다.

 예를 들어 Diagram1 변경, 포커스를 Diagram2로 변경, Diagram2 변경 작업을 수행한다고 가정합니다. 변경 내용을 취소하는 경우 첫 번째 실행 취소는 마지막 변경을 취소하고, 다음 실행 취소는 포커스를 다시 Diagram1로 전환하고, 세 번째 실행 취소는 Diagram1 변경 내용을 취소합니다.

 **Closing a diagram truncates the stack of changes.** 다이어그램을 닫으면 해당 다이어그램에서 수행한 변경 내용을 취소할 수 없으며, 모델 또는 해당 다이어그램에 대한 이전 변경 내용을 취소할 수 없습니다.

 **You cannot undo while you are editing a property.** 속성 창이나 다이어그램의 레이블에서 속성을 편집하는 경우 해당 속성에 대한 변경 내용만 취소할 수 있습니다. Enter 키를 눌러 속성 변경을 완료하거나 Esc 키를 눌러 취소합니다. 그런 다음 모델 및 다이어그램의 변경 내용을 취소할 수 있습니다.

 **Closing a diagram without saving might not have the effect you expect.** 변경 작업을 수행한 후 저장하지 않고 다이어그램을 닫는 경우 변경 내용이 모델에 그대로 유지됩니다. 저장하지 않고 닫으려면 전체 모델을 닫는 것이 좋습니다.

## <a name="Sharing"></a> Sharing Elements between Diagrams
 모델 요소의 특정 인스턴스가 다이어그램에 두 번 이상 표시되도록 만들 수 있습니다. 클래스, 인터페이스, 구성 요소, 사용 사례 및 행위자에 적용됩니다.

 이 기능은 각 다이어그램에 다른 관계 그룹을 표시하려는 경우에 유용합니다. 예를 들어 한 다이어그램에 Customer 및 Address 클래스 간의 연결을 표시할 수 있습니다. 다른 다이어그램에는 Postal Area에 대한 연결과 함께 Address 클래스를 다시 표시할 수 있습니다.

 다이어그램에서 뷰 중 하나를 선택하거나 UML 모델 탐색기에서 선택하여 해당 이름과 같은 모델 요소의 속성을 변경할 수 있습니다.

 각 종류의 다이어그램에서 일부 종류의 모델 요소만 표시할 수 있습니다. 예를 들어 구성 요소 다이어그램에는 사용 사례를 표시할 수 없습니다. 따라서 다음 절차는 모델 요소와 다이어그램의 일부 조합에 대해서만 작동합니다.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>UML 모델 탐색기를 사용하여 모델 요소의 새 뷰를 추가하려면

1. To open **UML Model Explorer**, on the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. Drag the model element from **UML Model Explorer** to a compatible diagram in the same project.

     다른 다이어그램이나 동일한 다이어그램의 뷰에 추가로, 모델 요소의 뷰를 제공하는 모양이 나타납니다.

    > [!NOTE]
    > 클래스 또는 구성 요소를 시퀀스 다이어그램으로 끌어올 경우 다른 결과가 나타납니다. 이 경우 형식이 해당 클래스 또는 구성 요소인 새 수명선이 생성됩니다. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>참조 붙여넣기를 사용하여 모델 요소의 새 뷰를 추가하려면

1. Right-click an existing element, and then click **Copy**.

    - 동시에 여러 요소를 복사할 수 있습니다. Hold down the CTRL key while you click each element, right-click one of them, and then click **Copy**.

2. Right-click an empty part of a compatible diagram, and then click **Paste Reference**.

     동일한 요소의 다른 뷰가 나타납니다.

    > [!NOTE]
    > This differs from the **Paste** command, which creates a new element in the model. For more information, see [Copying Elements and Groups of Related Elements](#Copying).

> [!NOTE]
> 관계로 이미 연결된 두 모델 요소의 뷰를 다이어그램에 추가하는 경우 관계 뷰도 다이어그램에 표시됩니다. 다이어그램에서 요소 중 하나를 제거하거나 모델에서 관계를 삭제해야만 이 뷰를 삭제할 수 있습니다.

## <a name="Copying"></a> Copying Elements and Groups of Related Elements
 모델 요소를 복사하여 붙여넣을 수 있으며, 요소 간의 관계와 함께 요소 그룹을 복사하여 붙여넣을 수 있습니다.

> [!NOTE]
> The **Paste** and **Paste Reference** commands have different effects. **Paste** creates new elements whose properties are like those of the copied elements. **Paste Reference** creates new views of the same elements.

#### <a name="to-copy-elements-and-their-relationships"></a>요소 및 해당 관계를 복사하려면

1. 복사할 요소가 포함된 다이어그램에서 하나 이상의 요소를 선택합니다.

    > [!NOTE]
    > 요소 그룹에 포함된 경우를 제외하고 관계는 복사할 수 없습니다.

2. On the **Edit** menu, click **Copy**.

3. 다른 다이어그램에 요소를 복사하려는 경우 새 다이어그램을 만들거나 기존 다이어그램을 엽니다.

4. On the **Edit** menu, click **Paste**.

    - 서로 연결하는 모든 관계의 복사본과 함께 요소의 복사본이 나타납니다.

    - 각각의 새 요소에 자동으로 생성된 새 이름이 지정됩니다.

5. 새 요소와 관계의 위치, 이름 및 기타 속성을 조정합니다.

> [!NOTE]
> 예를 들어 두 모델이 동일한 솔루션에 있는 경우 모델 간에 모델 요소를 복사할 수 없습니다. 그러나 다이어그램 간에는 요소를 복사할 수 있습니다.

#### <a name="to-copy-an-entire-diagram"></a>전체 다이어그램을 복사하려면

1. 새 다이어그램을 만듭니다.

2. 기존 다이어그램에서 모든 요소를 선택하고 복사한 다음 새 다이어그램에 붙여넣습니다.

   솔루션 탐색기에서 복사 및 붙여넣어 다이어그램을 복제할 수는 없습니다.

## <a name="Deleting"></a> Deleting a Model Element or its Views
 일부 종류의 요소, 특히 분류자는 모델에서 삭제하지 않고 다이어그램에서 제거할 수 있습니다. 분류자는 클래스 다이어그램, 구성 요소 다이어그램 및 사용 사례 다이어그램에 표시되는 주요 요소입니다. 두 개 이상의 다이어그램에 표시될 수 있습니다. For these types of elements, there are two separate commands: **Remove from Diagram** and **Delete from Model**.

 반면, 다이어그램에서 관계를 삭제하는 경우 항상 모델에서 삭제됩니다.

> [!NOTE]
> UML 다이어그램에서 특정 종류의 요소에는 레이블이 있습니다. 주위에 사각형을 그려 이러한 요소를 선택하는 경우 레이블을 선택할 수 있지만 이러한 레이블을 소유하는 요소는 선택할 수 없습니다. 이러한 방식으로 선택된 요소의 하위 집합 삭제는 지원되지 않습니다. To select a subset of these elements, press and hold the **CTRL** key while you click each element.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>다이어그램에서 분류자 뷰를 제거하려면

- Right-click the element on the diagram, and then click **Remove from Diagram**.

  \- 또는 -

- Click the element on the diagram and then press the **DELETE** key.

  - 이 요소 뷰가 사라집니다. However, the element remains in the model, and you can still find it in **UML Model Explorer**. 동일한 요소의 다른 뷰도 모두 그대로 유지됩니다.

  - 이 모양에서 종료되는 모든 연결선은 다이어그램에서 제거되지만 나타내는 관계는 모델에 그대로 유지됩니다. You can see the relationship in **UML Model Explorer** under **Relationships**, under each element that it connects.

#### <a name="to-delete-an-element-from-the-model"></a>모델에서 요소를 삭제하려면

- Right-click the element either in **UML Model Explorer** or on a diagram, and then click **Delete from Model**.

  - 요소가 표시되는 모든 다이어그램에서 삭제됩니다.

  - 이 요소에서 종료되는 모든 관계도 모델에서 삭제됩니다.

#### <a name="to-delete-a-relationship-from-the-model"></a>모델에서 관계를 삭제하려면

- Right-click the relationship on a diagram or in **UML Model Explorer**, and then click **Delete from Model**.

    > [!CAUTION]
    > 모델에서 제거해야만 다이어그램에서 관계를 제거할 수 있습니다.

     관계가 모델에서 삭제되고 표시되는 모든 다이어그램에서 삭제됩니다.

## <a name="presentation"></a> Preparing a Diagram for Presentation
 다음 기능은 다이어그램의 특정 부분으로 주의를 끌거나, 설명을 추가하거나, 다이어그램을 관심 있는 여러 영역으로 나누는 데 도움이 됩니다.

- Word, PowerPoint 또는 기타 문서에 다이어그램의 일부를 복사할 수 있습니다. Select the shapes and connectors you want, right-click and then click **Copy**.

- 모양 또는 연결선의 색을 변경할 수 있습니다. Select one or more shapes and change the **Color** property. **속성** 창이 보이지 않으면 **F4**키를 누릅니다.

- On diagrams of some kinds, you can draw lines, rectangles and ellipses from the **Simple Shapes** section of the Toolbox. 이러한 모양은 UML 모델의 파트를 구성하지 않습니다.

- To label an area, you can drag a Comment from the Toolbox and then set its **Transparent** property to **True**. 단순 도형과 마찬가지로 주석은 UML 모델의 파트를 구성하지 않고 UML 모델 탐색기에 나타나지 않습니다.

- 모델 요소에 메모 및 설명을 추가하려면 주석을 만들고 요소에 연결할 수 있습니다.

### <a name="to-export-a-diagram-as-an-image"></a>다이어그램을 이미지로 내보내려면
 For more information, see [Export diagrams as images](../modeling/export-diagrams-as-images.md).

## <a name="extensions"></a> Extending the UML Designers
 UML 도구에 새 기능을 추가하고 사용자 고유의 요구에 따라 다이어그램 표기법을 조정할 수 있습니다. For more information, see [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md).

## <a name="see-also"></a>관련 항목:
 [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md) [Create models for your app](../modeling/create-models-for-your-app.md)
