---
title: 'UML Sequence Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c5906084fc7db96ddf304e8362bf7692dac62d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297141"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sequence Diagrams: Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *sequence diagram* to show an interaction. 상호 작용은 클래스, 구성 요소, 하위 시스템 또는 행위자의 일반적인 인스턴스 간 메시지 시퀀스입니다.

 UML 시퀀스 다이어그램은 UML 모델의 일부이며 UML 모델링 프로젝트 내에만 존재합니다. To create a UML sequence diagram, on the **Architecture** menu, click **New UML or Layer Diagram**. Find out more about [UML sequence diagram elements](../modeling/uml-sequence-diagrams-reference.md) or [UML modeling diagrams](../modeling/edit-uml-models-and-diagrams.md) in general. For a video demonstration, see [Sketching Interactions by using Sequence Diagrams (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="in-this-topic"></a>항목 내용
 [Using UML Sequence Diagrams](#Using)

 [Basic Steps for Drawing Sequence Diagrams](#BasicSteps)

 [Creating and Using Simple Sequence Diagrams](#Simple)

 [Classes and Lifelines](#ClassesAndLifelines)

 [Creating Reusable Interaction Sequences](#Multiple)

 [Collapsing Groups of Lifelines](#Collapse)

 [Describing Control Structures with Fragments](#Fragments)

## <a name="Using"></a> Using UML Sequence Diagrams
 각기 다른 프로그램 세부 수준에서 다양한 용도로 시퀀스 다이어그램을 사용할 수 있습니다. 시퀀스 다이어그램을 그리는 일반적인 경우는 다음과 같습니다.

- 시스템 사용자 및 사용자 목표를 요약하는 사용 사례 다이어그램이 있는 경우 시스템의 주요 구성 요소가 각 사용 사례의 목표를 달성하기 위해 상호 작용하는 방식을 설명하는 시퀀스 다이어그램을 그릴 수 있습니다. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

- 구성 요소의 인터페이스에 도착하는 메시지를 식별한 경우 구성 요소의 내부 파트가 들어오는 각 메시지에 필요한 결과를 달성하기 위해 상호 작용하는 방식을 설명하는 시퀀스 다이어그램을 그릴 수 있습니다. For more information, see [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

  시퀀스 다이어그램을 그리면 다음과 같은 몇 가지 이점을 얻을 수 있습니다.

- 구성 요소 간에 작업이 배포되는 방식을 쉽게 확인할 수 있습니다.

- 소프트웨어 업데이트를 어렵게 만드는 상호 작용 패턴을 식별할 수 있습니다.

## <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계
 여러 가지 방법으로 다른 다이어그램과 함께 UML 시퀀스 다이어그램을 사용할 수 있습니다.

#### <a name="lifelines-and-types"></a>수명선 및 형식
 시퀀스 다이어그램에서 그리는 수명선은 시스템 구성 요소 또는 클래스의 일반적인 인스턴스를 나타낼 수 있습니다. 형식에서 수명선을 만들거나 수명선에서 형식을 만들 수 있으며, UML 클래스 다이어그램 및 UML 구성 요소 다이어그램에 형식을 표시할 수 있습니다. For more information, see [Classes and Lifelines](#ClassesAndLifelines).

#### <a name="parameter-types"></a>매개 변수 형식
 UML 클래스 다이어그램에서 수명선 간에 전송된 메시지에 사용된 매개 변수 형식과 반환 값을 설명할 수도 있습니다.

#### <a name="use-case-details"></a>사용 사례 정보
 사용 사례는 목표를 달성하기 위한 단계 시퀀스와 함께 사용자 목표를 나타냅니다. 여러 가지 방법으로 단계 시퀀스를 설명할 수 있습니다. 한 가지 옵션은 사용자와 시스템의 주요 구성 요소 간 상호 작용을 보여 주는 시퀀스 다이어그램을 그리는 것입니다. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Sequence Diagrams
 For a complete list of elements on sequence diagrams, see [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Detailed steps for how to create any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>시퀀스 다이어그램을 만들려면

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Sequence Diagram**.

3. 다이어그램 이름을 지정합니다.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a new modeling project**, and then click **OK**.

    A new sequence diagram appears with the **Sequence Diagram** toolbox. 이 도구 상자에는 필요한 요소 및 연결선이 포함되어 있습니다.

   ![Parts of a sequence diagram](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>시퀀스 다이어그램을 그리려면

1. Drag **Lifelines** (1) from the **Toolbox** onto the diagram to represent instances of classes, components, actors, or devices.

    > [!NOTE]
    > You can also create a lifeline by dragging an existing class, interface, actor or component from **UML Model Explorer** onto the diagram. 이렇게 하면 선택한 형식의 인스턴스를 나타내는 수명선이 생성됩니다.

2. 특정 목표를 달성하기 위해 수명선이 공동 작업하는 방식을 보여 주는 메시지를 그립니다.

     메시지(3, 4, 6, 7)를 만들려면 메시지 도구를 클릭합니다. 메시지를 시작할 지점에서 보내는 수명선을 클릭한 다음 받는 수명선을 클릭합니다.

     실행 발생(5)이 받는 수명선에 나타납니다. 실행 발생은 인스턴스가 메서드를 실행하는 기간을 나타냅니다. 실행 발생에서 시작되는 다른 메시지를 만들 수 있습니다.

3. 알 수 없는 이벤트 소스에서 들어오거나(9) 알 수 없는 받는 사람에게 브로드캐스트(10)되는 메시지를 표시하려면 다이어그램의 빈 공간에서 보내거나 받는 비동기 메시지를 그립니다. These messages are called *found messages* (9) and *lost messages* (10).

    > [!NOTE]
    > To move a group of lifelines that have lost or found messages, follow these steps to select the lifelines before you move them: Draw a rectangle around those lifelines, or press and hold the **CTRL** key while you click each lifeline. If you use **Select All** or **CTRL**+**A** to select all lifelines, and then move them, any lost or found messages attached to these lifelines will not move. 이 경우에는 해당 메시지를 개별적으로 이동할 수 있습니다.

4. 동일한 구성 요소 또는 시스템으로 보내는 각 주요 메시지에 대해 시퀀스 다이어그램을 그립니다.

#### <a name="to-change-the-order-of-messages"></a>메시지 순서를 변경하려면

- 수명선에서 메시지를 위 또는 아래로 끕니다. 다른 메시지 위로 끌거나, 실행 블록 안이나 밖으로 끌 수 있습니다.

     \- 또는 -

- Click the message and use the **UP ARROW** and **DOWN ARROW** keys to adjust message positions. Use **SHIFT+UP ARROW** and **SHIFT+DOWN ARROW** to change the order of the messages.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>시퀀스 다이어그램에서 메시지 시퀀스를 이동하거나 복사하려면

1. Right-click a message (3, 4) and then click **Copy**.

2. Right-click the execution occurrence (5) or a lifeline (1) from which you want the new message to be sent, and then click **Paste**. 원하는 경우 새 보낸 사람이 다른 다이어그램에 있을 수 있습니다.

     메시지 및 모든 보조 메시지의 복사본이 실행 발생의 끝이나 수명선의 끝에 추가됩니다.

    > [!NOTE]
    > 붙여넣은 메시지는 항상 실행 발생 또는 수명선의 끝에 표시됩니다. 붙여넣은 후 이전 위치까지 끌 수 있습니다.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>메시지에 대한 서명 텍스트를 표시하거나 편집하려면

- 서명 텍스트가 표시되려면 대상 수명선을 형식에 바인딩하거나 매핑해야 합니다. 이 작업을 완료하려면 다음 단계 중 하나를 수행합니다.

  - Right-click the lifeline, and then choose **Create Class**.

     또는

  - Select the lifeline, press **F4**, and then in the **Properties** window, set the **Type** property to an existing type or specify the name for a new type. Right-click the message label, and then choose **Create Operation**.

    서명 텍스트가 메시지 레이블 아래에 나타납니다. 이제 서명 텍스트를 편집할 수 있습니다. For more information, see [Classes and Lifelines](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>시퀀스 다이어그램의 레이아웃을 개선하려면

- Right-click a blank part of the diagram, and then click **Rearrange Layout**.

- To undo the operation, click **Edit**, and then click **Undo**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>상호 작용을 소유하는 패키지를 변경하려면

1. In **UML Model Explorer**, find the Interaction that the sequence diagram displays.

    > [!NOTE]
    > The interaction will not appear in **UML Model Explorer** until you add the first lifeline to the sequence diagram.

2. 상호 작용을 패키지로 끌어옵니다.

     \- 또는 -

     Right-click the Interaction, and then click **Cut**. Right-click the Package, and then click **Paste**.

## <a name="Simple"></a> Creating and Using Simple Sequence Diagrams
 가장 간단하고 널리 사용되는 형식의 시퀀스 다이어그램은 수명선과 메시지만 포함합니다. 이러한 종류의 다이어그램을 사용하면 디자인의 개체 간 또는 시스템과 사용자 간의 일반적인 상호 작용 시퀀스를 명확하게 표시할 수 있습니다. 이렇게 하면 디자인을 논의하고 전달하는 데 도움이 되는 경우가 많습니다.

 다음은 간단한 시퀀스 다이어그램을 그릴 때 고려해야 하는 몇 가지 사항입니다.

### <a name="types-of-message"></a>메시지 형식
 메시지를 만드는 데 사용할 수 있는 세 가지 도구가 있습니다.

- Use the **Synchronous** tool to describe an interaction in which the sender waits for the receiver to return a response (3).

     A **<\<return>>** arrow will be shown at the end of the execution occurrence. 보낸 사람에게 제어가 반환됨을 나타냅니다.

- Use the **Asynchronous** tool to describe an interaction in which the sender can continue immediately without waiting for the receiver (4).

- Use the **Create** tool to describe an interaction in which the sender creates the receiver (8).

     만들기 메시지는 받는 사람이 받은 첫 번째 메시지여야 합니다.

### <a name="annotating-the-interactions"></a>상호 작용에 주석 지정
 To describe more detail about the sequence, you can place a **Comment** anywhere on the diagram.

 Using **Comment Links**, you can link a comment to lifelines, executions, interaction uses, and fragments.

> [!CAUTION]
> 시퀀스의 특정 지점에 주석을 연결하려는 경우 실행 발생, 상호 작용 사용 또는 조각에 연결합니다. 수명선에는 연결하지 마세요. 이 경우 시퀀스의 정확한 위치에 연결된 상태로 유지되지 않습니다.

 주석을 사용하여 다음 작업을 수행합니다.

- 시퀀스의 주요 지점에서 달성된 목표를 기록합니다. 이렇게 하면 독자가 상호 작용의 목표를 확인하는 데 도움이 됩니다.

- 전체 시퀀스의 전반적인 목표를 설명합니다. 초기 실행 발생에 주석을 연결하거나 연결되지 않은 상태로 둡니다. 예를 들어 "고객이 메뉴에서 항목을 선택했으며 가격이 제공되었습니다."

- 각 수명선의 책임을 설명합니다. 수명선에 주석을 연결합니다. 예를 들어 "주문 관리자가 고객의 메뉴 선택을 수집합니다."

- 표시된 일반적인 시퀀스 대신 수행할 수 있는 대안 또는 예외를 기록합니다. 예를 들어 "고객이 이 시퀀스의 나머지를 건너뛰도록 선택할 수 있습니다."

  - 이러한 종류의 메모를 대체하는 보다 공식적인 방법으로 조각을 사용하는 것이 좋습니다. See [Describing Control Structures with Fragments](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>다이어그램의 범위 결정
 다이어그램에 표시하려는 사항을 명확히 하는 것이 중요합니다.

#### <a name="initiating-event"></a>이벤트 시작
 각 다이어그램에 하나의 시작 이벤트에서 발생하는 상호 작용 시퀀스가 표시되어야 합니다. 예를 들어 다음과 같을 수 있습니다.

- 사용자가 사용 사례를 시작합니다. 예를 들어 음식을 구입하기 위한 웹 페이지를 엽니다.

- 시스템 구성 요소 간에 메시지가 전송됩니다. 예를 들어 고객이 구입하려는 항목이 사용 가능한지 쿼리합니다.

- 상태 변경에 의해 이벤트가 트리거됩니다. 예를 들어 항목의 재고가 임계값 아래로 떨어집니다.

#### <a name="level-of-detail"></a>세부 수준
 시퀀스 다이어그램에서 여러 세부 수준을 표시할 수 있습니다. 두 개의 개별 차원에서 거의 독립적으로 세부 수준을 결정할 수 있습니다.

 수명선은 다음 세부 수준 중 하나를 나타낼 수 있습니다.

- 존재하거나 개발 중인 프로그램 코드의 개체

- 구성 요소 또는 해당 하위 구성 요소. 일반적으로 외관, 프록시 및 기타 연결 메커니즘은 생략됩니다.

- 시스템 및 외부 행위자

  메시지는 다음 세부 수준 중 하나를 나타낼 수 있습니다.

- 프로그램 코드, API 또는 웹 인터페이스의 소프트웨어 메시지

- 사용자와 시스템 간 또는 코드와 데이터베이스 간 등의 트랜잭션 또는 하위 트랜잭션

- 사용 사례 - 사용자와 시스템 간의 주요 상호 작용

  기존 코드를 탐색하든 또는 새 디자인을 설명하든 관계없이 덜 자세한 뷰를 그리고 논의하는 것이 유용한 경우가 많습니다.

## <a name="describing-variations"></a>변형 설명
 다이어그램에는 하나의 일반적인 이벤트 시퀀스가 표시됩니다. 오류 시나리오와 같은 대체 가능성을 표시하려는 경우 다음 옵션 중 하나를 사용할 수 있습니다.

- 이러한 시나리오를 설명하는 별도의 시퀀스 다이어그램을 그립니다.

- Use [Describing Control Structures with Fragments](#Fragments) to show loops, alternatives, and so on.

## <a name="assessing-the-design"></a>디자인 평가
 다이어그램을 사용하여 해당 개체 또는 구성 요소 간의 작업 분포를 평가할 수 있습니다. 다음 패턴이 표시되는 경우 리팩터링을 고려합니다.

- 한 수명선이 모든 작업을 수행하고 다른 모든 항목을 호출하는 반면, 다른 수명선은 수동적으로 응답만 합니다.

- 많은 메시지가 수명선을 교차합니다. 각 수명선은 몇 개의 인접한 항목에만 메시지를 보내야 하며 인접한 항목의 인접한 항목과 통신하면 안 됩니다. 일반적으로 몇 개의 위치에서만 메시지가 수명선을 교차하도록 수명선을 정렬할 수 있어야 하며, 교차가 있는 경우 대상 수명선이 교차된 수명선을 포함하는 메시지를 교환하면 안 됩니다.

- 일부 수명선이 두 종류 이상의 작업을 처리하는 것 같습니다. 각 수명선의 책임을 설명하고 받은 각 메시지에 대한 응답으로 수행하는 작업을 요약하는 하나의 간결한 문장을 찾기 쉬워야 합니다.

## <a name="ClassesAndLifelines"></a> Classes and Lifelines
 시퀀스 다이어그램의 수명선은 클래스 또는 구성 요소 인터페이스의 인스턴스를 표시합니다. 다음 두 가지 방법으로 수명선에 이름을 지정할 수 있습니다.

|**For this purpose**|**Use this format**|
|--------------------------|-------------------------|
|형식의 익명 인스턴스.<br /><br /> 각 형식의 수명선이 하나만 있는 경우에 사용합니다.|*typeName*|
|형식의 명명된 인스턴스.<br /><br /> 동일한 형식의 인스턴스를 두 개 이상 포함하는 시퀀스를 표시하려는 경우에 사용합니다.|*objectName*:*typeName*|

### <a name="creating-lifelines-from-types"></a>형식에서 수명선 만들기
 이미 정의한 클래스, 예를 들어 클래스 다이어그램에서 새 수명선을 만들 수 있습니다.

> [!NOTE]
> 이 작업을 수행하기 전에 기존 시퀀스 다이어그램이 있는지 확인합니다.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>기존 형식에서 수명선을 만들려면

- UML 모델 탐색기에서 시퀀스 다이어그램으로 클래스, 구성 요소 또는 인터페이스를 끌어옵니다.

   \- 또는 -

  1. Right-click the class, component, or interface on its respective diagram, and then click **Create Lifeline**.

  2. In the **Create Lifeline** dialog box, select a sequence diagram, and then click **OK**.

     해당 형식이 끌어온 형식인 새 명명된 인스턴스 수명선이 나타납니다.

  > [!NOTE]
  > 이 작업을 원하는 횟수만큼 반복할 수 있습니다. 각기 다른 인스턴스 이름으로 수명선이 생성됩니다.

##### <a name="to-change-the-type-of-a-lifeline"></a>수명선의 형식을 변경하려면

1. Right-click a lifeline, and then click **Properties**.

2. In the **Properties** window, set the **Type** property. 드롭다운 메뉴에서 형식을 선택하거나 새 이름을 입력합니다.

### <a name="creating-classes-from-lifelines"></a>수명선에서 클래스 만들기
 하나 이상의 시퀀스 다이어그램을 만든 경우 수명선에서 클래스 또는 인터페이스를 만들어 수명선을 요약할 수 있습니다.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>수명선에서 클래스 또는 인터페이스를 만들려면

1. Right-click the lifeline, and then click **Create Class** or **Create Interface**.

     새 클래스 또는 인터페이스가 UML 모델 탐색기에 나타납니다.

2. 클래스 또는 인터페이스에서 수명선이 받는 각 메시지에 대한 작업을 만듭니다.

    1. 포함할 메시지를 모두 선택합니다.

    2. Right-click one of the messages, and then click **Create Method**.

         새 클래스 또는 인터페이스에 선택한 각 메시지에 대한 작업이 포함됩니다.

         The operation name appears below each message arrow, and in the **Operation** property of the message.

         메시지에 "(parameter : type)" 형식의 매개 변수가 포함된 경우 새 작업의 매개 변수 목록에 표시됩니다.

        > [!NOTE]
        > 시퀀스 다이어그램에서 새 메시지를 추가하는 경우 이 단계를 반복해야 합니다.

3. 새 클래스 또는 인터페이스를 자세히 보려면 클래스 또는 구성 요소 다이어그램에 추가합니다.

    1. 클래스 또는 구성 요소 다이어그램을 열거나 만듭니다.

    2. Drag the new class or interface from **UML Model Explorer** to a class diagram.

         클래스 또는 인터페이스가 클래스 다이어그램에 나타납니다.

         \- 또는 -

    3. Drag the new interface from **UML Model Explorer** onto a component or port in a component diagram.

         인터페이스가 구성 요소에 롤리팝으로 나타납니다.

### <a name="creating-classes-for-parameters"></a>매개 변수에 대한 클래스 만들기
 시퀀스 다이어그램의 메시지에 매개 변수를 포함할 수 있습니다. UML 클래스 다이어그램을 사용하여 매개 변수 형식을 설명할 수 있습니다.

## <a name="Multiple"></a> Creating Reusable Interaction Sequences
 별도 다이어그램을 사용하여 분리하려고 하거나 여러 다이어그램 간에 공통된, 세부 정보가 포함된 시퀀스를 설명할 수 있습니다.

 한 다이어그램에서 다른 다이어그램의 세부 정보를 가리키는 상호 작용 사용 사각형(12)을 만들 수 있습니다.

 상호 작용 사용을 두 번 클릭하여 연결된 시퀀스 다이어그램을 엽니다.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>기존 수명선에서 다시 사용할 수 있는 상호 작용 시퀀스를 만들려면

1. In the **Toolbox**, click **Interaction Use**.

2. 시퀀스 다이어그램에서 마우스 단추를 누른 채 다시 사용할 수 있는 시퀀스에 포함할 수명선으로 끕니다. 상호 작용 사용을 삽입하려는 세로 위치에서 시작합니다.

     시퀀스 다이어그램에서 선택한 수명선에 상호 작용 사용이 표시됩니다.

3. 상호 작용 사용에서 이름을 두 번 클릭하고 이름을 바꾸어 이 다이어그램에서 다시 사용할 수 있는 시퀀스의 효과를 설명합니다.

     \- 또는 -

     매개 변수를 사용하여 함수 호출과 같은 이름을 작성합니다.

4. 다른 시퀀스 다이어그램에 상호 작용 사용을 연결합니다. 상호 작용 사용을 마우스 오른쪽 단추로 클릭하고 다음 중 하나를 수행합니다.

     Click **Create New Sequence** to create a new sequence diagram

     \- 또는 -

     Click **Link to Sequence** to link to an existing diagram.

     Visual Studio에서 상호 작용 사용과 새 상호 작용 시퀀스 간의 링크가 생성됩니다.

     새 시퀀스 다이어그램이 솔루션에 나타납니다. 상호 작용 사용을 만드는 데 사용한 수명선을 포함합니다.

    > [!NOTE]
    > 상호 작용 사용을 만드는 데 사용한 수명선만 포함됩니다. 상호 작용 사용 이후에 만든 수명선은 이제 상호 작용 사용에서 처리되는 경우에도 새 다이어그램에 포함되지 않습니다.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>기존 메시지에서 다시 사용할 수 있는 시퀀스를 만들려면

- Right-click the message that you want to move, and then click **Move to Diagram**.

  Visual Studio:

  - 선택한 메시지 및 보조 메시지를 상호 작용 사용으로 바꿉니다.

  - 바뀐 메시지를 새 시퀀스 다이어그램으로 이동합니다.

  - 상호 작용 사용과 새 시퀀스 다이어그램 간에 링크를 만듭니다.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>상호 작용 사용에서 참조하는 시퀀스로 이동하려면

- 상호 작용 사용을 두 번 클릭합니다.

     \- 또는 -

     Right-click the interaction use and then click **Go to Sequence**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>상호 작용 사용으로 자리 표시자 만들기
 다른 다이어그램에 연결하지 않고 상호 작용 사용을 만들 수 있습니다. You can use this as a placeholder for a part of the sequence whose details are yet to be worked out. Use the name of the interaction use to indicate the outcome that you want.

## <a name="Collapse"></a> Collapsing Groups of Lifelines
 그룹이 하나의 수명선으로 나타나도록 수명선 집합을 함께 축소할 수 있습니다. 이렇게 하면 개체 그룹을 단일 구성 요소로 시각화하는 데 도움이 됩니다. 축소된 그룹에서 수명선 간의 메시지 및 상호 작용 사용은 숨겨집니다. 다른 수명선을 포함하는 메시지 및 상호 작용 시퀀스는 표시됩니다.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>수명선 그룹을 함께 축소하려면

1. 수명선을 두 개 이상 선택합니다.

2. Right-click one of them, and then click **Collapse**.

     개별 수명선이 단일 수명선으로 대체됩니다.

     그룹의 멤버만 포함하는 메시지 및 상호 작용 사용은 숨겨집니다.

3. 그룹의 이름을 바꾸려면 이름을 클릭합니다.

    > [!NOTE]
    > 그룹을 확장하면 그룹 이름이 손실됩니다.

#### <a name="to-expand-a-collapsed-group"></a>축소된 그룹을 확장하려면

- Right-click the collapsed lifeline, and then click **Expand**.

    > [!NOTE]
    > 그룹과 주석 또는 작업 항목 간의 모든 링크와 함께 그룹 이름이 손실됩니다.

## <a name="Fragments"></a> Describing Control Structures with Fragments
 결합 조각(13)을 사용하여 시퀀스 다이어그램에서 루프, 분기 및 동시 처리를 정의할 수 있습니다. 또는 동작 다이어그램을 대신 사용하는 것이 좋습니다. 동작 다이어그램은 행위자 간의 메시지를 표시할 때는 그만큼 유용하지 않지만 일부 경우에서 루프, 분기 및 동시성을 표시할 때 보다 효과적입니다.

 For a full list of the types of fragment, see [Describe control flow with fragments on UML sequence diagrams](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>결합 조각을 만들려면

1. 한 메시지 또는 모두 동일한 실행 발생이나 수명선에서 시작되는 메시지 시퀀스를 선택합니다.

    > [!NOTE]
    > 메시지가 가리키는 실행 발생이 아니라 메시지 화살표를 선택합니다.

2. Right-click one of the messages, point to **Surround With**, and then click the type of fragment that you require.

     새 조각이 나타납니다. 선택한 메시지를 포함합니다.

     결합 조각 형식이 여러 조각을 허용하는 경우 빈 조각도 나타납니다.

3. To set the guard of a fragment, right-click the fragment border, and then click **Properties**. Set the **Guard** property.

     가드는 분기 또는 루프에 대한 조건을 정의하는 데 사용됩니다.

4. To add a new fragment to a kind that allows multiple fragments, right-click the boundary of a fragment, and point to **Add**. Click either **Interaction Operand Before** or **Interaction Operand After**.

5. 조각에 새 메시지를 추가하려면 메시지 도구를 사용하거나 복사하여 붙여넣습니다.

## <a name="see-also"></a>관련 항목:
 [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Sketching Interactions by using Sequence Diagrams](https://go.microsoft.com/fwlink/?LinkId=201113)
