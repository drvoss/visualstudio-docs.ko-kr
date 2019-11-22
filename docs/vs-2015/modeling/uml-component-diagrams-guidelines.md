---
title: 'UML Component Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297153"
---
# <a name="uml-component-diagrams-guidelines"></a>UML 구성 요소 다이어그램: 지침
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *component diagram* to show the structure a software system. For a video demonstration, see [Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure).

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 To create a UML component diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 구성 요소는 환경 내에서 대체할 수 있는 모듈식 단위입니다. Its internals are hidden, but it has one or more well-defined *provided interfaces* through which its functions can be accessed. A component can also have *required interfaces*. 필요한 인터페이스는 다른 구성 요소로부터 요청하는 기능 또는 서비스를 정의합니다. 여러 구성 요소의 제공된 인터페이스와 필요한 인터페이스를 연결하면 더 큰 구성 요소를 생성할 수 있습니다. 결과적으로 전체 소프트웨어 시스템을 하나의 구성 요소로 이해할 수 있습니다.

 구성 요소 다이어그램을 그리면 다음과 같은 몇 가지 이점을 얻을 수 있습니다.

- 주요 블록 관점에서 디자인을 생각하면 개발 팀이 기존 디자인을 이해하고 새 디자인을 만드는 데 도움이 됩니다.

- 시스템을 제공된 인터페이스와 필요한 인터페이스가 잘 정의되어 있는 구성 요소 컬렉션으로 간주하면 구성 요소 간 분리를 개선할 수 있습니다. 즉, 디자인을 잘 이해하고 요구 사항이 변경될 경우 쉽게 변경할 수 있게 됩니다.

  구성 요소 다이어그램을 사용하면 현재 또는 앞으로 사용할 언어나 플랫폼에 관계없이 디자인을 나타낼 수 있습니다.

## <a name="OtherDiagrams"></a> Relationship to Other Diagrams
 구성 요소 다이어그램을 다른 다이어그램과 함께 사용할 수 있습니다.

|다른 다이어그램|디자인과 관련하여 논의하고 의견을 교환할 요소|
|-------------------|--------------------------------------------------------------------|
|UML 시퀀스 다이어그램|-   Interactions between a system's components<br />-   Interactions and between the parts inside a component.<br /><br /> For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).|
|UML 클래스 다이어그램|-   The interfaces of a component. 클래스 다이어그램을 사용하여 인터페이스의 메서드를 자세히 설명할 수 있습니다.<br />-   The data sent in parameters across the components' interfaces.<br /><br /> For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).|
|동작 다이어그램|-   The internal processing performed by a component in response to incoming messages.<br /><br /> For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).|
|레이어 다이어그램|-   Logical architectural tiers for your components.<br /><br /> For more information, see [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).|

## <a name="Basics"></a> Basic Steps for Drawing Component Diagrams
 For reference information about the elements on component diagrams, see [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md).

 For more information about how to use component diagrams in the process of design, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-component-diagram"></a>구성 요소 다이어그램을 만들려면

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Component Diagram**.

3. 다이어그램 이름을 지정합니다.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**..

     A new component diagram appears with the UML **Component Diagram** toolbox. 이 도구 상자에는 필요한 요소 및 관계가 포함되어 있습니다.

