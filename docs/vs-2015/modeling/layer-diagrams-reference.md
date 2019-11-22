---
title: 'Layer Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd2b2d19e55cbaf9af63ddeafdbdf9f6d677c5bc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301611"
---
# <a name="layer-diagrams-reference"></a>레이어 다이어그램: 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *layer diagram* to visualize the high-level, logical architecture of your system. A layer diagram organizes the physical artifacts in your system into logical, abstract groups called *layers*. 이들 레이어는 아티팩트가 수행하는 주요 작업 또는 시스템의 주요 구성 요소를 설명합니다. 각 레이어에는 더 세부적인 작업을 설명하는 중첩된 레이어가 포함될 수도 있습니다.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 레이어 간에 의도한 종속성이나 기존 종속성을 지정할 수 있습니다. 이와 같이 화살표로 나타내는 종속성은 다른 레이어가 나타내는 기능을 어느 레이어가 사용할 수 있는지 또는 현재 어느 레이어가 사용하고 있는지를 나타냅니다. 시스템을 개별 역할 및 함수를 설명하는 레이어로 구성하면 레이어 다이어그램을 통해 코드를 더 쉽게 이해하고 다시 사용하고 유지 관리할 수 있습니다.

 레이어 다이어그램을 사용하여 다음 작업을 하는 데 도움이 됩니다.

- 시스템의 기존 또는 의도한 논리적 아키텍처를 전달합니다.

- 기존 코드와 의도한 아키텍처 간 충돌을 검색합니다.

- 시스템을 리팩터링, 업데이트하거나 발전시킬 때 변경이 의도한 아키텍처에 미치는 영향을 시각화합니다.

- 체크 인 및 빌드 작업을 통해 유효성 검사를 포함하여 개발 및 유지 관리 중에 의도한 아키텍처를 보강합니다.

  이 항목에서는 레이어 다이어그램에서 사용할 수 있는 요소에 대해 설명합니다. For more detailed information about how to create and draw layer diagrams, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md). For more information about layering patterns, visit the [Patterns & Practices site](https://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-layer-diagrams"></a>레이어 다이어그램 읽기
 ![Elements on layer diagrams](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 다음 표에서는 레이어 다이어그램에서 사용할 수 있는 요소에 대해 설명합니다.

|**Shape**|**요소**|**설명**|
|---------------|-----------------|---------------------|
|1|**Layer**|시스템에 있는 물리적 아티팩트의 논리적 그룹입니다. 이들 아티팩트는 네임스페이스, 프로젝트, 클래스, 메서드 등에 해당할 수 있습니다.<br /><br /> To see the artifacts that are linked to a layer, open the shortcut menu for the layer, and then choose **View Links** to open **Layer Explorer**.<br /><br /> For more information, see [Layer Explorer](#Explorer).<br /><br /> -   **Forbidden Namespace Dependencies** - Specifies that artifacts associated with this layer cannot depend on the specified namespaces.<br />-   **Forbidden Namespaces** - Specifies that artifacts associated with this layer must not belong to the specified namespaces.<br />-   **Required Namespaces** - Specifies that artifacts associated with this layer must belong to one of the specified namespaces.|
|2|**Dependency**|한 레이어에서 다른 레이어의 기능을 사용할 수 있지만 반대의 경우는 불가능함을 나타냅니다.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|3|**Bidirectional Dependency**|한 레이어에서 다른 레이어의 기능을 사용할 수 있고 반대의 경우도 가능함을 나타냅니다.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|4|**설명**|다이어그램 또는 다이어그램의 요소에 일반적인 메모를 추가하려면 사용합니다.|
|5|**Comment Link**|다이어그램의 요소에 주석을 연결하려면 사용합니다.|

## <a name="Explorer"></a> Layer Explorer
 솔루션에서 각 레이어를 프로젝트, 클래스, 네임스페이스, 프로젝트 파일 및 기타 소프트웨어 파트와 같은 아티팩트에 연결할 수 있습니다. 레이어의 숫자는 해당 레이어에 연결된 아티팩트의 수를 나타냅니다. 그러나 레이어의 아티팩트 수를 읽을 때 다음을 고려하세요.

- 레이어가 직접 연결되지 않은 다른 아티팩트를 포함하는 아티팩트에 연결된 경우 연결된 아티팩트만 숫자에 포함됩니다. 그러나 레이어 유효성 검사 중에는 직접 연결되지 않은 다른 아티팩트도 분석을 위해 포함됩니다.

   예를 들어 레이어가 단일 네임스페이스에 연결된 경우 해당 네임스페이스에 클래스가 들어 있더라도 연결된 아티팩트의 수는 1입니다. 레이어가 네임스페이스의 각 클래스에도 연결되어 있으면 연결된 클래스가 숫자에 포함됩니다.

- 레이어가 아티팩트에 연결된 다른 레이어를 포함하면 컨테이너 레이어가 이 아티팩트에도 연결됩니다. 단, 컨테이너 레이어의 숫자에는 이러한 아티팩트가 포함되지 않습니다.

  레이어 및 아티팩트 연결에 대한 자세한 내용은 다음을 참조하세요.

- [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)

- [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>연결된 아티팩트를 검사하려면

- On the layer diagram, open the shortcut menu for one or more layers, and then choose **View Links**.

     **Layer Explorer** opens and shows the artifacts that are linked to the selected layers. **Layer Explorer** has a column that shows each of the properties of the artifact links.

    > [!NOTE]
    > If you cannot see all of these properties, expand the **Layer Explorer** window.

    |**Column in Layer Explorer**|**설명**|
    |----------------------------------|---------------------|
    |**Categories**|클래스, 네임스페이스, 소스 파일 등의 아티팩트 종류|
    |**Layer**|아티팩트에 연결되는 레이어|
    |**Supports Validation**|If **True**, then the layer validation process can verify that the project conforms to dependencies to or from this element.<br /><br /> If **False**, then the link does not participate in the layer validation process.<br /><br /> For more information, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md).|
    |**식별자**|연결된 아티팩트에 대한 참조|

## <a name="see-also"></a>관련 항목:
 [앱용 모델 만들기](../modeling/create-models-for-your-app.md)
