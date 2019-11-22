---
title: Create layer diagrams from your code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e6cd77e785adb59fc8b2cf3b28724ed0efe1ae3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300279"
---
# <a name="create-layer-diagrams-from-your-code"></a>코드에서 레이어 다이어그램 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To visualize your software system's high-level, logical architecture, create a *layer diagram* in Visual Studio. 코드가 디자인과 일치하는지 확인하려면 레이어 다이어그램에서 코드의 유효성을 검사합니다. Visual C# .NET 및 Visual Basic .NET 프로젝트의 레이어 다이어그램을 만들 수 있습니다. To see which versions of Visual Studio support this feature, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Create a layer diagram](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 A layer diagram lets you organize Visual Studio solution items into logical, abstract groups called *layers*. 레이어를 사용하여 이러한 아티팩트가 수행하는 주요 작업 또는 시스템의 주요 구성 요소를 설명할 수 있습니다. 각 레이어에는 보다 세부적인 작업을 나타내는 다른 레이어가 포함될 수 있습니다. You can also specify the intended or existing *dependencies* between layers. 이와 같이 화살표로 나타내는 종속성은 다른 레이어가 나타내는 기능을 어느 레이어가 사용할 수 있는지 또는 현재 어느 레이어가 사용하고 있는지를 표시합니다. 코드의 아키텍처 제어를 유지하려면 다이어그램에서 의도한 종속성을 표시한 다음 해당 다이어그램에 대해 코드 유효성을 검사합니다.

