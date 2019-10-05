---
title: 'UML 클래스 다이어그램: 참조 | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2be23466642357d19dad52407fcb9bf82e843c5b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424484"
---
# <a name="uml-class-diagrams-reference"></a>UML 클래스 다이어그램: 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 클래스 다이어그램에서는 애플리케이션에서 내부적으로, 그리고 사용자와의 통신에 사용되는 개체 및 정보 구조에 대해 설명합니다. 특정 구현에 대한 참조 없이 정보에 대해 설명합니다. 해당 클래스 및 관계는 데이터베이스 테이블, XML 노드 또는 소프트웨어 개체 컴퍼지션과 같은 다양한 방법으로 구현할 수 있습니다.  
  
> [!NOTE]
> 이 항목에서는 UML 클래스 다이어그램에 대해 설명합니다. 프로그램 코드를 시각화하는 데 사용되는 또 다른 클래스 다이어그램인 .NET 클래스 다이어그램이 있습니다. 자세한 내용은 [보기 클래스와 형식 디자인 및](http://go.microsoft.com/fwlink/?LinkId=142231)합니다.  
  
 UML 클래스 다이어그램을 만들려면에 **아키텍처** 메뉴 선택 **새 UML 또는 레이어 다이어그램**합니다. UML 클래스 다이어그램을 그리는 방법에 대 한 자세한 내용은 참조 하세요. [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)합니다. 만들고 모델링 다이어그램을 그리는 방법에 대 한 자세한 내용은 참조 하세요. [편집 UML 모델 및 다이어그램](../modeling/edit-uml-models-and-diagrams.md)합니다.  
  
 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [아키텍처 및 모델링 도구에 대한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.  
  
## <a name="reading-class-diagrams"></a>클래스 다이어그램 읽기  
 이 섹션의 표에서는 UML 클래스 다이어그램에서 확인할 수 있는 요소에 대해 설명합니다. 이들 요소의 속성에 대한 자세한 내용은 다음 항목을 참조하세요.  
  
- [UML 클래스 다이어그램 형식의 속성](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
- [UML 클래스 다이어그램 특성의 속성](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [UML 클래스 다이어그램 작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [UML 클래스 다이어그램 연결의 속성](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
  ![속성과 관계를 보여 주는 세 개의 클래스](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
| **셰이프** |       **요소**        |                                                                                                                                                             **설명**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **클래스**         |                                                           지정된 구조 또는 동작 특성을 공유하는 개체의 정의입니다. 자세한 내용은 [uml 형식의 속성 클래스 다이어그램](../modeling/properties-of-types-on-uml-class-diagrams.md)합니다.                                                            |
|     1     |        분류자        |                                                                                                             클래스, 인터페이스 또는 열거형의 일반 이름입니다. 구성 요소, 사용 사례 및 행위자도 분류자입니다.                                                                                                             |
|     2     | 축소/확장 컨트롤 |                                                                                         분류자 세부 정보가 보이지 않으면 분류자의 왼쪽 위에 있는 확장기를 클릭합니다. 각 세그먼트에서 [+]를 클릭해야 할 수도 있습니다.                                                                                         |
|     3     |      **특성**       |   각 분류자 인스턴스에 연결된 형식화된 값입니다.<br /><br /> 특성을 추가 하려면 클릭 합니다 **특성** 섹션 및 키를 누릅니다 **ENTER**합니다. 특성의 서명을 입력합니다. 자세한 내용은 [속성의 특성을 UML 클래스 다이어그램](../modeling/properties-of-attributes-on-uml-class-diagrams.md)합니다.   |
|     4     |      **연산**       | 분류자 인스턴스가 실행할 수 있는 메서드 또는 함수입니다. 작업을 추가 하려면 클릭 합니다 **Operations** 섹션 및 키를 누릅니다 **ENTER**합니다. 작업의 서명을 입력합니다. 자세한 내용은 [클래스 다이어그램에 UML 작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md)합니다. |
|     5     |     **연결**      |                                                                  두 분류자의 멤버 간 관계입니다. 자세한 내용은 [UML 연결의 속성 클래스 다이어그램](../modeling/properties-of-associations-on-uml-class-diagrams.md)합니다.                                                                   |
|    5a     |     **집계**      |                                                                                                    공유된 소유권 관계를 나타내는 연결입니다. 합니다 **집계** 소유자 역할의 속성 **공유**합니다.                                                                                                     |
|    5b     |     **컴퍼지션**      |                                                                                                      전체-부분 관계를 나타내는 연결입니다. 합니다 **집계** 소유자 역할의 속성 **복합**합니다.                                                                                                      |
|     6     |   **연결 이름**   |                                                                                                                                         연결의 이름입니다. 이름은 비워 둘 수 있습니다.                                                                                                                                          |
|     7     |      **역할 이름**       |                       역할의 이름(연결의 한쪽 끝)입니다. 연결된 개체를 참조하는 데 사용됩니다. 이전 그림에서 순서 `O`의 경우 `O.ChosenMenu`는 연결된 메뉴입니다.<br /><br /> 각 역할에는 연결 속성에 나열되는 고유한 속성이 있습니다.                       |
|     8     |     **다중성**     |                                         다른 끝에 있는 각 개체에 연결할 수 있는 이 끝에 있는 개체 수를 나타냅니다. 예제에서 각 순서는 정확히 하나의 메뉴에 연결되어야 합니다.<br /><br /> **\\** \* 수행할 수 있는 링크의 수에 제한이 없어집니다 임을 의미 합니다.                                         |
|     10     |    **일반화**    |  합니다 *특정* 분류자에서 정의 파트를 상속 합니다 *일반* 분류자입니다. 일반 분류자는 연결선 끝의 화살표에 있습니다. 특정 분류자는 특성, 연결 및 작업을 상속합니다.<br /><br /> 사용 된 **상속** 도구를 두 분류자 간에 일반화를 만듭니다.   |
  
 ![인터페이스 및 열거형을 포함 하는 패키지](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|모양|요소|설명|  
|-----------|-------------|-----------------|  
|10|**Interface**|개체의 외부적으로 표시되는 동작 파트에 대한 정의입니다. 자세한 내용은 [uml 형식의 속성 클래스 다이어그램](../modeling/properties-of-types-on-uml-class-diagrams.md)합니다.|  
|11|**열거형**|일련의 리터럴 값으로 구성되는 분류자입니다.|  
|12|**패키지**|분류자, 연결, 작업, 수명선, 구성 요소 및 패키지의 그룹입니다. 논리 클래스 다이어그램에서 보면 멤버 분류자 및 패키지는 패키지 내에 포함됩니다.<br /><br /> 이름은 패키지 내에서 범위가 지정 됩니다 있도록 **Class1** 내 **Package1** 별개인 **Class1** 패키지 외부의 합니다. 일부분으로 패키지의 이름을 표시 합니다 **정규화 된 이름** 콘텐츠의 속성입니다.<br /><br /> 설정할 수 있습니다 합니다 **연결 된 패키지** 패키지를 가리키는 모든 UML 다이어그램의 속성입니다. 해당 다이어그램에서 만든 모든 요소가 패키지 파트가 됩니다. 패키지 아래 나타납니다 **UML 모델 탐색기**합니다.|  
|13|**Import**|한 패키지에 또 다른 패키지의 모든 정의가 포함됨을 나타내는 패키지 간의 관계입니다.|  
|14|**Dependency**|화살촉 끝의 분류자가 변경되면 종속 분류자의 정의 또는 구현이 변경될 수 있습니다.|  
  
 ![연결선과 롤리팝으로 표시 된 구현](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|모양|**요소**|설명|  
|-----------|-----------------|-----------------|  
|15|**인식**|클래스는 인터페이스를 통해 정의된 작업 및 특성을 구현합니다.<br /><br /> 사용 된 **상속** 도구를 클래스와 인터페이스 간에 인식을 만듭니다.|  
|16|**인식**|같은 관계의 대체 표현입니다. 롤리팝 기호의 레이블은 인터페이스를 나타냅니다.<br /><br /> 이 표현을 만들려면 기존 인식 관계를 선택합니다. 작업 태그는 연결 주변에 나타납니다. 작업 태그를 클릭 한 다음 클릭 **롤리팝으로 표시**합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [UML 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)   
 [UML 클래스 다이어그램 형식의 속성](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML 클래스 다이어그램 특성의 속성](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML 클래스 다이어그램 작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML 클래스 다이어그램 연결의 속성](../modeling/properties-of-associations-on-uml-class-diagrams.md)