### <a name="drawing-components"></a>구성 요소 그리기
 ![Components with interfaces](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 Create a *component* (1) for each major functional unit in your system or application.

 예를 들면 애플리케이션, 하드웨어 디바이스, 웹 서비스, .NET 어셈블리, 프로그램 클래스나 클래스 그룹 또는 프로그램의 분리 가능 세그먼트 등이 있습니다.

##### <a name="to-create-components"></a>구성 요소를 만들려면

1. Click **Component** in the toolbox, and then click a blank part of the diagram.

     \- 또는 -

     기존 구성 요소를 복사하여 붙여넣습니다.

    1. Find an existing component in a diagram or in **UML Model Explorer**.

    2. Right-click the component and then click **Copy**.

    3. 복사한 구성 요소를 나타낼 다이어그램을 엽니다.

    4. Right-click a blank part of the diagram and then click **Paste**.

         새 이름이 지정된 구성 요소 복사본이 나타납니다.

2. 이름을 변경하려면 구성 요소의 이름을 클릭합니다.

3. 구성 요소의 헤더만 표시하려면 펼침 단추(5)를 클릭합니다.

### <a name="showing-the-ports-of-a-component"></a>구성 요소의 포트 표시
 A *port* (2, 3) represents a group of messages or operation calls that pass either into or out of a component. 이 그룹은 포트 형식을 정의하는 인터페이스에 의해 기술됩니다. 포트는 인터페이스를 제공하거나 요청할 수 있습니다.

 A port with a *provided interface* (2) supplies operations that are implemented by the component, and that can be used by other components.

 예를 들면 사용자 인터페이스, 웹 서비스, .NET 인터페이스 또는 프로그래밍 언어의 함수 컬렉션 등이 있습니다.

 A port with a *required interface* (3) represents a component's requirement for a group of operations or services to be provided by other components or external systems.

 예를 들면 웹 브라우저가 웹 서버를 요청하거나 애플리케이션 추가 기능이 애플리케이션의 서비스를 요청하는 경우입니다.

 구성 요소에 사용할 수 있는 포트 수에는 제한이 없습니다.

##### <a name="to-add-ports-to-a-component"></a>구성 요소에 포트를 추가하려면

1. In the toolbox, click **Provided Interface** or **Required Interface**.

2. 포트를 추가할 구성 요소를 클릭합니다.

    구성 요소의 경계에 포트가 나타납니다.

    이 포트의 형식으로 새 인터페이스가 만들어집니다. This interface appears in **UML Model Explorer**.

3. 구성 요소 경계 주위에서 포트를 끌어 원하는 위치에 놓습니다.

4. 포트 레이블을 끌어 위치를 조정합니다.

5. 레이블을 변경하려면 클릭합니다. 레이블에는 인터페이스 이름이 표시됩니다. 즉, 레이블을 변경하면 인터페이스의 이름이 변경됩니다.

   인터페이스의 특성과 작업을 나열하려면 UML 모델 탐색기에 추가하십시오. 또는 UML 모델 탐색기의 인터페이스를 클래스 다이어그램으로 끌어 놓은 다음, 여기에 작업과 특성을 추가할 수 있습니다.

### <a name="linking-between-components"></a>구성 요소 간 연결
 종속성(4)을 사용하면 다른 구성 요소에서 제공하는 작업 또는 서비스로 구성 요소의 요구 사항이 충족될 수 있음을 나타낼 수 있습니다.

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>제공된 인터페이스로 필요한 인터페이스를 충족시킬 수 있음을 나타내려면

1. In the toolbox, click **Dependency**.

2. 한 구성 요소에서 필요한 인터페이스가 있는 포트를 클릭한 다음, 다른 구성 요소에서 제공된 인터페이스가 있는 포트를 클릭합니다.

   그룹의 모든 구성 요소가 다른 모든 구성 요소에 종속되는 종속성 루프를 디자인하지 않도록 해야 합니다.

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>기존 인터페이스의 포트를 구성 요소에 추가하려면

- Find the interface in **UML Model Explorer** and then drag it from there onto the component.

     또는

- 다이어그램에서 인터페이스에 대한 참조를 복사하여 붙여넣습니다.

    1. On a class diagram or a component diagram, right-click the interface and then click **Copy**.

    2. On the component diagram, right-click the component, and then click **Paste Reference**.

         제공된 인터페이스가 구성 요소에 나타나고 근처에 작업 태그가 나타납니다.

        > [!NOTE]
        > If you use **Paste** instead of **Paste Reference**, a new interface that has a new name will be created.

    3. If you wanted to create a required interface, click the Action tag and then click **Convert to Required Interface**.

## <a name="Parts"></a> Showing the Internal Parts of a Component
 ![Component diagram showing internal parts](../modeling/media/uml-compshowing.png "UML_CompShowing")

 구성 요소(1)에 파트(3)를 배치하면 구성 요소가 서로 상호 작용하는 더 작은 구성 요소로 어떻게 이루어져 있는지 나타낼 수 있습니다.

 그림의 다이어그램에서는 Dinner Now Web Service 형식의 모든 인스턴스에 Customer Server 인스턴스 하나와 Kitchen Server 인스턴스 하나가 포함되어 있음을 보여 줍니다.

 파트는 부모 구성 요소의 속성이며, 대체로 특성이 일반 클래스에 속하는 것과 같습니다. 파트에는 고유 형식이 있으며 이 형식도 대개 구성 요소입니다. 파트 레이블은 다음과 같이 일반 특성과 형식이 같습니다.

 `+ partName : TypeName`

 부모 구성 요소 내에서 각 파트는 형식에 대해 정의된 제공된 인터페이스와 필요한 인터페이스를 보여 줍니다(4, 5). 한 파트에 필요한 작업 또는 서비스는 다른 파트에서 제공할 수 있습니다. You can use **Part Assembly** connectors to show how parts are connected with one another (6).

 부모 구성 요소의 인터페이스가 실제로 제공되었는지 아니면 파트 중 하나에 필요한지를 나타낼 수도 있습니다. You can connect a port of the parent to a port of an internal part using a **Delegation** relation (9). 이때 두 포트는 종류(제공된 포트 또는 필요한 포트)가 같아야 하고 인터페이스 형식이 호환되어야 합니다.

 새 형식을 지정하거나 기존 형식을 사용하여 새 파트를 만들 수 있습니다.

#### <a name="to-add-parts-to-a-component"></a>구성 요소에 파트를 추가하려면

1. 부모 구성 요소의 파트로 간주하는 각 주요 기능 단위에 대한 파트를 만듭니다.

    1. Click **Component** in the toolbox, and then click inside the parent component (1).

         새 파트(3)가 부모 구성 요소 내에 나타납니다.

         A new component is created in **UML Model Explorer**. 이 구성 요소가 새 파트의 형식입니다.

         \- 또는 -

         UML 모델 탐색기의 기존 구성 요소를 부모 구성 요소로 끌어 옵니다.

         새 파트(3)가 부모 구성 요소 내에 나타납니다. 새 파트의 형식은 UML 모델 탐색기에서 끌어 온 구성 요소입니다.

         \- 또는 -

         Right-click a component, either in a diagram or in UML Model Explorer, and then click **Copy**.

         Right-click on the parent component, and then click **Paste Reference**.

         새 파트(3)가 부모 구성 요소 내에 나타납니다. 새 파트의 형식은 복사한 구성 요소입니다.

    2. 이름을 변경하려면 새 파트의 이름을 클릭합니다. 형식은 변경할 수 없습니다.

    3. 제공된 인터페이스와 필요한 인터페이스(4, 5)를 새 파트에 추가할 수 있습니다. Click the **Provided Interface** or **Required Interface** tool, and then click in the part.

         \- 또는 -

         Drag an existing interface from **UML Model Explorer** onto the part.

         인터페이스가 파트 형식에 추가되고 파트 자체에 나타납니다. 필요한 경우 부모 구성 요소가 크기를 조정합니다.

2. 파트를 다른 파트에 연결합니다.

    - Use the **Dependency** tool to connect the ports of different parts (6).

3. 파트를 부모 구성 요소의 포트에 연결합니다.

    1. 부모 구성 요소에 하나 이상의 포트(7)를 만듭니다. Click **Required Interface** or **Provided Interface** on the toolbox, and then click the parent component.

    2. 포트를 하나 이상의 파트에 위임합니다(9). Click the **Delegation** tool, then a port on the parent component, and then a port on a part. 인터페이스를 제공하거나 요청하는 포트를 같은 방식으로 연결할 수 있습니다.

### <a name="showing-the-parts-of-a-part"></a>파트의 파트 표시
 구성 요소를 파트로 분해한 후에는 각 파트 형식을 고유한 내부 파트로 분해할 수 있습니다.

 별도의 구성 요소 다이어그램에서 분해 레이어를 각각 처리하는 것이 더 간단합니다. 먼저 파트의 형식을 찾아야 합니다. 예를 들어 그림에서 한 파트의 이름은 `DNCustomerServer`이고 형식은 `CustomerServer`라는 구성 요소입니다. UML 모델 탐색기에서 이 형식을 찾아 다른 다이어그램에 배치할 수 있습니다. 그런 다음 고유한 내부 파트를 만들 수 있습니다.

##### <a name="to-place-a-parts-type-on-a-diagram"></a>파트의 형식을 다이어그램에 배치하려면

1. 파트 형식의 정규화된 이름을 확인합니다.

     Right-click the part and then click **Properties**.

     The type name appears in the **Type** field of the Properties window.

2. Locate the part's type in **UML Model Explorer**.

     Click **View**, point to **Other Windows**, and then click **UML Model Explorer**.

     프로젝트를 확장하고, 필요한 경우 형식이 속한 패키지도 확장합니다.

     The type will be listed as a **Component**.

     원하는 경우 이름을 변경할 수 있습니다.

3. 다른 구성 요소 다이어그램을 열거나 만듭니다.

4. UML 모델 탐색기의 형식을 다이어그램으로 끌어 옵니다.

     형식 뷰가 다이어그램에서 구성 요소로 나타납니다.

     파트에 정의한 것과 같은 인터페이스가 포함되어 있습니다.

     이제 내부에 파트를 추가할 수 있습니다.

## <a name="Designing"></a> Designing the Component

### <a name="describing-how-the-parts-collaborate"></a>파트의 공동 작업 방식 기술
 부모 구성 요소에 도착하는 메시지에 응답하여 파트가 공동으로 작업하는 방식을 나타내기 위해 시퀀스 다이어그램을 그릴 수 있습니다.

 이러한 다이어그램을 사용하면 기존 구성 요소를 설명하고 새 구성 요소를 디자인할 수 있습니다.

 아직 구성 요소를 디자인하는 중이면 구성 요소에 포함할 파트를 결정하기 전에 시퀀스 다이어그램을 그릴 수 있습니다. 시퀀스 다이어그램을 사용하면 파트, 필요한 인터페이스 및 메시지 시퀀스 등을 다르게 하여 실험해 볼 수 있습니다. 들어오는 메시지 중에서 가장 많고 가장 중요한 메시지에 대해 시퀀스 다이어그램을 그립니다. 그런 다음 결정한 수명선에 해당하는 파트를 구성 요소에 만들 수 있습니다.

 시퀀스 다이어그램을 사용하면 시스템 작업이 서로 다른 구성 요소 간에 분산되는 방식을 평가할 수 있습니다.

- 작업이 한 파트에만 너무 많으면 고르게 분산된 경우에 비해 애플리케이션에서 업데이트하기가 어렵습니다.

- 상호 작용이 많아서 작업이 너무 적게 분산되면 시스템 성능이 저하되고 이해하기가 어렵습니다.

  ![Sequence diagram showing collaborating parts](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>파트 간 협업을 나타내는 시퀀스 다이어그램을 그리려면

1. 새 시퀀스 다이어그램을 만듭니다.

     For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

2. 이 구성 요소에 메시지를 보내는 외부 구성 요소, 사용자, 디바이스 또는 다른 행위자(1)에 대한 수명선을 만듭니다.

     You can set the **Actor** property of this lifeline to true, to indicate that it is external to the component under consideration. 수명선 위에 사람 모양 아이콘이 나타납니다.

3. 선택한 행위자가 메시지를 보내는 이 구성 요소의 제공된 인터페이스(2)에 대한 수명선을 만듭니다.

4. 구성 요소의 각 파트(3)에 대한 수명선을 만듭니다.

5. 구성 요소의 각 필요한 인터페이스(4)에 대한 수명선을 만듭니다.

6. 외부 행위자(5)에서 메시지를 가져옵니다. 메시지가 파트에 전달되는 방식 및 파트가 공동으로 이 메시지에 응답하는 방식을 나타내십시오.

7. 필요한 경우 필요한 인터페이스(6)에 전송되는 메시지를 표시합니다. 메시지 실행 내부의 세부 정보는 나타내지 마세요.

### <a name="is-the-component-more-than-its-parts"></a>파트의 하위로 사용되는 구성 요소
 구성 요소가 파트 컬렉션에 지정된 이름일 뿐인 경우도 있습니다. 모든 작업은 파트에서 수행되고 런타임에 구성 요소를 나타내는 코드 또는 다른 아티팩트가 없습니다.

 You can indicate this in the model by setting the **Is Indirectly Instantiated** property of the component. 이 경우에는 구성 요소의 모든 인터페이스가 내부 파트에 위임된 상태로 포트에 있어야 합니다.

### <a name="describing-the-process-inside-each-part"></a>각 파트 내에 프로세스 기술
 동작 다이어그램을 사용하면 구성 요소가 들어오는 각 메시지를 처리하는 방식을 나타낼 수 있습니다. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 ![Activity diagram with data buffer](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 이벤트 적용 동작(1)을 사용하여 들어오는 메시지가 새 스레드를 시작한다는 것을 나타냅니다.

 개체 노드 및 입/출력 핀을 사용하여 정보 흐름을 표시하고 정보 저장 위치를 나타냅니다. 이 예제에서는 스레드 간에 버퍼링되는 항목을 나타내기 위해 개체 노드(2)를 사용합니다.

### <a name="defining-data-and-classes"></a>데이터 및 클래스 정의
 UML 클래스 다이어그램을 사용하여 다음 요소의 자세한 내용을 기술할 수 있습니다.

- 구성 요소의 인터페이스 구성 요소에 포트를 추가하면 UML 모델 탐색기에 인터페이스가 나타납니다. 이 인터페이스를 UML 클래스 다이어그램으로 끌어 놓거나 복사해서 특성, 작업 및 기타 인터페이스에 대한 관계를 보여줄 수 있습니다.

- 인터페이스에서 작업 매개 변수에 전달된 데이터

- 구성 요소에 저장된 데이터(예: 동작 다이어그램에서 개체 흐름에 표시)

### <a name="general-dependencies-between-components"></a>구성 요소 간의 일반 종속성
 디자인의 주요 파트 및 파트의 상호 종속성만 나타내려는 경우 구성 요소 다이어그램을 사용할 수 있습니다.

 ![A dependency between components](../modeling/media/uml-compdepend.png "UML_CompDepend")

 Use the **Dependency** tool to draw a dependency. 이는 한 구성 요소의 디자인이 다른 구성 요소를 기반으로 한다는 것을 나타냅니다.

 일반적인 종속성 유형은 다음과 같습니다.

- 한 구성 요소가 다른 구성 요소 내의 코드를 호출합니다.

- 한 구성 요소가 다른 클래스에 정의되어 있는 클래스를 인스턴스화합니다.

- 한 구성 요소가 다른 구성 요소에서 만든 정보를 사용합니다.

  종속성 화살표의 이름을 사용하여 특정 용도를 나타낼 수 있습니다. To set the name, right-click the arrow, then click **Properties**, and set the **Name** field in the properties window.

## <a name="see-also"></a>관련 항목:
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
