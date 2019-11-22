---
title: 'UML Class Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c170827825d772f4d97cd22f0b5754232e8d2257
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297291"
---
# <a name="uml-class-diagrams-guidelines"></a>UML 클래스 다이어그램: 지침
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *UML class diagram* to describe data types and their relationships separately from their implementation. 이 다이어그램은 클래스의 구현 대신 논리적 측면에 중점을 둘 때 사용됩니다.

 To create a UML class diagram, on the **Architecture** menu, choose **New UML Diagram or Layer Diagram**.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

> [!NOTE]
> 이 항목에서는 UML 클래스 다이어그램에 대해 설명합니다. 이외에도 프로그램 코드를 시각화하는 데 사용하기 위해 만들 수 있는 다른 종류의 클래스 다이어그램이 있습니다. See [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="Using"></a> Using UML Class Diagrams
 다음과 같은 다양한 용도로 UML 클래스 다이어그램을 사용할 수 있습니다.

- 시스템에 사용되고 구성 요소 간에 전달되는 형식에 대해 구현과 독립적인 설명을 제공할 수 있습니다.

     예를 들어 .NET 코드의 비즈니스 계층, XML의 구성 요소 간 인터페이스, SQL의 데이터베이스 및 HTML의 사용자 인터페이스 등에서 Meal Order 형식을 구현할 수 있습니다. 이러한 구현은 세부적으로는 다르지만 Menu와 Payment 같은 다른 형식과 Meal Order 간의 관계는 항상 같습니다. UML 클래스 다이어그램을 사용하면 이러한 관계를 구현과 분리하여 논의할 수 있습니다.

- 애플리케이션과 사용자 간의 통신에 사용되고 사용자 요구를 기술하는 데 필요한 용어 모음을 명확하게 정의할 수 있습니다. See [Model user requirements](../modeling/model-user-requirements.md).

     예를 들어 식당 애플리케이션의 사용자 스토리, 사용 사례 또는 기타 요구 사항을 설명하는 경우를 가정해 봅니다. 이러한 설명에서 Menu, Order, Meal, Price, Payment 등의 용어를 발견할 수 있습니다. 이때 이러한 용어 간의 관계를 정의하는 UML 클래스 다이어그램을 그릴 수 있습니다. 그러면 요구 사항 설명, 사용자 인터페이스 및 도움말 문서 등에서 용어 불일치 문제가 줄어듭니다.

### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계
 일반적으로 UML 클래스 다이어그램을 그릴 때는 다른 모델링 다이어그램도 함께 그려 해당 다이어그램에서 사용하는 형식을 기술합니다. 각 경우에서 형식의 실제 표현은 다른 다이어그램에 포함되지 않습니다.

 동작 다이어그램

 개체 노드를 통과하는 데이터의 형식

 입력 핀, 출력 핀 및 동작 매개 변수 노드의 형식

 See [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 시퀀스 다이어그램

 매개 변수 형식 및 메시지 반환 값

 수명선 형식. 수명선의 클래스에는 수신할 수 있는 모든 메시지에 대한 작업이 포함되어야 합니다.

 See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

 구성 요소 다이어그램

 구성 요소 인터페이스, 각 인터페이스의 작업 목록

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 사용 사례 다이어그램

 사용 사례의 목표 및 단계를 기술할 때 언급된 형식

 See [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Class Diagrams
 For reference information about the elements on UML class diagrams, see [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-uml-class-diagram"></a>UML 클래스 다이어그램을 만들려면

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **UML Class Diagram**.

3. 다이어그램 이름을 지정합니다.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then choose **OK**.

     A new class diagram appears with the **UMLClass Diagram** Toolbox. 이 도구 상자에는 필요한 요소 및 관계가 포함되어 있습니다.

#### <a name="to-draw-a-uml-class-diagram"></a>UML 클래스 다이어그램을 그리려면

1. To create a type, choose the **Class**, **Interface** or **Enumeration** tool on the Toolbox, and then click a blank part of the diagram. (도구 상자가 표시되지 않은 경우 Ctrl + ALT + X를 누릅니다.)

2. To add attributes or operations to the types, or literals to an enumeration, choose the **Attributes**, **Operations** or **Literals** heading in the type, and press ENTER.

     `f(x:Boolean):Integer`와 같은 시그니처를 작성할 수 있습니다. See [Attributes and Operations](#AttributesAndOperations).

     여러 항목을 빠르게 추가하려면 각 항목의 끝에서 Enter 키를 두 번 누릅니다. 화살표 키를 사용하여 목록에서 위 또는 아래로 이동할 수 있습니다.

3. 형식을 확장하거나 축소하려면 왼쪽 위에 있는 펼침 아이콘을 선택합니다. You can also expand and collapse the **Attributes** and **Operations** section of a class or interface.

4. 형식 간의 연결, 상속 또는 종속성 링크를 그리려면 적절한 도구를 클릭하고 소스 형식과 대상 형식을 차례로 클릭합니다.

5. To create types in a package, create a package using the **Package** tool, and then create new types and packages within the package. 복사 명령을 사용하여 형식을 복사한 후 패키지에 붙여넣을 수도 있습니다.

6. 모든 다이어그램은 같은 프로젝트에서 다른 다이어그램과 공유하는 모델 뷰입니다. To see a tree view of the complete model, choose **View**, **Other Windows**, **UML Model Explorer**.

## <a name="UsingTypes"></a> Using Classes, Interfaces, and Enumerations
 도구 상자에서 사용할 수 있는 표준 분류자에는 세 가지 종류가 있습니다. These are referred to as *types* throughout this document.

 ![A class, an enumeration, and an interface](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Use **Classes** (1) to represent data or object types for most purposes.

- Use **Interfaces** (2) in a context where you have to differentiate between pure interfaces and concrete classes that have internal implementations. 이런 식으로 구별하면 다이어그램으로 소프트웨어 구현을 기술하려는 경우 유용합니다. 그러나 수동 데이터를 모델링하는 경우 또는 사용자 요구 사항을 기술하는 데 사용되는 개념을 정의하는 경우에는 별로 유용하지 않습니다.

- Use an **Enumeration** (3) to represent a type that has a limited number of literal values, for example `Stop` and `Go`.

  - 리터럴 값을 열거형에 추가하고 각각 별도의 이름을 지정합니다.

  - 원하는 경우 각 리터럴 값에 숫자 값을 제공할 수도 있습니다. Open the shortcut menu for the literal in the enumeration, choose **Properties**, and then type a number in the **Value** field in the **Properties** window.

  각 형식에 고유한 이름을 지정합니다.

### <a name="getting-types-from-other-diagrams"></a>다른 다이어그램에서 형식 가져오기
 다른 다이어그램의 형식을 UML 클래스 다이어그램에 나타낼 수 있습니다.

 UML 클래스 다이어그램

 둘 이상의 UML 클래스 다이어그램에 클래스를 나타낼 수 있습니다. When you have created a class on one diagram, drag the class from **UML Model Explorer** onto the other diagram.

 이 방법은 각 다이어그램에서 특정 관계 그룹에 중점을 두려는 경우 유용합니다.

 예를 들어 한 다이어그램에서 Meal Order와 Menu 간 연결을 나타내고 다른 다이어그램에서 Meal Order와 Payment 간 연결을 나타낼 수 있습니다.

 구성 요소 다이어그램

 If you have defined interfaces on the components in a component diagram, you can drag an interface from **UML Model Explorer** onto the class diagram. 클래스 다이어그램에서 인터페이스를 포함하는 메서드를 정의할 수 있습니다.

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 UML 시퀀스 다이어그램

 You can create classes and interfaces from lifelines in a sequence diagram, and then drag the class from **UML Model Explorer** to a UML class diagram. 시퀀스 다이어그램의 각 수명선은 개체, 구성 요소 또는 행위자의 인스턴스를 나타냅니다.

 To create a class from a lifeline, open the shortcut menu for the lifeline, and then choose **Create Class** or **Create Interface**. See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a> Attributes and Operations
 특성(4)은 형식의 모든 인스턴스가 가질 수 있는 명명된 값입니다. 특성에 액세스하면 인스턴스의 상태가 변경되는 것이 아닙니다.

 작업(5)은 형식의 인스턴스가 수행할 수 있는 메서드 또는 함수입니다. 이때 값을 반환할 수 있습니다. If its **isQuery** property is true, it cannot change the state of the instance.

 To add an attribute or operation to a type, open the shortcut menu for the type, choose **Add**, and then choose **Attribute** or **Operation**.

 To see its properties, open the shortcut menu for the attribute or operation, and then choose **Properties**. The properties appear in the **Properties** window.

 To see the properties of an operation's parameters, choose <strong>[…]</strong>in the **Parameters** property. 그러면 새 속성 대화 상자가 나타납니다.

 설정할 수 있는 모든 속성에 대한 자세한 내용은 다음을 참조하세요.

- [UML 클래스 다이어그램 특성의 속성](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML 클래스 다이어그램 작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>특성 및 작업의 형식
 Each *Type* of an attribute or operation, and each parameter type, can be one of the following:

- **(none)** - You can leave a type unspecified in the signature by omitting the preceding colon (`:`).

- One of the standard primitive types: **Boolean**, **Integer**, **String**.

- 모델에 정의된 형식

- A parameterized value of a template type, written Template\<Parameter>. See [Template Types](#Templates).

  모델에 아직 정의하지 않은 형식의 이름을 작성할 수도 있습니다. The name will be listed under **Unspecified Types** in UML Model Explorer.

> [!NOTE]
> 그런 다음 이 이름의 클래스 또는 인터페이스를 모델에 정의하더라도 기존 특성 및 작업에서는 여전히 지정되지 않은 형식의 요소를 참조합니다. 기존 특성 및 작업에서 새 클래스를 참조하도록 변경하려면 각 특성 또는 작업의 드롭다운 메뉴에서 새 클래스를 선택하여 형식을 다시 설정해야 합니다.

#### <a name="multiple-types"></a>여러 형식
 특성, 작업 또는 매개 변수 형식의 복합성을 설정할 수 있습니다.

 허용된 값은 다음과 같습니다.

 `[1]`

 지정된 형식의 단일 값. 기본값입니다.

 `[0..1]`

 **Null** or a value of the given type.

 `[*]`

 지정된 형식의 여러 인스턴스로 구성된 컬렉션

 `[1..*]`

 지정된 형식의 인스턴스가 최소한 하나 이상 포함된 컬렉션

 `[n..m]`

 지정된 형식의 인스턴스가 `n`개에서 `m`개까지 포함된 컬렉션

 복합성이 1보다 크면 다음 속성도 설정할 수 있습니다.

- **IsOrdered** - If true, the collection has a defined order.

- **IsUnique** - If true, there are no duplicate values in the collection.

### <a name="visibility"></a>표시 유형
 *Visibility* indicates whether the attribute or operation can be accessed outside the class definition. 허용된 값은 다음과 같습니다.

 **Public**

 **+**

 다른 모든 형식에서 액세스할 수 있습니다.

 **전용**

 **-**

 이 형식의 내부 정의에만 액세스할 수 있습니다.

 **패키지**

 **~**

 이 형식을 포함하는 패키지 및 형식을 명시적으로 가져오는 패키지에서만 액세스할 수 있습니다. See [Defining Namespaces and Packages](#Packages).

 **보호됨**

 **#**

 이 형식 및 이 형식에서 상속되는 형식에만 액세스할 수 있습니다. See [Inheritance](#Inheritance).

### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>특성 또는 작업의 시그니처 설정
 특성 또는 작업의 시그니처는 표시 유형, 이름, 매개 변수(작업의 경우) 및 형식을 포함하는 속성 컬렉션입니다.

 다이어그램에서 직접 시그니처를 작성할 수 있습니다. 특성 또는 작업을 클릭하여 선택한 다음, 다시 클릭합니다.

 다음과 같은 형식으로 시그니처를 작성합니다.

```
visibility attribute-name : Type
```

 \- 또는 -

```
visibility operation-name (parameter1 : Type1, ...) : Type
```

 예를 들어 다음과 같은 가치를 제공해야 합니다.

```
+ AddItem (item : MenuItem, quantity : Integer) : Boolean
```

 약식 표시 유형을 사용합니다. 기본값은 `+`(공용)입니다.

 각 형식은 모델에 정의한 형식, 정수나 문자열 같은 표준 형식 또는 아직 정의하지 않은 새 형식의 이름이 될 수 있습니다.

> [!NOTE]
> 매개 변수 목록에 형식 없이 이름을 작성하면 매개 변수의 형식 대신 이름을 나타냅니다. 이 예제의 경우 MenuItem과 Integer는 형식이 지정되지 않은 두 매개 변수의 이름이 됩니다.
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 시그니처에서 형식의 복합성을 설정하려면 다음 예제와 같이 형식 이름 다음에 대괄호를 사용하여 복합성을 작성합니다.

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 특성 또는 작업이 정적이면 시그니처에서 이름에 밑줄이 표시되고 추상인 경우에는 이름이 기울임꼴로 표시됩니다.

 However, you can only set the **Is Static** and **Is Abstract** properties in the **Properties** window.

#### <a name="full-signature"></a>전체 시그니처
 특성 또는 작업의 시그니처를 편집하는 경우 줄의 끝과 각 매개 변수 뒤에 몇 가지 추가 속성이 나타날 수 있습니다. 이러한 속성은 중괄호 {…} 안에 포함되어 있으며 편집하거나 추가할 수 있습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 속성은 다음과 같습니다.

 `unique`

 **Is Unique**

 컬렉션에 중복 값이 없습니다. 복합성이 1보다 큰 형식에 적용됩니다.

 `ordered`

 **Is Ordered**

 컬렉션이 시퀀스입니다. false이면 첫 번째 항목이 명확하지 않습니다. 복합성이 1보다 큰 형식에 적용됩니다.

 `query`

 **Is Query**

 작업이 인스턴스의 상태를 변경하지 않습니다. 작업에만 적용됩니다.

 `/`

 **Is Derived**

 특성이 다른 특성의 값 또는 연결에서 계산됩니다.

 특성 이름 앞에 "/"가 나타납니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

```
/TotalPrice: Integer
```

 일반적으로 전체 시그니처는 편집하는 동안에만 다이어그램에 나타나고 편집이 끝나면 추가 속성이 숨겨집니다. If you want to see the full signature all the time, open the shortcut menu for the type, and then choose **Show Full Signature**.

## <a name="Associations"></a> Drawing and Using Associations
 두 요소 간의 링크가 소프트웨어에서 구현되는 방식에 관계없이 링크의 종류를 나타낼 때 연결을 사용합니다. 예를 들어 C#의 포인터, 데이터베이스의 관계, XML 파일에서 각 파트 간 상호 참조 등을 나타낼 때 연결을 사용할 수 있습니다. 이러한 연결은 지구와 태양 같이 실재하는 개체 간의 연결을 나타낼 수 있으며, 해당 정보가 존재한다는 것만 알려 줄 뿐 링크를 나타내는 방법에 대해서는 알려 주지 않습니다.

### <a name="properties-of-an-association"></a>연결의 속성
 연결을 만든 후에는 속성을 설정합니다. Open the shortcut menu for the association, and then choose **Properties**.

 In addition to the properties of the association as a whole, each *role*, that is, each end of the association, has some properties of its own. To view them, expand the **First Role** and **Second Role** properties.

 각 역할의 일부 속성은 다이어그램에서 직접 볼 수 있습니다. 그 차이점은 다음과 같습니다.

- 역할 이름. 다이어그램에서 연결의 끝에 나타납니다. You can set it either on the diagram or in the **Properties** window.

- **Multiplicity**, which defaults to **1**. 마찬가지로 다이어그램에서 연결의 끝에 나타납니다.

- **Aggregation**. 이 속성은 연결선의 한 쪽 끝에 다이아몬드 모양으로 나타납니다. 집합체 역할의 인스턴스가 다른 역할의 인스턴스를 소유하거나 포함한다는 것을 나타낼 때 사용할 수 있습니다.

- **Is Navigable**. 한 역할에 대해서만 true이면 탐색 가능 방향에 화살표가 나타납니다. 소프트웨어에서 데이터베이스 관계 및 링크의 탐색 가능성을 나타낼 때 이 속성을 사용할 수 있습니다.

  For the full details of these and other properties, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>탐색 가능성
 연결을 그리면 한쪽 끝에 화살표가 표시되어 그 방향으로 연결을 탐색할 수 있음을 나타냅니다. 이는 클래스 다이어그램이 소프트웨어 클래스를 나타내고 연결이 포인터나 참조를 나타내는 경우에 유용합니다. 그러나 클래스 다이어그램을 사용하여 엔터티 및 관계나 비즈니스 개념을 나타내는 경우는 탐색 가능성을 나타내는 것과 관련이 적습니다. 이 경우에는 화살표 없이 연결을 그릴 수 있습니다. You can do so by setting the **Is Navigable** property on both ends of the association to True.

### <a name="attributes-and-associations"></a>특성 및 연결
 연결은 그림으로 특성을 나타내는 방법입니다. 예를 들어 Menu 형식의 특성이 있는 Restaurant 클래스를 만드는 대신 Restaurant에서 Menu로 이어지는 연결을 그릴 수 있습니다.

 각 특성 이름은 역할 이름이 되고, 소유하는 형식에서 연결의 반대쪽 끝에 나타납니다. 예를 들어 다음 그림에서 `myMenu`를 보십시오.

 일반적으로 기본 형식과 같이 다이어그램에 그리지 않는 형식에 대해서만 특성을 사용하는 것이 좋습니다.

 ![Equivalent association and attributes](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a> 상속
 Use the **Inheritance** tool to create the following relationships:

- A *generalization* relationship between a specialized type and a general type

   \- 또는 -

- A *realization* relation between a class and an interface that it implements.

  상속 관계에서는 루프를 만들 수 없습니다.

### <a name="generalization"></a>일반화
 일반화는 특수화 또는 파생 형식이 일반 형식이나 기본 형식의 특성, 작업 및 연결을 상속한다는 것을 의미합니다.

 일반 형식은 관계의 화살촉 끝에 나타납니다.

 상속된 작업 및 특성은 대개 특수화 형식에 표시되지 않습니다. 그러나 상속된 작업을 특수화 형식의 작업 목록에 추가할 수 있습니다. 이 방법은 특수화 형식에서 작업의 일부 속성을 재정의하거나, 구현하는 코드에서 수행해야 할 작업을 나타내려는 경우 유용합니다.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>특수화 형식에서 작업의 정의를 재정의하려면

1. 일반화 관계를 클릭합니다.

    관계가 강조 표시된 상태로 나타나고 작업 태그가 주변에 나타납니다.

2. Click the Action tag, and then click **Override Operations**.

    The **Override Operations** dialog box appears.

3. Select the operations that you want to appear in the specializing type, and then click **OK**.

   선택한 작업이 특수화 형식에 나타납니다.

### <a name="realization"></a>인식
 인식은 클래스가 인터페이스에 지정된 특성 및 작업을 구현하는 것을 의미합니다. 인터페이스는 연결선의 화살표 끝에 있습니다.

 인식 연결선을 만들면 인터페이스의 작업이 자동으로 인식 클래스에 복제됩니다. 인터페이스에 새 작업을 추가하는 경우에도 이러한 작업이 인식 클래스에 복제됩니다.

 인식 관계를 만든 후에는 롤리팝 표기로 변환할 수 있습니다. Right-click the relationship and choose **Show as Lollipop**.

 이렇게 하면 인식 링크로 인해 클래스 다이어그램을 복잡하게 만들지 않고 클래스에서 구현하는 인터페이스를 표시할 수 있습니다. 또한 인터페이스와 이 인터페이스를 구현하는 클래스를 별도의 다이어그램에 표시할 수도 있습니다.

 ![Realization shown with conector and lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a> Template Types
 다른 형식이나 값에 의해 매개 변수화될 수 있는 제네릭 또는 템플릿 형식을 정의할 수 있습니다.

 예를 들어 다음과 같이 키 및 값 형식에 의해 매개 변수화된 제네릭 Dictionary를 만들 수 있습니다.

 ![Template class with two parameters](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>템플릿 형식을 만들려면

1. 클래스 또는 인터페이스를 만듭니다. 이 클래스 또는 인터페이스가 템플릿 형식이 됩니다. 그런 다음 적절하게 이름을 지정합니다(예: `Dictionary`).

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Properties** window, click **[…]** in the **Template Parameters** field.

    The **Template Parameter Collection Editor** dialog box appears.

4. **추가**를 선택합니다.

5. 이름 속성을 템플릿 형식의 매개 변수 이름으로 설정합니다(예: `Key`).

6. Set **Parameter Kind**. The default is **Class**.

7. If you want the parameter to accept only derived classes of a particular base class, set **Constrained Value** to the base class that you want.

8. Add as many parameters as you need, then choose **OK**.

9. 다른 클래스에 했던 것과 마찬가지로 템플릿 형식에 특성 및 작업을 추가합니다.

     You can use parameters whose kind is **Class**, **Interface** or **Enumeration** in the definition of attributes and operations. 예를 들어 다음과 같이 `Key`와 `Value`라는 클래스 매개 변수를 사용하여 `Dictionary`에 이 작업을 정의할 수 있습니다.

     `Get(k : Key) : Value`

     You can use a parameter whose kind is **Integer** as a bound in a multiplicity. 예를 들어 정수 매개 변수 max를 사용하여 특성의 복합성을 `[0..max]`로 정의할 수 있습니다.

   템플릿 형식을 만들었으면 템플릿 바인딩을 정의하는 데 사용할 수 있습니다.

   ![A  class bound from the Dictionary template](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>템플릿 형식을 사용하려면

1. 새 형식을 만듭니다(예: `AddressTable`).

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Template Binding** property, select the template type, for example `Dictionary`, from the drop-down list.

4. Expand the **Template Binding** property.

     템플릿 형식의 각 매개 변수에 대한 행이 나타납니다.

5. 각 매개 변수에 적절한 값을 설정합니다. 예를 들어 `Key` 매개 변수를 `Name`이라는 클래스로 설정합니다.

## <a name="Packages"></a> Packages
 UML 클래스 다이어그램에서 패키지를 볼 수 있습니다. 패키지는 다른 모델 요소를 포함하기 위한 컨테이너입니다. 패키지 내에 어떤 요소라도 만들 수 있습니다. 다이어그램에서 패키지를 움직이면 해당 패키지에 포함된 요소도 움직이게 됩니다.

 확장/축소 컨트롤을 사용하여 패키지 내용을 표시하거나 숨길 수 있습니다.

 See [Define packages and namespaces](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a> Generating Code from UML Class Diagrams
 UML 클래스 다이어그램에 대한 클래스 구현을 시작하려면 C# 코드를 생성하거나 코드 생성에 대한 템플릿을 사용자 지정합니다. 제공된 C# 템플릿을 사용하여 코드 생성을 시작하려면

- Open the shortcut menu for the diagram or an element, choose **Generate Code**, and then set the necessary properties.

     For more information about how to set these properties and customize the provided templates, see [Generate code from UML class diagrams](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>관련 항목:
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [Model user requirements](../modeling/model-user-requirements.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md)
