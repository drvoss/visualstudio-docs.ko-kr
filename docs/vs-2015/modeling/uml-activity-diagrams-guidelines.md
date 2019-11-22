---
title: 'UML Activity Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298994"
---
# <a name="uml-activity-diagrams-guidelines"></a>UML 동작 다이어그램: 지침
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 동작 다이어그램을 그려서 일련의 작업을 통한 작업 흐름으로 비즈니스 프로세스 또는 소프트웨어 알고리즘을 설명합니다. 사용자, 소프트웨어 구성 요소 또는 디바이스가 이러한 작업을 수행할 수 있습니다. For a video demonstration, see: [Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 To create a UML activity diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 다음과 같은 다양한 용도로 동작 다이어그램을 사용할 수 있습니다.

- 사용자와 시스템 간의 비즈니스 프로세스 또는 워크플로를 설명합니다. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

- 사용 사례에서 수행된 단계를 설명합니다. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

- 소프트웨어의 메서드, 함수 또는 작업을 설명합니다. For more information, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

  동작 다이어그램 그리기를 통해 프로세스를 향상할 수 있습니다. 기존 프로세스의 다이어그램이 매우 복잡한 것으로 확인되면 프로세스를 단순화하는 방법을 고려할 수 있습니다.

  For reference information about the elements on activity diagrams, see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a> Relationship to Other Diagrams
 동작 다이어그램을 그려서 비즈니스 프로세스 또는 사용자가 시스템을 사용하는 방법을 설명할 경우 사용 사례 다이어그램을 그려서 같은 정보를 다른 뷰로 표시할 수 있습니다. 사용 사례 다이어그램에서는 동작을 사용 사례로 그립니다. 사용 사례에 해당 동작과 같은 이름을 지정합니다. 사용 사례 뷰의 장점은 다음을 수행할 수 있다는 점입니다.

- 포함 관계를 사용하여 더 작은 작업/사용 사례로 더 큰 작업/사용 사례를 구성하는 방법을 한 다이어그램에 표시합니다.

- 각 작업/사용 사례를 실행에 포함된 사용자 또는 외부 시스템에 명시적으로 연결합니다.

- 시스템에서 지원되는 작업/사용 사례 또는 시스템의 주요 구성 요소 주위에 경계를 그립니다.

  동작 다이어그램을 그려서 소프트웨어 작업의 세부 디자인을 설명할 수도 있습니다.

  동작 다이어그램에서 작업 간에 전달된 데이터 흐름을 표시할 수 있습니다. See the section on [Describing Data Flow](#DataFlows). 그러나 동작 다이어그램에서는 데이터 구조를 설명하지 않습니다. 데이터 구조를 설명하려면 UML 클래스 다이어그램을 그립니다. For information see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Activity Diagrams
 Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>동작 다이어그램을 그리려면

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Activity Diagram**.

3. 다이어그램 이름을 지정합니다.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>동작 다이어그램의 요소를 그리려면

1. 도구 상자에서 다이어그램으로 요소를 끌어옵니다.

     먼저 다이어그램에 주 동작을 배치하고 이들 동작을 연결하고 나서 마지막으로 초기 및 최종 노드 등을 추가합니다.

    > [!NOTE]
    > 기존 요소를 UML 모델 탐색기에서 다이어그램으로 끌 수는 없습니다.

2. 요소를 연결하려면 다음 단계를 수행합니다.

    1. In the **Activity Diagram** toolbox, click **Connector**.

    2. 다이어그램에서 소스 요소를 클릭합니다.

    3. 대상 요소를 클릭합니다.

        > [!NOTE]
        > 한 도구를 여러 번 사용하려면 도구 상자에서 도구를 두 번 클릭합니다.

#### <a name="to-move-an-activity-to-another-package"></a>동작을 다른 패키지로 이동하려면

- In **UML Model Explorer**, drag the activity into a package.

     \- 또는 -

- In **UML Model Explorer**, right-click the activity and click **Cut**. Then right-click the package and click **Paste**.

    > [!NOTE]
    > 다이어그램에 첫 번째 요소를 추가할 때만 동작이 UML 모델 탐색기에 표시됩니다.

## <a name="SimpleControlFlow"></a> Describing Control Flow
 동작 다이어그램에서는 비즈니스 프로세스나 소프트웨어 알고리즘을 일련의 작업으로 설명합니다. 커넥터 화살표는 한 작업에서 다음 작업으로 제어가 순차적으로 전달되는 방식을 보여 줍니다. 일반적으로 작업은 이전 작업이 완료된 후에만 시작될 수 있습니다.

 다음 그림은 작업, 커넥터, 분기 및 루프가 있는 일련의 작업을 표시하는 방법의 한 가지 예입니다. 각 요소는 다음 섹션에서 더 자세히 설명합니다.

 ![A simple activity diagram](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Activity diagrams use **Actions** and **Connectors** to describe your system or application as a series of actions with the control flowing sequentially from one action to the next.

- Create an **Action** (1) for each major task that is performed by a user, the system, or both in collaboration.

  > [!NOTE]
  > 몇 가지 작업으로만 프로세스나 알고리즘을 설명해 보세요. You can use **Call Behavior Actions** to define each action in more detail in a separate diagram, as described in [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- 각 작업의 제목이 일반적으로 작업으로 달성하는 결과를 분명히 나타내는지 확인합니다.

- Link the actions in sequence with **Connectors** (2).

- 각 작업은 제어 흐름의 다음 작업이 시작되기 전에 끝납니다. If you want to describe actions that overlap, use a **Fork Node** as described in the section [Concurrent Flows](#Concurrent).

  다이어그램에서는 작업 시퀀스를 설명하지만 작업이 실행되는 방식이나 한 작업에서 다음 작업으로 컨트롤이 전달되는 방식을 설명하지는 않습니다. 예를 들어 다이어그램을 사용하여 비즈니스 프로세스를 나타낼 경우 한 사람이 다른 사람에게 메일 메시지를 보낼 때 제어가 전달될 수 있습니다. 다이어그램을 사용하여 소프트웨어 디자인을 나타낼 경우 한 문에서 다음 문으로 일반적인 실행 흐름에 의해 제어가 전달될 수 있습니다.

### <a name="describing-decisions-and-loops"></a>의사 결정 및 루프 설명

- Use a **Decision Node** (3) to indicate a point where the outcome of a decision dictates the next step. 원하는 만큼 나가는 경로를 그릴 수 있습니다.

- 동작 다이어그램을 사용하여 애플리케이션 파트를 정의할 경우 각 경로를 사용해야 하는 시기가 분명하도록 가드(4)를 정의해야 합니다. Right-click the connector, click **Properties**, and in the **Properties** window, type a value for the **Guard** field.

- 가드를 항상 정의할 필요는 없습니다. 예를 들어 동작 다이어그램을 사용하여 비즈니스 프로세스 또는 상호 작용 프로토콜을 설명할 경우 분기는 사용자 또는 상호 작용하는 구성 요소에 제공되는 옵션 범위를 정의합니다.

- Use a **Merge Node** (5) to bring together two or more alternative flows that branched at a **Decision Node**.

    > [!NOTE]
    > You should use a **Merge Node** to bring together alternative flows, instead of bringing the flows together at an action. In the example, it would not be correct to connect from the decision node directly back to **Choose Menu Item**. 이는 제어 스레드가 모든 들어오는 커넥터에 도착할 때까지 작업이 시작되지 않기 때문입니다. 따라서 동시 흐름만 작업으로 결합해야 합니다. For more information, see [Concurrent Flows](#Concurrent).

- 예제와 같이 분기를 사용하여 루프를 설명합니다.

    > [!NOTE]
    > 프로그램 코드에서 하는 것처럼 잘 구성된 방식으로 루프를 중첩해 보세요. 기존 비즈니스 프로세스를 설명할 경우 이를 통해 기존 비즈니스 프로세스를 개선할 수 있는 기회가 드러날 수 있습니다.

### <a name="starting-the-activity"></a>동작 시작
 동작에 대한 진입점을 나타내는 두 가지 방법은 다음과 같습니다.

- **Initial Node**

     Create one **Initial Node** (6) to indicate the first action of the activity.

     이 메서드는 하위 동작을 설명할 때나 동작을 시작하는 상태를 명시적으로 지정할 필요가 없을 경우 가장 유용합니다. 예를 들어 Order a Meal 동작은 분명히 고객이 배고플 때 시작됩니다.

- **Accept Event Node**

     Create **Accept Event Nodes**, as described in the section [Concurrent Flows](#Concurrent), to indicate the start of a thread that responds to a particular event, such as a user input. 노드에 들어오는 흐름을 제공하지 마세요. 들어오는 흐름을 생략하면 이벤트가 발생할 때마다 스레드가 시작됩니다.

     이 방법은 특정 외부 이벤트에 대한 응답을 설명할 때 가장 유용합니다.

### <a name="ending-the-activity"></a>동작 종료
 Use an **Activity Final Node** (7) to indicate the end of an activity.

- When a thread of control reaches an **Activity Final Node**, all the activity's concurrent actions and sub-activities terminate.

- 동작 최종 노드를 두 개 이상 사용하여 추가 커넥터의 혼잡함을 줄일 수 있습니다.

### <a name="interrupting-the-activity"></a>동작 중단
 예를 들어 사용자가 프로세스를 취소하도록 결정할 경우, 일반적인 동작 흐름을 중단할 수 있는 방법을 설명하려면 해당 이벤트를 수신하는 이벤트 적용 노드를 만들면 됩니다. For more information, see the section [Concurrent Flows](#Concurrent). 이 노드에서 동작 최종 노드(7)까지 제어 흐름을 만듭니다.

### <a name="swimlanes"></a>스윔 레인
 때때로 작업을 수행하는 다양한 개체 또는 비즈니스 역할에 해당하는 영역으로 동작의 작업을 정렬할 때 유용합니다. These areas are conventionally arranged in columns and are called *swimlanes*.

- Use lines or rectangles from the **Simple Shapes** section of the Toolbox to draw swimlanes or other areas.

- To label each swimlane, create a comment and set its **Transparent** property to **True**.

  단순한 모양은 UML 모델의 파트를 구성하지 않고 UML 모델 탐색기에 나타나지 않습니다.

## <a name="DataFlows"></a> Describing Data Flow
 동작에 대해 나가거나 들어오는 데이터 전달은 다음 두 가지 방법의 하나로 설명할 수 있습니다.

- Use an **Object Node**. 이는 동작 간에 흐르는 정보를 설명하는 가장 단순한 방법입니다. 개체 노드는 프로그램의 변수와 같습니다. 한 작업에서 다른 작업으로 전달되는 하나 이상의 값을 저장하는 항목을 나타냅니다.

- Use an **Output Pin** and an **Input Pin**. 이 방법을 통해 한 작업에서 나가는 출력 및 다른 작업으로 들어오는 입력을 개별적으로 설명할 수 있습니다. 핀은 프로그램의 매개 변수와 같습니다. 핀은 개체가 작업에 들어오고 나가는 포트를 나타냅니다.

    > [!NOTE]
    > For an overview of the elements used in this section, see the Data Flows section of the topic see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>개체 노드를 사용하여 데이터 흐름 설명
 대부분 제어 흐름은 데이터를 전달합니다. 예를 들어 “고객이 세부 정보 제공” 작업의 출력 흐름은 배송 주소에 대한 참조를 전달합니다.

 다이어그램에서 해당 데이터를 설명하려면 다음 그림과 같이 커넥터를 개체 노드 및 두 개의 커넥터로 바꿉니다.

 ![Object nodes can show data passed between actions](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 모퉁이가 둥근 사각형(예: 상품 발송)은 처리가 발생하는 작업을 나타냅니다. 모퉁이가 각진 사각형(예: 배송 주소)은 한 작업에서 다른 작업으로 개체의 흐름을 나타냅니다.

 작업 간에 흐르는 개체의 통로 또는 버퍼로 사용되는 노드 역할을 반영하는 이름을 개체 노드에 지정합니다.

 You can set the **Type** of the object node in the Properties window. 형식은 클래스 다이어그램에서 정의한 정수 또는 클래스와 같은 기본 형식, 인터페이스 또는 열거형이 될 수 있습니다. 예를 들어 Street Address, City 등의 특성과 Customer라는 다른 클래스에 대한 연결을 함께 사용하여 Shipment Address 클래스를 만들 수 있습니다. For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> If you type the name of a type that has not yet been defined, an item will be added under **Unspecified Types** in UML Model Explorer. 이후에 클래스 다이어그램에서 해당 이름의 형식을 정의할 경우 새 형식을 참조하도록 개체 노드의 형식을 다시 설정해야 합니다.

#### <a name="buffering-data-in-object-nodes"></a>개체 노드에서 데이터 버퍼링
 개체 노드는 여러 개체에 대한 버퍼로 사용될 수 있습니다. 다음 그림에서 제어 흐름은 사용자가 [choose more] 루프(1)를 여러 번 방문하고 동시에 Chosen Menu Items 개체 노드(2)에 사용자 선택이 누적됨을 보여 줍니다. 마지막으로 사용자가 선택을 완료하면 Chosen Menu Items 버퍼에서 전체 선택 목록을 적용하는 Confirm Order 작업(3)으로 제어가 전달됩니다.

 ![Buffering data in object nodes](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 개체 노드의 속성을 설정하여 버퍼의 항목을 저장하는 방법을 지정할 수 있습니다.

- Set the **Ordering** property:

  - **Unordered** to specify a random or unspecified order. (Default.)

  - **Ordered** to specify an order according to a specific key.

  - **Fifo** to specify an order of first-in, first-out.

  - **Lifo** to specify an order of last-in, first-out.

- Set the **Upper Bound** property to specify the maximum number of objects that can be contained in the buffer. 기본값은 *입니다. 이는 제한이 없음을 의미합니다.

### <a name="describing-data-flow-with-input-and-output-pins"></a>입력 및 출력 핀을 사용하여 데이터 흐름 설명
 Use an **Output Pin** and an **Input Pin** to separately describe the outputs from one action and the inputs to another.

 ![Input and output pins are action parameters](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 To create a pin, click **Input Pin** or **Output Pin** on the toolbox and then click an action. 작업 경계로 핀을 이동하고 해당 이름을 변경할 수 있습니다. You can create input and output pins on any kind of action, including **Call Behavior Actions**, **Call Operation Actions**, **Send Signal Actions**, and **Accept Event Actions**.

 개체 노드에 들어오고 나가는 흐름이 수행하는 것과 같이 두 핀 사이의 커넥터는 개체 흐름을 나타냅니다.

 매개 변수 이름과 같이 핀이 생성하거나 적용하는 개체의 역할을 나타내는 이름을 핀에 지정합니다.

 You can set the type of objects transmitted in the **Type** property. 이 형식은 UML 클래스 다이어그램에서 만든 형식이어야 합니다.

 연결된 핀 사이에 흐르는 개체는 어떤 방식으로든 호환되어야 합니다. 이는 출력 핀에서 생성된 개체는 입력 핀 형식의 파생 형식에 속하기 때문일 수 있습니다.

 또는 출력 핀 형식과 입력 핀 형식 간에 데이터를 바꾸는 변환이 개체 흐름에 포함되도록 지정할 수 있습니다. 이 종류의 가장 일반적인 변환만으로 더 큰 형식에서 적절한 파트를 추출할 수 있습니다. 그림의 예제는 주문 세부 정보에서 배송 주소를 추출하는 변환이 있음을 의미합니다.

## <a name="Details"></a> Defining an Action in More Detail
 작업 이름을 사용하여 일반적으로 획득하는 결과를 분명히 설명하는 방법 이외에 다음과 같은 몇 가지 방법으로 작업에 세부 정보를 추가할 수 있습니다.

- Write a more detailed description in the **Body** property. 예를 들어 프로그램 코드 또는 의사 코드의 조각을 작성하거나 획득한 결과에 대한 전체 설명을 작성할 수 있습니다.

- 작업을 동작 호출 작업으로 바꾸고 개별 동작 다이어그램 내에서 세부 동작을 설명합니다. See [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- Set the action's **Local Postconditions** and **Local Preconditions** properties to describe its outcome in more specific detail. For more information, see [Defining Postconditions and Preconditions](#Postcondition).

### <a name="Subactivities"></a> Describing Sub-activities with Call Behavior Actions
 개별 동작 다이어그램을 사용하여 작업의 세부 동작을 설명할 수 있습니다. 호출된 동작은 동작 호출 작업을 통해 주 동작 다이어그램에 표시되는 동작 다이어그램입니다. 하위 동작을 여러 번 그릴 필요가 없도록 동작 호출 작업을 사용하여 여러 동작 간에 공유되는 동작을 설명할 수도 있습니다.

 다음 그림에서 다이어그램 1에는 동작 호출 작업이 포함된 동작이 표시되고 다이어그램 2에는 호출된 동작을 나타내는 하위 동작 다이어그램이 표시됩니다.

 ![A separate activity diagram shows detailed actions](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>동작 호출 작업으로 하위 동작을 설명하려면

1. To create the diagram for the sub-activity, in **Solution Explorer**, right-click your modeling project, point to **Add**, and then click **New Item**.

2. In the **Add New Item** dialog box, under **Templates** click **Activity Diagram** and in the **Name** box type the name that you plan to give your **Call Behavior Action**.

3. 하위 동작에 대한 세부 작업을 그립니다. 이는 호출된 동작입니다.

    - In the called sub-activity diagram, the **Initial Node** indicates where control starts when the called behavior is invoked. The **Activity Final Node** shows where control should return to the parent activity.

4. Set the **Behavior** property of the **Call Behavior Action** to refer to the called behavior diagram.

    > [!NOTE]
    > The sub-activity diagram must have some elements on it or the diagram will not be available in the drop-down list for the **Behavior** property. Also, the trident icon will not appear on your **Call Behavior Action** shape until you set its **Behavior** property.

5. Set the **Is Synchronous** property of the action to indicate whether your activity waits for the called activity to complete.

    - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called activity finishes. 작업에서 출력 핀 또는 나가는 데이터 흐름을 정의하면 안 됩니다.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>하위 동작에 들어오고 나가는 데이터 흐름 설명
 소프트웨어에서 매개 변수를 사용하는 것과 같은 방법으로 하위 동작에 들어오고 나가는 데이터 흐름을 설명할 수 있습니다.

- 호출된 동작 작업에서 작업에 흘러 들어오거나 나가는 데이터의 조각에 대한 입력 및 출력 핀(1)을 만듭니다. 각 조각에 적절한 이름을 지정합니다.

- In the sub-activity diagram, create an **Activity Parameter Node** (2) for each input and output pin on the calling action. 각 노드에 해당 핀과 같은 이름을 지정합니다.

  > [!NOTE]
  > 동작 매개 변수 노드는 개체 노드와 비슷합니다. To check what type of node that you are looking at, right-click the node and then click **Properties**. 노드 형식은 속성 창의 헤더에 표시됩니다.

- 하위 동작 다이어그램에서 각 동작 매개 변수 노드에 들어오거나 나가는 개체 흐름을 표시하는 커넥터를 그립니다.

  ![Pins on Call Behavior map to activity parameters](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a> Defining Postconditions and Preconditions
 You can use the **Local Postconditions** and **Local Preconditions** properties to specify in detail the outcome of an action. 이들 속성은 효과를 어떻게 얻는지를 설명하지 않고 작업의 효과를 설명합니다.

 To set these properties, right-click the action and then click **Properties**. 속성 창에서 속성에 값을 입력합니다.

#### <a name="local-postconditions"></a>로컬 사후 조건
 사후 조건은 작업을 완료된 것으로 간주하기 전에 충족해야 하는 조건입니다. 예제 작업 Confirm Order에서 사후 조건은 다음과 같습니다.

 고객이 신용 카드를 처리하는 데 필요한 완전하고 올바른 세부 정보를 제공했습니다.

 사후 조건은 작업 발생 전후 상태 간의 관계를 표현합니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

 이자율이 이전보다 2배가 되었습니다.

 작업에서 처리된 데이터의 특정 특성을 참조하여 사후 조건을 더 공식적인 스타일로 작성할 수 있습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>로컬 사전 조건
 사전 조건은 작업이 시작할 준비가 되었을 때 true여야 하는 조건입니다. 예를 들어 Confirm Order 작업에는 다음 사전 조건이 있을 수 있습니다.

 고객이 메뉴에서 하나 이상의 항목을 선택했습니다.

### <a name="describing-calls-to-operations"></a>작업에 대한 호출 설명
 일반적으로 작업은 사용자, 소프트웨어 또는 컴퓨터의 조합에 의해 수행되는 작업을 설명합니다. 그러나 작업 호출 작업을 사용하여 특정 소프트웨어 메서드 또는 함수에 대한 호출을 설명할 수 있습니다.

- 작업 호출 작업의 이름을 설정하여 호출되는 작업 및 대상 개체나 구성 요소를 나타냅니다.

- 작업 호출 작업에 입력 및 출력 핀을 추가하여 매개 변수를 설명하고 값을 반환합니다.

- You can set the **Is Synchronous** property of the action to indicate whether your activity waits for the operation to complete.

  - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called operation is complete. 작업에서 출력 핀 또는 나가는 데이터 흐름을 정의하면 안 됩니다.

## <a name="Concurrent"></a> Concurrent Flows
 You can use the **Fork Node** and the **Join Node** to describe two or more threads of activities that can execute at the same time.

 ![The fork and join nodes show concurrent flows](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 The effect of the **Fork Node** (1) is to divide the thread of control into two or more threads. 이전 작업이 종료되면 분기의 출력 쪽 모든 작업이 시작될 수 있습니다.

 A **Join Node** (2) brings concurrent threads together. The action after the **Join Node** may not start until all the actions leading to the **Join Node** are complete.

### <a name="describing-signals-and-events"></a>신호 및 이벤트 설명
 동작에서 신호를 신호 보내기 작업으로 보내는 프로세스의 단계를 표시할 수 있습니다. 단계가 이벤트 적용 작업으로 계속되기 전에 특정 신호 또는 이벤트를 기다리는 단계를 표시할 수 있습니다.

 예를 들어 주문을 전송하는 한 단계를 표시하고 나서 주문을 처리하기 전에 해당 주문을 수신해야 하는 또 다른 단계를 표시할 수 있습니다.

#### <a name="sending-a-signal"></a>신호 보내기
 신호 보내기 작업(3)을 사용하여 일종의 신호 또는 메시지가 다른 동작 또는 프로세스에 전송됨을 나타냅니다. 작업 이름을 사용하여 보내는 메시지 종류를 나타냅니다.

- 제어는 즉시 제어 흐름의 다음 작업에 전달됩니다(있는 경우).

- 신호 보내기 작업을 사용하여 프로세스가 반환된 정보에 응답하는 방식을 설명합니다. 이렇게 하려면 별도의 이벤트 적용 작업을 사용합니다.

- 신호 보내기 작업에 들어오는 데이터 흐름을 표시하여 나가는 메시지와 함께 전송될 수 있는 데이터를 나타냅니다. For more information, see [Describing Data Flow](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>신호 또는 이벤트 대기
 이벤트 적용 작업(4)을 사용하여 이 동작이 일부 외부 이벤트 또는 들어오는 메시지를 기다리도록 지정합니다. 작업 이름을 사용하여 기다리는 이벤트 형식을 나타냅니다.

- 동작이 흐름의 특정 지점에서 외부 이벤트 또는 메시지를 기다리고 있음을 표시하려면 들어오는 흐름을 사용하여 동작의 해당 위치에 이벤트 적용 작업을 그립니다.

- 동작이 언제든지 외부 이벤트 또는 메시지에 응답할 수 있음을 표시하려면 들어오는 흐름이 없는 이벤트 적용 작업을 그립니다. 명명된 외부 이벤트가 발생하면 동작에서 새 스레드가 시작되어 이벤트 적용 작업부터 시작됩니다.

- 신호의 보낸 사람에게 반환되는 값을 설명하는 데는 이벤트 적용 작업을 사용할 수 없습니다. 이 목적에는 개별 신호 보내기 작업을 사용하세요.

- 작업에서 나가는 데이터 흐름을 표시하여 신호로 수신된 데이터를 동작에서 어떻게 처리하는지를 나타낼 수 있습니다. If you want to show more than one output flow, you should set the **IsUnmarshall** property of the Accept Event Action, which indicates that the action parses the incoming signal into its separate components. For more information, see [Describing Data Flow](#DataFlows).

### <a name="describing-multiple-data-flows"></a>여러 데이터 흐름 설명
 작업에서 나오는 두 개 이상의 제어 흐름 또는 개체 흐름을 그려서 작업이 종료되면 두 개 이상의 스레드가 곧 발생함을 나타냅니다. 제어 및 개체 흐름을 혼합해서 사용할 수 있다는 점을 제외하고 이 효과는 분기의 효과와 비슷합니다.

 다음 예제에서는 작업에 들어오고 나가는 여러 흐름을 보여 줍니다.

 ![Parallel object flows](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 “고객이 세부 정보 제공” 작업이 완료되면 "Shipment address" 및 "Credit card details" 개체가 생성됩니다. 두 개체는 다른 작업에서 처리하기 위해 전달됩니다.

 작업에서는 시작하기 전에 모든 입력을 사용할 수 있어야 하므로 마지막 작업은 선행 작업이 모두 완료될 때까지 시작되지 않습니다.

### <a name="streams"></a>스트림
 동작 다이어그램을 사용하면 동시에 실행되고 지속적으로 한 작업에서 다른 작업으로 데이터를 전달하는 파이프라인 또는 일련의 작업을 설명할 수 있습니다.

 다음 예제에서는 각 작업이 개체를 생성하고 계속 작동할 수 있음을 보여 줍니다. 제어 흐름이 없으므로 각 작업은 첫 번째 개체를 수신하면 바로 시작될 수 있습니다.

 이 예제의 커넥터는 동작 매개 변수 노드, 개체 노드 또는 입력/출력 핀에 하나 이상의 끝이 있으므로 모두 개체 흐름입니다.

 ![A data flow](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. 예제에는 입력 및 출력을 나타내는 세 가지 동작 매개 변수 노드가 있습니다.

 2. 개체 노드, 입력 핀 및 출력 핀은 버퍼를 나타낼 수 있습니다. 개체 노드의 상한 속성을 설정하여 동시에 버퍼에 포함할 수 있는 개체 수를 지정합니다.

 3. 의사 결정 노드를 사용하여 스트림이 나뉘어서 여러 가지 개체를 여러 분기로 전송함을 표시할 수 있습니다. 주석이나 노드 제목을 사용하여 구분 기준을 설명할 수 있습니다.

 4. 분기 노드를 사용하여 개체 복사본을 두 개 이상 만들어서 동시 처리를 위해 전송함을 표시할 수 있습니다.

 5. 조인 노드를 사용하여 처리 스트림 두 개가 다시 하나로 병합됨을 표시할 수 있습니다.

### <a name="selection-and-transformation"></a>선택 및 변환
 개체 흐름의 개체가 변환 또는 선택되거나 변환과 선택이 모두 수행되도록 지정할 수 있습니다. 개체 흐름은 핀 또는 개체 노드에 들어오거나 나가는 흐름입니다.

- 변환은 흐름에 들어오는 개체가 다른 형식으로 변환되는 방식을 설명합니다.

- 선택은 흐름에 들어오는 일부 개체만 수신 작업으로 전송되는 방식을 설명합니다.

  예제에서는 변환을 보여 줍니다. 다이어그램 1의 첫 번째 작업에서는 출력 핀에 우편 번호를 생성합니다. 이 항목은 두 번째 작업에서 입력 핀에 연결됩니다. 그러나 두 번째 작업에는 완전히 지정된 주소가 필요합니다. 한 형식에서 다른 형식으로의 변환은 두 번째 동작인 주소 조회에서 지정됩니다. 이 동작은 개체 흐름의 변환 속성에서 참조됩니다. 주소 조회 동작에는 들어오는 우편 번호에 대한 한 동작 매개 변수 노드 및 나가는 전체 주소에 대한 다른 동작 매개 변수 노드가 포함됩니다.

  ![Object transformation defined in another diagram](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  변환 또는 선택을 지정할 수 있는 두 가지 방법은 다음과 같습니다.

- 주석을 입력 또는 출력 핀에 연결합니다.

  - To distinguish this description from a general comment, you can begin the comment with <\<**transformation**>> or <\<**selection**>>.

- 개별 동작 다이어그램에서 변환 또는 선택을 자세히 지정합니다.

  - 이 방법을 사용할 경우 주석도 연결하여 변환이 정의되었음을 독자에게 분명히 보여 줍니다.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>개별 동작 다이어그램에서 변환 또는 선택을 지정하려면

1. 변환 또는 선택 흐름을 설명하는 새 동작 다이어그램을 만듭니다.

   - In **Solution Explorer**, right-click your project, point to **Add**, click **New Item**, and then click **Activity Diagram**. 변환 또는 선택 흐름에 대한 적절한 이름을 다이어그램에 지정합니다. **추가**를 클릭합니다.

2. 새 다이어그램에서:

   1. 입력 흐름 및 출력 흐름에 대해 하나씩 두 동작 매개 변수 노드를 만듭니다.

   2. 개체 흐름과 상호 연결된 작업을 만듭니다. 이 작업은 변환 또는 선택이 작동하는 방식을 보여 줍니다.

3. 변환 또는 선택을 사용할 다이어그램에서:

   1. 입력/출력 핀, 개체 노드 또는 동작 매개 변수 노드에 들어오거나 나가는 커넥터인 개체 흐름을 만듭니다.

   2. Right-click the object flow and then click **Properties**.

   3. In the **Transformation** or **Selection** property, select the diagram where you specified the transformation or selection flow.

   개체 노드 및 개별 입력/출력 핀에 대해 선택을 정의할 수도 있습니다. Define a selection activity as in the previous procedure, and then set the **Selection** property of the object node, or input or output pin.

## <a name="see-also"></a>관련 항목:
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
