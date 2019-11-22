---
title: 'UML Class Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da4e0e3bab904b660f3d843e105b7d256a63a1b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297226"
---
# <a name="uml-class-diagrams-reference"></a>UML 클래스 다이어그램: 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 클래스 다이어그램에서는 애플리케이션에서 내부적으로, 그리고 사용자와의 통신에 사용되는 개체 및 정보 구조에 대해 설명합니다. 특정 구현에 대한 참조 없이 정보에 대해 설명합니다. 해당 클래스 및 관계는 데이터베이스 테이블, XML 노드 또는 소프트웨어 개체 컴퍼지션과 같은 다양한 방법으로 구현할 수 있습니다.

> [!NOTE]
> 이 항목에서는 UML 클래스 다이어그램에 대해 설명합니다. 프로그램 코드를 시각화하는 데 사용되는 또 다른 클래스 다이어그램인 .NET 클래스 다이어그램이 있습니다. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

 To create a UML class diagram, on the **Architecture** menu, choose **New UML or Layer Diagram**. For more information about how to draw UML class diagrams, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md). For more information about how to create and draw modeling diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="reading-class-diagrams"></a>클래스 다이어그램 읽기
 이 섹션의 표에서는 UML 클래스 다이어그램에서 확인할 수 있는 요소에 대해 설명합니다. 이들 요소의 속성에 대한 자세한 내용은 다음 항목을 참조하세요.

- [UML 클래스 다이어그램 형식의 속성](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [UML 클래스 다이어그램 특성의 속성](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML 클래스 다이어그램 작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [UML 클래스 다이어그램 연결의 속성](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Three classes showing relationships and properties](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Shape** |       **요소**        |                                                                                                                                                             **설명**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **클래스**         |                                                           지정된 구조 또는 동작 특성을 공유하는 개체의 정의입니다. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        분류자        |                                                                                                             클래스, 인터페이스 또는 열거형의 일반 이름입니다. 구성 요소, 사용 사례 및 행위자도 분류자입니다.                                                                                                             |
|     2     | 축소/확장 컨트롤 |                                                                                         분류자 세부 정보가 보이지 않으면 분류자의 왼쪽 위에 있는 확장기를 클릭합니다. 각 세그먼트에서 [+]를 클릭해야 할 수도 있습니다.                                                                                         |
|     3     |      **특성**       |   각 분류자 인스턴스에 연결된 형식화된 값입니다.<br /><br /> To add an attribute, click the **Attributes** section and then press **ENTER**. 특성의 서명을 입력합니다. For more information, see [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **연산**       | 분류자 인스턴스가 실행할 수 있는 메서드 또는 함수입니다. To add an operation, click the **Operations** section and then press **ENTER**. 작업의 서명을 입력합니다. For more information, see [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Association**      |                                                                  두 분류자의 멤버 간 관계입니다. For more information, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **집계**      |                                                                                                    공유된 소유권 관계를 나타내는 연결입니다. The **Aggregation** property of the owner role is set to **Shared**.                                                                                                     |
|    5b     |     **Composition**      |                                                                                                      전체-부분 관계를 나타내는 연결입니다. The **Aggregation** property of the owner role is set to **Composite**.                                                                                                      |
|     6     |   **Association Name**   |                                                                                                                                         연결의 이름입니다. 이름은 비워 둘 수 있습니다.                                                                                                                                          |
|     7     |      **Role Name**       |                       역할의 이름(연결의 한쪽 끝)입니다. 연결된 개체를 참조하는 데 사용됩니다. 이전 그림에서 순서 `O`의 경우 `O.ChosenMenu`는 연결된 메뉴입니다.<br /><br /> 각 역할에는 연결 속성에 나열되는 고유한 속성이 있습니다.                       |
|     8     |     **Multiplicity**     |                                         다른 끝에 있는 각 개체에 연결할 수 있는 이 끝에 있는 개체 수를 나타냅니다. 예제에서 각 순서는 정확히 하나의 메뉴에 연결되어야 합니다.<br /><br /> **\\** \* means that there is no upper limit to the number of links that can be made.                                         |
|     10     |    **Generalization**    |  The *specific* classifier inherits part of its definition from the *general* classifier. 일반 분류자는 연결선 끝의 화살표에 있습니다. 특정 분류자는 특성, 연결 및 작업을 상속합니다.<br /><br /> Use the **Inheritance** tool to create a generalization between two classifiers.   |

 ![Package containing interface and enumeration](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|모양|요소|설명|
|-----------|-------------|-----------------|
|10|**Interface**|개체의 외부적으로 표시되는 동작 파트에 대한 정의입니다. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeration**|일련의 리터럴 값으로 구성되는 분류자입니다.|
|12|**패키지**|분류자, 연결, 작업, 수명선, 구성 요소 및 패키지의 그룹입니다. 논리 클래스 다이어그램에서 보면 멤버 분류자 및 패키지는 패키지 내에 포함됩니다.<br /><br /> Names are scoped within packages so that **Class1** within **Package1** is distinct from **Class1** outside that package. The name of the package appears as part of the **Qualified Name** properties of its contents.<br /><br /> You can set the **Linked Package** property of any UML diagram to refer to a package. 해당 다이어그램에서 만든 모든 요소가 패키지 파트가 됩니다. They will appear under the package in **UML Model Explorer**.|
|13|**Import**|한 패키지에 또 다른 패키지의 모든 정의가 포함됨을 나타내는 패키지 간의 관계입니다.|
|14|**Dependency**|화살촉 끝의 분류자가 변경되면 종속 분류자의 정의 또는 구현이 변경될 수 있습니다.|

 ![Realization shown with conector and lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|모양|**요소**|설명|
|-----------|-----------------|-----------------|
|15|**Realization**|클래스는 인터페이스를 통해 정의된 작업 및 특성을 구현합니다.<br /><br /> Use the **Inheritance** tool to create a realization between a class and an interface.|
|16|**Realization**|같은 관계의 대체 표현입니다. 롤리팝 기호의 레이블은 인터페이스를 나타냅니다.<br /><br /> 이 표현을 만들려면 기존 인식 관계를 선택합니다. 작업 태그는 연결 주변에 나타납니다. Click the action tag, and then click **Show as Lollipop**.|

## <a name="see-also"></a>관련 항목:
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md) [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md) [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md)