## <a name="CreateDiagram"></a> Create a layer diagram
 레이어 다이어그램을 만들기 전에 솔루션에 모델링 프로젝트가 있는지 확인하십시오. See [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> 한 모델링 프로젝트에서 다른 모델링 프로젝트나 솔루션의 다른 위치로 기존 레이어 다이어그램을 추가하거나 끌어 놓거나 복사하지 마십시오. 그러면 다이어그램을 변경하더라도 원래 다이어그램의 참조가 유지됩니다. 또한 레이어 유효성 검사가 제대로 작동하지 않고 다이어그램을 열려고 할 때 요소 누락이나 기타 오류 등의 다른 문제가 발생할 수 있습니다.
>
> 그 대신, 모델링 프로젝트에 새 레이어 다이어그램을 추가합니다. 소스 다이어그램에서 새 다이어그램으로 요소를 복사합니다. 모델링 프로젝트와 새 레이어 다이어그램을 저장합니다.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>모델링 프로젝트에 새 레이어 다이어그램을 추가하려면

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **Layer Diagram**.

3. 다이어그램 이름을 지정합니다.

4. In **Add to Modeling Project**, browse to and select an existing modeling project in your solution.

     또는

     Choose **Create a new modeling project** to add a new modeling project to the solution.

    > [!NOTE]
    > 레이어 다이어그램은 모델링 프로젝트 내에 있어야 합니다. 그러나 솔루션의 다른 위치에 있는 항목에 링크를 연결할 수 있습니다.

5. 모델링 프로젝트와 레이어 다이어그램을 반드시 저장합니다.

## <a name="CreateLayers"></a> Create layers from artifacts
 프로젝트, 코드 파일, 네임스페이스, 클래스, 메서드 등 Visual Studio 솔루션 항목에서 레이어를 만들 수 있습니다. 이렇게 하면 레이어와 항목 간에 링크가 자동으로 만들어지고 레이어 유효성 검사 프로세스에 포함됩니다.

 또한 Word 문서 또는 PowerPoint 프레젠테이션과 같이 유효성 검사를 지원하지 않는 항목에 레이어를 연결하여 레이어에 사양 또는 계획을 연결할 수 있습니다. 또한 여러 앱에 공유되는 프로젝트의 파일에 레이어를 연결할 수 있지만, 유효성 검사 프로세스에는 "레이어 1", "레이어 2"와 같이 제네릭 이름으로 나타나는 레이어는 포함되지 않습니다.

 To see if a linked item supports validation, open **Layer Explorer** and examine the **Supports Validation** property of the item. See [Managing links to artifacts](#Managing).

|**대상**|**Follow these steps**|
|------------|----------------------------|
|단일 아티팩트에 대한 레이어 만들기|<ol><li>다음 소스에서 레이어 다이어그램으로 항목을 끌어옵니다.<br /><br /> <ul><li>**솔루션 탐색기**<br /><br />         예를 들어 파일이나 프로젝트를 끌어 올 수 있습니다.</li><li>코드 맵<br /><br />         See [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) and [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Class View** or **Object Browser**</li></ul><br />     레이어가 다이어그램에 나타나고 아티팩트에 연결됩니다.</li><li>연결된 코드 또는 아티팩트의 기능을 반영하도록 레이어 이름을 바꿉니다.</li></ol> **Important:**  Dragging binary files to the layer diagram does not automatically add their references to modeling project. 유효성을 검사할 이진 파일을 모델링 프로젝트에 수동으로 추가해야 합니다. **To add binary files to the modeling project** <ol><li>In **Solution Explorer**, open the shortcut menu for the modeling project, and then choose **Add Existing Item**.</li><li>In the **Add Existing Item** dialog box, browse to the binary files, select them, and then choose **OK**.     이진 파일이 모델링 프로젝트에 나타납니다.</li><li>In **Solution Explorer**, choose a binary file that you added, and then press **F4** to open the **Properties** window.</li><li>On each binary file, set the **Build Action** property to **Validate**.</li></ol>|
|선택한 모든 아티팩트에 대한 단일 레이어 만들기|모든 아티팩트를 레이어 다이어그램으로 동시에 끌어 옵니다.<br /><br /> 레이어가 다이어그램에 나타나고 모든 아티팩트에 연결됩니다.|
|선택한 각 아티팩트마다 레이어 만들기|Press and hold the **SHIFT** key while you drag all of the artifacts to the layer diagram at the same time. **Note:**  If you use the **SHIFT** key to select a range of items, release the key after you select the artifacts. 그런 다음 이 키를 다시 누른 상태로 아티팩트를 다이어그램으로 끌어 옵니다. <br /><br /> 각 아티팩트에 대한 레이어가 다이어그램에 나타나고 각 아티팩트에 연결됩니다.|
|레이어에 아티팩트 추가|아티팩트를 레이어로 끌어 옵니다.|
|연결되지 않은 새 레이어 만들기|In the **Toolbox**, expand the **Layer Diagram** section, and then drag a **Layer** to the layer diagram.<br /><br /> 레이어를 여러 개 추가하려면 이 도구를 두 번 클릭합니다. When you are finished, choose the **Pointer** tool or press the **ESC** key.<br /><br /> 또는<br /><br /> Open the shortcut menu for the layer diagram, choose **Add**, and then choose **Layer**.|
|중첩된 레이어 만들기|기존 레이어를 다른 아티팩트로 끌어 옵니다.<br /><br /> 또는<br /><br /> Open the shortcut menu for a layer, choose **Add**, and then choose **Layer**.|
|기존 레이어를 두 개 이상 포함하는 새 레이어 만들기|Select the layers, open the shortcut menu for your selection, and then choose **Group**.|
|레이어 색 변경|Set its **Color** property to the color that you want.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스에 속하지 않도록 지정합니다.|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스에 종속될 수 없도록 지정합니다.|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스 중 하나에 속해야 하도록 지정합니다.|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

 레이어의 숫자는 해당 레이어에 연결된 아티팩트의 수를 나타냅니다. 그러나 이 숫자를 읽을 때 다음 사항을 유념해야 합니다.

- 레이어가 직접 연결되지 않은 다른 아티팩트를 포함하는 아티팩트에 연결된 경우 연결된 아티팩트만 숫자에 포함됩니다. 그러나 레이어 유효성 검사 중에는 직접 연결되지 않은 다른 아티팩트도 분석을 위해 포함됩니다.

     예를 들어 레이어가 단일 네임스페이스에 연결된 경우 해당 네임스페이스에 클래스가 들어 있더라도 연결된 아티팩트의 수는 1입니다. 레이어가 네임스페이스의 각 클래스에도 연결되어 있으면 연결된 클래스가 숫자에 포함됩니다.

- 레이어가 아티팩트에 연결된 다른 레이어를 포함하면 컨테이너 레이어가 이 아티팩트에도 연결됩니다. 단, 컨테이너 레이어의 숫자에는 이러한 아티팩트가 포함되지 않습니다.

## <a name="Managing"></a> Manage links between layers and artifacts

1. On the layer diagram, open the shortcut menu for the layer, and then choose **View Links**.

     **Layer Explorer** shows the artifact links for the selected layer.

2. 다음 작업으로 이러한 링크를 관리할 수 있습니다.

|**대상**|**In Layer Explorer**|
|------------|---------------------------|
|레이어와 아티팩트 간의 링크 삭제|Open the shortcut menu for the artifact link, and then choose **Delete**.|
|한 레이어에서 다른 레이어로 링크 이동|아티팩트 링크를 다이어그램의 기존 레이어로 끌어 옵니다.<br /><br /> 또는<br /><br /> 1.  Open the shortcut menu for the artifact link, and then choose **Cut**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|한 레이어에서 다른 레이어로 링크 복사|1.  Open the shortcut menu for the artifact link, and then choose **Copy**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|기존 아티팩트 링크에서 새 레이어 만들기|아티팩트 링크를 다이어그램의 빈 영역으로 끌어 옵니다.|
|연결된 아티팩트가 레이어 다이어그램에 대한 유효성 검사를 지원하는지 확인|Look at the **Supports Validation** column for the artifact link.|

## <a name="Discovering"></a> Reverse-engineer existing dependencies
 한 레이어와 연결된 아티팩트에 다른 레이어와 연결된 아티팩트에 대한 참조가 있을 때마다 종속성이 존재합니다. 예를 들어 한 레이어의 클래스가 다른 레이어의 클래스를 포함하는 변수를 선언하는 경우입니다. 다이어그램의 레이어에 연결된 아티팩트에 대한 기존 종속성을 리버스 엔지니어링할 수 있습니다.

> [!NOTE]
> 일부 아티팩트 종류의 경우 종속성을 리버스 엔지니어링할 수 없습니다. 예를 들어 텍스트 파일에 연결된 레이어를 소스 또는 대상으로 하는 종속성은 리버스 엔지니어링되지 않습니다. To see which artifacts have dependencies that you can reverse-engineer, open the shortcut menu for one or multiple layers, and then choose **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

- Select one or multiple layers, open the shortcut menu for a selected layer, and then choose **Generate Dependencies**.

  일반적으로 존재할 수 없는 일부 종속성이 나타나는데, 이러한 종속성을 편집하여 계획된 디자인에 맞출 수 있습니다.

## <a name="EditDependencies"></a> Edit layers and dependencies to show the intended design
 시스템에 대해 변경할 내용 또는 계획된 아키텍처를 나타내려는 경우 레이어 다이어그램을 편집합니다.

|**대상**|**Perform these steps**|
|------------|-----------------------------|
|종속성 방향 변경 또는 제한|Set its **Direction** property.|
|새 종속성 만들기|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> 종속성을 여러 개 그리려면 이 도구를 두 번 클릭합니다. When you are finished, choose the **Pointer** tool or press the **ESC** key.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스에 종속될 수 없도록 지정합니다.|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스에 속하지 않도록 지정합니다.|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스 중 하나에 속해야 하도록 지정합니다.|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

## <a name="EditLayout"></a> Change how elements appear on the diagram
 해당 속성을 편집하여 레이어의 크기, 모양, 색, 위치 또는 종속성의 색을 변경할 수 있습니다.

## <a name="Codemaps"></a> Discover patterns and dependencies on a code map
 While creating layer diagrams, you might also create **code maps**. 이러한 다이어그램은 코드를 탐색하는 동안 패턴 및 종속성을 검색하는 데 도움이 됩니다. 솔루션 탐색기, 클래스 뷰 또는 개체 브라우저를 사용하여 어셈블리, 네임스페이스 및 클래스를 탐색합니다. 이러한 요소는 기존 레이어에 해당하는 경우가 많습니다. 코드 맵에 대한 자세한 내용은 다음을 참조하세요.

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)

- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)

- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>관련 항목:
 [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073) [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md) [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md) [Visualize code](../modeling/visualize-code.md)