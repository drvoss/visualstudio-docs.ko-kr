---
title: 'UML Use Case Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302841"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML 사용 사례 다이어그램: 지침
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *use case diagram* to summarize who uses your application or system, and what they can do with it. To create a UML use case diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 For a video demonstration, see [Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 사용 사례 다이어그램을 사용하여 다음을 논의하고 커뮤니케이션할 수 있습니다.

- 시스템 또는 애플리케이션이 사용자, 조직 또는 외부 시스템과 상호 작용하는 시나리오

- 이러한 행위자가 달성하도록 돕는 목표

- 시스템의 범위

  사용 사례 다이어그램은 사용 사례의 세부 정보를 표시하지 않습니다. 사용 사례, 행위자 및 시스템 간의 일부 관계만 요약해서 보여 줍니다. 특히, 각 사용 사례의 목표를 달성하기 위해 단계를 수행하는 순서는 다이어그램에 표시되지 않습니다. 이러한 세부 정보는 각 사용 사례에 연결할 수 있는 다른 다이어그램 및 문서에서 설명할 수 있습니다. For more information, see [Describing Use Cases in Detail](#Details) in this topic.

  사용 사례에 대해 제공하는 설명은 판매, 메뉴, 고객 등 시스템이 작동하는 도메인과 관련된 여러 용어를 사용합니다. 이러한 용어 및 해당 관계를 명확하게 정의하는 것이 중요하며, UML 클래스 다이어그램을 사용하여 이 작업을 수행할 수 있습니다. For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

  사용 사례는 시스템에 대한 기능 요구 사항만 다룹니다. 비즈니스 규칙, 서비스 품질 요구 사항 및 구현 제약 조건과 같은 다른 요구 사항은 개별적으로 표현해야 합니다. 아키텍처 및 내부 세부 정보도 별도로 설명해야 합니다. For more information about how to define user requirements, see [Model user requirements](../modeling/model-user-requirements.md).

  이 항목에서 사용된 예제는 고객이 현지 식당에서 음식을 주문할 수 있는 웹 사이트와 관련이 있습니다.

  ![Elements in a use case diagram](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- An *actor* (1) is a class of person, organization, device, or external software component that interacts with your system. Example actors are **Customer**, **Restaurant**, **Temperature Sensor**, **Credit Card Authorizer.**

- A *use case* (2) represents the actions that are performed by one or more actors in the pursuit of a particular goal. Example use cases are **Order Meal**, **Update Menu**, **Process Payment**.

   사용 사례 다이어그램에서 사용 사례는 수행하는 행위자와 연결(3)됩니다.

- Your *system (4)* is whatever you are developing. 행위자가 다른 소프트웨어 구성 요소인 작은 소프트웨어 구성 요소일 수도 있고, 완전한 애플리케이션일 수도 있고, 여러 컴퓨터와 디바이스에 배포된 애플리케이션의 대규모 분산 제품군일 수도 있습니다. Example subsystems are **Meal Ordering Website**, **Meal Delivery Business**, **Website Version 2**.

   사용 사례 다이어그램은 시스템 또는 해당 하위 시스템에서 지원하는 사용 사례를 표시할 수 있습니다.

## <a name="BasicSteps"></a> Basic Steps for Drawing Use Case Diagrams

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-new-use-case-diagram"></a>새로운 사용 사례 다이어그램을 만들려면

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UMLUse Case Diagram**.

3. 다이어그램 이름을 지정합니다.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>사용 사례 다이어그램을 그리려면

1. Drag **Subsystem** boundaries from the toolbox onto the diagram, to represent either your whole system or its major components.

    - 시스템 또는 해당 구성 요소가 지원하는 사용 사례를 설명하지 않으려는 경우 시스템 경계 없이 사용 사례 다이어그램을 그릴 수 있습니다.

    - 필요한 경우 시스템의 모퉁이를 끌어 확장합니다.

    - 적절하게 이름을 바꿉니다.

2. Drag **Actors** from the toolbox onto the diagram (placing them outside any system boundary).

    - 행위자는 시스템과 상호 작용하는 사용자, 조직 및 외부 시스템의 클래스를 나타냅니다.

    - 이름을 바꿉니다. For example: **Customer, Restaurant, Credit card agency.**

3. Drag **Use Cases** from the toolbox onto the appropriate systems.

    - 사용 사례는 행위자가 시스템을 사용하여 수행하는 동작을 나타냅니다.

    - 행위자 자신이 이해하는 제목을 사용하여 이름을 바꿉니다. 코드와 관련된 제목을 사용하지 마세요. For example: **Order Meal, Pay for Meal, Deliver Meal**.

    - Begin with major transactions such as **Order Meal**, leaving until later smaller interactions such as **Select Menu Item**.

    - 각 사용 사례를 지원하는 시스템 또는 주요 하위 시스템에 배치합니다(외관 또는 사용자에 연결할 때만 필요한 구성 요소 무시).

    - 시스템 경계 외부에 사용 사례를 그려 특정 버전 또는 릴리스에서 시스템이 지원하지 않음을 표시할 수 있습니다.

4. Click **Association** on the toolbox, then a use case, and then an actor that participates in the use case. 이런 방식으로 각 행위자를 해당 사용 사례에 연결합니다.

5. Structure the use cases with the **Include**, **Extend** and **Generalization** relationships. 이러한 각 링크를 만들려면 도구, 소스 사용 사례, 대상을 차례로 클릭합니다. See the following section titled [Structuring Use Cases](#Structuring).

6. 사용 사례를 자세히 설명합니다. See the following section titled [Describing Use Cases in Detail](#Details).

7. 관련된 사용 사례의 서로 다른 하위 시스템이나 그룹에 초점을 두는 별도 다이어그램을 그립니다. 한 모델링 프로젝트의 모든 다이어그램은 동일한 모델의 뷰입니다.

## <a name="Actors"></a> Drawing Actors and Use Cases
 사용 사례 다이어그램의 주요 목적은 시스템과 상호 작용하는 사용자 및 이를 통해 달성하는 주요 목표를 표시하는 것입니다.

- Create **Actors** to represent classes of people, organizations, other systems, software or devices that interact with your system or subsystem.

  - To learn how to draw actors and other elements, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

  - 실제 사용자나 엔터티는 동일할 수 있지만 고유한 각 목표 집합에 대한 행위자를 형식이나 역할로 식별합니다. 예를 들어 식당 직원이 고객인 경우도 있지만 식당과 고객은 별도 행위자입니다.

- Create **Use Cases** for each of the goals that each actor seeks to achieve with the system.

  - 구현 용어가 아니라 행위자가 이해하는 단어로 사용 사례의 이름을 지정하고 설명합니다.

- Use **Associations** to link actors to use cases.

### <a name="inheritance-between-actors"></a>행위자 간 상속
 ![Use case diagram showing inheritance](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 You can draw a **Generalization** link between Actors. 예제의 클럽 고객과 같은 특수화된 행위자는 고객과 같은 일반화된 행위자의 사용 사례를 상속합니다. 화살촉은 고객과 같은 보다 일반적인 행위자를 가리켜야 합니다. 링크를 만들 때는 보다 특수화된 행위자를 먼저 가리킵니다.

 특수화된 행위자는 다른 행위자가 사용할 수 없는 자체 사용 사례를 추가로 가질 수 있습니다.

> [!CAUTION]
> 행위자가 자신을 일반화하는 일반화 관계 루프를 만들면 안 됩니다. 루프에서 오류가 발생할 수 있습니다.

### <a name="alternative-actor-icons"></a>대체 행위자 아이콘
 표준 사람 모양 대신 사용자 지정 아이콘을 사용하여 행위자를 나타낼 수 있습니다. 예를 들어 디바이스, 식당, 은행 등과 비슷하게 변경할 수 있습니다.

##### <a name="to-change-the-appearance-of-an-actor"></a>행위자의 모양을 변경하려면

1. Right-click the actor and then click **Properties**.

     **속성** 창이 열립니다.

2. Set the **Image Path** property to the location of an image file.

    - .gif, .jpg, .bmp 등 여러 이미지 형식 중 하나를 사용할 수 있습니다.

    - 솔루션을 이동하거나 복사한 경우에도 계속 사용할 수 있도록 솔루션 또는 프로젝트 소스 제어에 포함된 파일을 사용합니다.

3. 다른 사용 사례 다이어그램에서 이 모양을 복제하려면 행위자를 복사하고 다른 다이어그램에 붙여넣습니다.

    - 이미지의 변경 내용은 특정 다이어그램의 뷰에만 적용됩니다. 기본 모델 요소에는 적용되지 않습니다. UML 모델 탐색기에서 다른 다이어그램으로 행위자를 끌어오면 표준 사람 모양으로 나타납니다.

### <a name="multiplicities-between-actors-and-use-cases"></a>행위자 및 사용 사례 간의 복합성
 The association between an actor and a use case can show a *multiplicity* at each end.

 ![Use case one to one with actor](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> The multiplicities of an association on a use case diagram are hidden if they are both **1**.

 By default, each multiplicity is **1**. 모델을 엄격하게 해석할 때 복합성 1은 예를 들어 한 고객만 각 음식 주문에 관련되고 각 고객이 한 번에 하나의 음식만 주문함을 의미합니다.

 이러한 복합성을 변경할 수 있습니다.

 예를 들어 다음과 같은 가치를 제공해야 합니다.

 ![Use case showing many to many multiplicity](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- To state that several actors of the same class can take part in a single occurrence of a use case, set the multiplicity at the actor end of the association to **1..\*** .

   그림에서는 하나 이상의 식당이 동일한 음식 주문 수행에 참여할 수 있습니다.

- To show that each actor can participate at the same time in several occurrences of a use case, set the multiplicity at the use case end of the association to **\*** .

   그림에서는 각 식당이 한 번에 두 개 이상의 주문을 수행할 수 있습니다.

##### <a name="to-set-multiplicities-on-an-association"></a>연결에 복합성을 설정하려면

1. Right-click the association and then click **Properties**.

2. Expand either **First Role** or **Second Role**.

    *Role* means the element at one end of the association.

3. 목록에서 선택하여 복합성 속성을 설정합니다.

   - **1** to state that exactly one instance of this role participates in each link.

   - **1..\*** to state that one or more instance of this role participate in each link.

   - **0..1** to state that participation is optional.

   - **\*** to state that zero or more instances of this role participate in the link.

> [!NOTE]
> 대부분의 팀은 사용 사례 다이어그램에 복합성 정보를 배치하지 않고 복합성을 기본값 1로 그대로 둡니다. 대신, 사용 사례에 대한 별도 설명에서 정보를 제공합니다. 이 경우 사용 사례 다이어그램의 복합성이 모두 숨겨집니다.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>여러 다이어그램에서 행위자 또는 사용 사례 사용
 여러 다이어그램에 동일한 행위자 및 사용 사례를 표시할 수 있습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

- 한 행위자와 관련된 여러 사용 사례를 서로 다른 다이어그램에서 설명할 수 있습니다.

- 한 다이어그램을 통해 사용 사례와 연결된 행위자 및 하위 시스템을 표시하고, 다른 다이어그램을 통해 사용 사례를 포함 및 확장된 사용 사례로 구성하는 방법을 표시할 수 있습니다.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>여러 다이어그램에 동일한 행위자 또는 사용 사례를 표시하려면

1. 한 다이어그램에서 행위자 또는 사용 사례를 만듭니다.

2. 다른 사용 사례 다이어그램을 만듭니다.

3. Drag an actor or use case off **Model Explorer** onto the new diagram.

    > [!NOTE]
    > 이미 연결된 행위자 및 사용 사례를 새 다이어그램에 배치하면 항목 간의 연결이 새 다이어그램에 자동으로 표시됩니다.

## <a name="Details"></a> Describing use cases in detail
 사용 사례는 다음을 나타냅니다.

- A goal of an actor in using the system, such as **Buy a Meal**; and

- One or more *scenarios*, that is, sequences of steps performed in pursuing the goal, such as: {**Order Meal, Pay, Deliver**}. In addition to success scenarios, there might be several exception or failure scenarios, such as **Credit Card Rejected**.

  한 사용 사례를 여러 세부 수준으로 설명할 수 있습니다. 디자인의 초기 단계에서는 사용 사례 다이어그램의 이름만으로 충분합니다.  나중에 시나리오에 대한 자세한 설명을 작성할 수 있습니다.

  Visual Studio Ultimate에서 개별적으로 또는 함께 사용할 수 있는 여러 가지 방법으로 사용 사례를 설명할 수 있습니다.

- 프로젝트에 있는 하나 이상의 다른 다이어그램에 사용 사례를 연결합니다.

  - 동작 다이어그램은 루프, 분기 및 병렬 스레드가 있는 더 복잡한 프로세스를 설명하는 데 도움이 됩니다. 프로세스의 파트 간 데이터 흐름을 표시할 수도 있습니다. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  - 시퀀스 다이어그램은 여러 행위자 간의 복잡한 일련의 상호 작용을 설명하는 데 도움이 됩니다. 시퀀스 다이어그램을 사용하여 각 사용 사례에 대한 응답으로 시스템 내에서 수행되는 작업을 표시할 수도 있습니다. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

- 사용 사례를 자세히 설명하는 OneNote 페이지, 섹션 또는 단락에 사용 사례를 연결합니다.

- 텍스트, 스크린샷 등을 사용하여 사용 사례 시나리오를 설명하는 Word 문서에 사용 사례를 연결합니다. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>동일한 솔루션의 다이어그램 또는 파일에 사용 사례를 연결하려면

1. 사용 사례 시나리오를 설명하는 시퀀스 다이어그램 또는 동작 다이어그램과 같은 다이어그램을 그립니다.

2. 사용 사례 다이어그램으로 돌아갑니다.

3. 솔루션 탐색기에서 사용 사례 다이어그램의 빈 부분으로 다이어그램 또는 파일을 끌어옵니다.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Word 문서 또는 PowerPoint 프레젠테이션과 같은 솔루션 파일에 연결하려면

1. 텍스트, 스크린샷 등을 사용하여 사용 사례 시나리오를 설명하는 문서를 작성합니다.

2. 솔루션에 문서를 추가합니다.

    1. Word 문서를 솔루션과 동일한 Windows 폴더로 이동합니다.

    2. In Solution Explorer, right-click the solution, point to **Add**, and then click **Existing Item**.

    3. Navigate to the Word document and click **Add**.

         Word 문서가 솔루션 탐색기의 솔루션 폴더에 나타납니다.

3. 솔루션 탐색기에서 사용 사례 다이어그램의 빈 부분으로 Word 문서를 끌어옵니다.

     새 아티팩트가 표시됩니다.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>공유 문서, OneNote 요소 또는 웹 페이지에 연결하려면

1. 공유 요소의 URL을 가져옵니다. This can be, for example, a network file path beginning '\\\\', or a web page or Sharepoint URL beginning 'http://', or a link to a OneNote section, page, or paragraph beginning 'onenote:'.

2. In the Toolbox, click **Artifact** and then click in the use case diagram.

3. With the new artifact selected, type or paste the URL into the **Hyperlink** property.

> [!NOTE]
> 아티팩트를 두 번 클릭하여 연결하는 다이어그램 또는 문서를 열 수 있습니다.

### <a name="linking-use-cases-to-work-items"></a>작업 항목에 사용 사례 연결
 If your project uses [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] and you have [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], you can link each use case to a work item in [!INCLUDE[esprfound](../includes/esprfound-md.md)]. To learn how to make these links, see [Link model elements and work items](../modeling/link-model-elements-and-work-items.md).

 이렇게 하면 다음을 수행할 수 있습니다.

- 연결된 작업 항목에서 사용 사례를 설명합니다. 특히, 프로젝트에서 Visual Studio 공식 프로세스 템플릿을 사용하는 경우 사용 사례 작업 항목에 연결할 수 있습니다. 이 작업 항목 형식은 사용 사례의 목표와 시나리오를 설명하기 위한 필드를 제공합니다.

- 개발 중인 코드가 사용 사례를 어느 정도까지 구현하는지에 대한 보고서를 얻을 수 있도록 사용 사례에 테스트 사례를 연결합니다.

- 개발 작업의 진행률을 추적할 수 있도록 사용 사례에 작업을 연결합니다.

## <a name="Structuring"></a> Structuring Use Cases
 몇 가지 주요 사용 사례만으로 시스템의 동작을 설명하려고 해야 합니다. 각각의 큰 사용 사례는 제품 구입이나 공급업체의 관점에서 판매용 제품 제공과 같은 행위자가 달성하는 주요 목표를 정의합니다.

 이러한 목표를 명확하게 지정한 경우 각 목표를 달성하는 방법 및 기본 목표의 변형에 대한 세부 정보로 넘어갈 수 있습니다.

 사용 사례를 너무 세부적으로 분해하지 마세요. 사용 사례는 내부 작업이 아니라 사용자의 시스템 경험에 대한 것입니다. 또한 일반적으로 사용 사례를 세부적으로 구성하는 데 시간을 할애하는 것보다 코드의 초기 작업 버전을 만드는 것이 훨씬 생산적입니다.

 사용 사례 다이어그램에서 주요 사용 사례와 자세한 사용 사례 간의 관계를 요약할 수 있습니다. 다음 섹션에서는 다음 방법에 대해 설명합니다.

- [Showing the details of a use case with Include](#Include)

- [Sharing goals with Generalization](#Inheritance)

- [Separating out variant cases with Extend](#Extend)

### <a name="Include"></a> Showing the details of a use case with Include
 Use an **Include** relation to show that one use case describes some of the detail of another. In the illustration, **Order a Meal** includes **Pay**, **Choose Menu**, and **Choose Menu Item**. 각각의 포함된 자세한 사용 사례는 행위자가 포함하는 사용 사례의 전반적인 목표를 달성하기 위해 수행해야 할 수 있는 단계입니다. 화살표는 포함된 자세한 사용 사례를 가리켜야 합니다.

> [!CAUTION]
> 사용 사례가 자신을 포함하는 포함 관계 루프를 만들면 안 됩니다. 루프에서 오류가 발생할 수 있습니다.

 포함된 사용 사례를 공유할 수 있습니다. In the example, the **Order a Meal** and **Subscribe to Reviews** use cases both include **Pay**.

 ![Use cases decomposed with include](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 포함된 사용 사례의 목표 및 시나리오는 나중에 디자인하는 사용 사례에 포함될 수 있도록 독립적으로 타당해야 합니다.

 사용 사례를 포함하는 파트와 포함된 파트로 구분하면 다음과 같은 목표를 달성하는 데 유용합니다.

- 사용 사례 설명을 다양한 세부 레이어로 구성합니다.

- 여러 사용 사례에서 공유 시나리오를 반복하지 마세요.

#### <a name="Steps"></a> Defining the order of the detailed steps
 자세한 단계를 수행해야 하는 순서 및 각 단계가 항상 필요한지 여부에 대해서는 사용 사례 다이어그램에 표시되지 않습니다.

 To make the order of the steps clear, you can use an **Artifact** to attach a separate document to the including use case. 다음 예제에서는 음식 주문 사용 사례에 동작 다이어그램이 연결되어 있습니다. 또는 단계 목록이나 일련의 스크린샷이 포함된 텍스트 문서를 사용할 수 있습니다. For more information, see [Describing Use Cases in Detail](#Details).

 동작 다이어그램을 사용하는 경우 다음과 같은 명명 규칙을 확인합니다.

- 전체 동작의 이름은 포함하는 사용 사례와 같습니다.

- 동작 다이어그램의 작업 이름은 포함된 사용 사례와 같습니다.

  For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  ![Use case steps shown in linked activity diagram](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a> Sharing goals with Generalization
 Use a Generalization relation to show that a *specialized* use case is a particular way to achieve the goals expressed by another *general* use case. 열린 화살촉이 보다 일반적인 사용 사례를 가리켜야 합니다.

 ![Use cases showing the generalization relation](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 For example, **Pay** generalizes **Pay by Credit Card** and **Pay by Cash**.

> [!CAUTION]
> 행위자가 자신을 일반화하는 일반화 관계 루프를 만들면 안 됩니다. 루프에서 오류가 발생할 수 있습니다.

 특수화된 사용 사례는 시스템이 동일한 목표를 달성할 수 있는 다양한 방법을 표시하는 데 도움이 됩니다.

 특수화된 사용 사례는 일반적인 사용 사례의 목표 및 행위자를 상속하는 것으로 간주됩니다. 일반적인 사용 사례에는 자체 시나리오가 없어도 됩니다. 특수화에서 목표를 달성하는 다양한 방법을 설명합니다.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>두 개 이상의 사용 사례에서 공통 목표를 리팩터링하려면

1. 새로운 일반적인 사용 사례를 만들고 이름을 지정합니다.

2. Create a **Generalization** relation with the large arrow pointing at the new general use case.

    1. Click **Generalization** in the toolbox.

    2. Click a specialized use case (**Pay by Credit Card** in the example).

    3. Click the general use case (**Pay** in the example).

3. 특수화된 사용 사례의 목표를 설명한 경우 공통 부분을 일반적인 사용 사례의 설명으로 이동합니다.

4. 특수화된 사용 사례 간에 공유되는 행위자를 일반적인 사용 사례로 이동할 수 있습니다.

### <a name="Extend"></a> Separating variant cases with Extend
 확장 링크를 사용하여 한 사용 사례가 특정 상황에서 다른 사용 사례에 기능을 추가할 수 있음을 표시할 수 있습니다. 화살표가 확장된 기본 사용 사례를 가리켜야 합니다.

 ![One use case extending another](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> 행위자가 자신을 일반화하는 확장 관계 루프를 만들면 안 됩니다. 루프에서 오류가 발생할 수 있습니다.

 For example, the **Login** use case of a typical Web site can include **Register New User** - but only when the user does not already have an account.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>사용 사례를 기본 파트와 확장하는 파트로 구분하려면

1. 새로운 확장 사용 사례를 만들고 이름을 지정합니다.

2. Create an **Extend** relation with the arrow pointing at the extended use case.

   1. Click **Extend** in the toolbox.

   2. Click the extending use case (**Register New User** in the example).

   3. Click the extended use case (**Login** in the example).

       > [!NOTE]
       > 다이어그램에서 확장 관계 루프를 만들지 마세요. 사용 사례가 자체 확장이 되는 것은 올바르지 않습니다.

3. 확장된 사용 사례에 대한 시나리오를 이미 만든 경우 관련 단계를 확장 시나리오로 이동합니다.

4. The description of the extension (**Register New User** in the example) should include details of where in the main use case scenarios it will occur, and under what circumstances. 기본 사례의 설명을 수정한다고 생각하시면 됩니다.

   확장 사용 사례는 그렇지 않을 경우 기본 사용 사례의 시나리오에 포함되는 시나리오 단계를 나타냅니다. 확장의 시나리오 및 목표는 항상 기본 사용 사례의 컨텍스트에서 읽혀지므로 독립적으로 유용하지 않아도 됩니다.

   확장을 분리하면 다음과 같은 상황을 설명하는 데 유용할 수 있습니다.

- 확장 사용 사례에만 관련된 추가 행위자가 있습니다. 예를 들어 관리자가 웹 사이트의 고객 등록을 승인해야 합니다.

- 별도 하위 시스템에서 확장 사용 사례를 처리합니다.

- 이 확장은 시스템의 특정 버전에서만 사용할 수 있습니다. 사용 사례 다이어그램에서 각 버전을 별도 하위 시스템으로 표시할 수 있습니다.

## <a name="Subsystems"></a> Using Subsystem Boundaries
 하위 시스템 경계를 사용하여 시스템의 범위 내에 있는 사용 사례를 표시할 수 있습니다.

#### <a name="to-draw-a-subsystem-boundary"></a>하위 시스템 경계를 그리려면

1. In the toolbox, click **Subsystem**, then click the diagram.

    다이어그램에 하위 시스템이 표시됩니다.

2. 하위 시스템의 모퉁이를 끌어 크기를 조정합니다.

3. 기존 사용 사례를 하위 시스템 안이나 밖으로 끌어 콘텐츠를 조정합니다.

   \- 또는 -

   To create a new use case directly in a subsystem, click **Use Case** in the toolbox, then click inside the subsystem.

> [!NOTE]
> The **Subjects** property of a use case indicates what subsystem it is contained within.

### <a name="use-cases-outside-the-system-scope"></a>시스템 범위 외부의 사용 사례
 비즈니스의 일부이지만 개발 중인 시스템에서 처리하지 않는 사용 사례를 다이어그램에 포함하면 유용한 경우가 많습니다. 이렇게 하면 개발자가 해당 작업의 컨텍스트를 이해하는 데 도움이 됩니다. 예를 들어 음식 주문 웹 사이트의 책임 외부에 식당 및 고객 행위자와 관련된 사용 사례로 음식 배달을 표시할 수 있습니다.

### <a name="multiple-subsystems"></a>여러 하위 시스템
 여러 하위 시스템 경계를 만들어 각 사용 사례가 시스템의 서로 다른 구성 요소에서 처리되는 방식을 표시할 수 있습니다. For example, **Add Restaurant Appraisal** may be dealt with on a separate forum Web site. 사용 사례 다이어그램은 사용자에게 표시되는 사항을 처리해야 합니다. 시스템의 내부 작업 부서를 설명하려는 경우 구성 요소 다이어그램을 사용하는 것이 좋습니다.

### <a name="system-versions"></a>시스템 버전
 여러 하위 시스템 경계를 사용하여 시스템의 서로 다른 버전을 표시할 수 있습니다. 예를 들어 대금 지불 사용 사례를 웹 사이트 버전 2에만 포함하고 버전 1에는 포함하지 않을 수 있습니다. 이는 시스템에서 고객 주문을 도와준다는 것을 의미합니다. 그러나 식당에 직접 대금을 지불해야 합니다.

 Use **Dependency** relations to link subsystems representing different versions or variants.

 ![Subsystems show different versions of a system](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>관련 항목:
 [Model user requirements](../modeling/model-user-requirements.md) [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md) [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md) [Video: Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
