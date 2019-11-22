---
title: Customizing Tools and the Toolbox | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a5e2a46a2326c123d6b7b4e85fa29908ede9fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299338"
---
# <a name="customizing-tools-and-the-toolbox"></a>도구 및 도구 상자 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자가 모델에 추가할 수 있도록 할 요소에 대해 도구 상자 항목을 정의해야 합니다. 도구에는 요소 도구와 연결 도구의 두 가지 종류가 있습니다. 사용자는 생성된 디자이너에서 요소 도구를 선택해 도형을 다이어그램으로 끌고 연결 도구를 선택해 도형 간에 링크를 그릴 수 있습니다. 일반적으로 요소 도구를 사용하면 도메인 클래스 인스턴스를 모델에 추가할 수 있으며 연결 도구를 사용하면 도메인 관계 인스턴스를 추가할 수 있습니다.

 항목 내용:

- [How the Toolbox is Defined](#ToolboxDef)

- [요소 도구 사용자 지정](#customizing)

- [Creating Groups of Elements from a Tool](#groups)

- [Customizing Connection Tools](#connections)

## <a name="ToolboxDef"></a> How the toolbox is defined
 DSL 탐색기에서 편집기 노드와 그 아래의 노드를 확장합니다. 일반적으로는 다음과 같은 계층 구조가 표시됩니다.

```

Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool

```

 DSL 탐색기의 이 부분에서 다음 작업을 수행할 수 있습니다.

- 새 탭 만들기. 탭은 도구 상자의 섹션 제목을 정의합니다.

- 새 도구 만들기

- 도구 복사/붙여넣기

- 도구를 목록에서 위/아래로 이동

- 탭과 도구 삭제

> [!IMPORTANT]
> DSL 탐색기에서 항목을 추가하거나 붙여넣으려면 새 노드의 상위 부모를 마우스 오른쪽 단추로 클릭합니다. For example, to add a tool, right-click the tab, and not the **Tools** node. To add a tab, right-click the **Editor** node.

 The **Toolbox Icon** property of every tool references a 16x16 bitmap file. These files are usually kept in the **Dsl\Resources** folder.

 The **Class** property of an element tool refers to a concrete domain class. 도구는 기본적으로 이 클래스의 인스턴스를 만듭니다. 그러나 도구가 요소 그룹이나 다른 형식의 요소를 만들도록 코드를 작성할 수 있습니다.

 The **Connection Builder** property of a connection tool refers to a connection builder, which defines what types of elements the tool can connect, and what relationships it creates between them. 연결 작성기는 DSL 탐색기의 노드로 정의되며 도메인 관계를 정의할 때 자동으로 만들어지지만 연결 작성기를 사용자 지정하는 코드를 작성할 수 있습니다.

#### <a name="to-add-a-tool-to-the-toolbox"></a>도구 상자에 도구를 추가하려면

1. 요소 도구는 일반적으로 도형 클래스를 만들고 도메인 클래스에 매핑한 후 만듭니다.

     연결선 도구는 대개 연결선 클래스를 만들고 참조 관계에 매핑한 후 만듭니다.

2. In DSL Explorer, expand the **Editor** node and the **Toolbox Tabs** node.

     Right-click a toolbox tab node, and then click **Add New Element Tool** or **Add New Connection Tool**.

3. Set the **Toolbox Icon** property to refer to a 16x16 bitmap.

     If you want to define a new icon, create a bitmap file in Solution Explorer in the **Dsl\Resources** folder. The file should have the following property values: **Build Action** = **Content**; **Copy to Output Directory** = **Do not copy**.

4. **For an element tool:** Set the **Class** property of the tool to refer to a concrete domain class that is mapped to a shape.

     **For a connector tool:** Set the **Connection Builder** property of the tool to one of the items that are offered in the drop-down list. 연결 작성기는 연결선을 도메인 관계에 매핑하면 자동으로 만들어집니다. 최근에 연결선을 만든 경우에는 보통 연결된 연결 작성기를 선택합니다.

5. DSL을 테스트하려면 F5 키나 Ctrl+F5를 누르고 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 실험 인스턴스에서 샘플 모델 파일을 엽니다. 도구 상자에 새 도구가 표시되어야 합니다. 해당 도구를 다이어그램으로 끌어 새 요소가 만들어지는지 확인합니다.

     도구가 표시되지 않으면 실험 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 중지합니다. In the Windows **Start** menu, run **Reset the Microsoft Visual Studio 2010 Experimental Instance**. On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**. 그런 후에 DSL을 다시 테스트합니다.

## <a name="customizing"></a> Customizing Element Tools
 도구는 기본적으로 지정한 클래스의 단일 인스턴스를 만들지만 두 가지 방법을 통해 이 기본 옵션을 변경할 수 있습니다.

- 다른 클래스에 대해 요소 병합 지시문을 정의하여 해당 클래스가 이 클래스의 새 인스턴스를 수락하고 새 요소를 만들 때 추가 링크를 만들 수 있도록 설정합니다. 예를 들어 사용자가 다른 요소에 주석을 놓아 두 요소 간에 참조 링크를 만들도록 허용할 수 있습니다.

     이러한 사용자 지정은 사용자가 요소를 붙여넣거나 끌어서 놓을 때 수행되는 작업에도 영향을 줍니다.

     For more information, see [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md).

- 요소 그룹을 만들 수 있도록 도구를 사용자 지정하는 코드를 작성합니다. 그러면 도구가 재정의 가능한 ToolboxHelper.cs의 메서드를 통해 초기화됩니다. For more information, see [Creating Groups of Elements from a Tool](#groups).

## <a name="groups"></a> Creating Groups of Elements from a Tool
 각 요소 도구는 만들어야 하는 요소의 프로토타입을 포함합니다. 기본적으로 각 요소 도구는 단일 요소를 만들지만 도구 하나로 관련 개체 그룹을 만들 수도 있습니다. 이렇게 하려면 관련 항목이 포함된 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>을 사용하여 도구를 초기화합니다.

 다음 예제는 Transistor 형식이 포함된 DSL에서 가져온 것입니다. 각 Transistor에는 명명된 Terminal 세 개가 있습니다. Transistor용 요소 도구는 모델 요소 4개와 관계 링크 3개가 포함된 프로토타입을 저장합니다. 사용자가 도구를 다이어그램으로 끌면 프로토타입이 인스턴스화되어 모델 루트에 연결됩니다.

 This code overrides a method that is defined in **Dsl\GeneratedCode\ToolboxHelper.cs**.

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }

```

## <a name="connections"></a> Customizing Connection Tools
 일반적으로는 새 연결선 클래스를 만들 때 요소 도구를 만듭니다. 두 도구의 형식을 통해 관계 형식을 결정하도록 허용하여 도구 하나를 재정의할 수도 있습니다. 예를 들어 사용자 간 관계와 사용자 대 지역 관계를 모두 만들 수 있는 연결 도구 하나를 정의할 수 있습니다.

 연결 도구는 연결 작성기를 호출합니다. 연결 작성기를 통해 사용자가 생성된 디자이너에서 요소를 연결할 수 있는 방법을 지정합니다. 연결 작성기는 연결 가능한 요소 및 해당 요소 간에 작성되는 링크의 종류를 지정합니다.

 도메인 클래스 간에 참조 관계를 만들면 연결 작성기가 자동으로 만들어집니다. 연결 도구를 매핑할 때 이 연결 작성기를 사용할 수 있습니다. For more information about how to create connection tools, see [Configuring the Toolbox](../modeling/customizing-tools-and-the-toolbox.md).

 기본 연결 작성기가 다른 소스 및 대상 형식 범위를 처리하고 다른 관계 형식을 만들도록 수정할 수 있습니다.

 또한 연결 작성기에 대해 사용자 지정 코드를 작성하여 연결의 소스 및 대상 클래스를 지정하고 설정할 연결 형식을 정의하며 연결 작성과 관련된 기타 작업을 수행할 수 있습니다.

### <a name="the-structure-of-connection-builders"></a>연결 작성기의 구조
 연결 작성기는 도메인 관계와 소스/대상 요소를 지정하는 링크 연결 지시문을 하나 이상 포함합니다. For example, in the Task Flow solution template, you can see the **CommentReferencesSubjectsBuilder** in the **DSL Explorer**. This connection builder contains one link connect directive named **CommentReferencesSubjects**, which is mapped to the domain relationship **CommentReferencesSubjects**. 이 링크 연결 지시문은 `Comment` 도메인 클래스를 가리키는 소스 역할 지시문과 `FlowElement` 도메인 클래스를 가리키는 대상 역할 지시문을 포함합니다.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>연결 작성기를 사용하여 소스 및 대상 역할 제한
 연결 작성기를 사용하여 지정된 도메인 관계의 소스 역할 또는 대상 역할에서 특정 클래스의 발생을 제한할 수 있습니다. 다른 도메인 클래스에 대한 도메인 관계가 포함된 기본 도메인 클래스가 있는데 기본 클래스의 모든 파생된 클래스가 해당 관계에서 같은 역할을 포함하지 않도록 지정하려는 경우를 예로 들 수 있습니다. In the Task Flow solution, there are four concrete domain classes (**StartPoint**, **EndPoint**, **MergeBranch**, and **Synchronization**) that inherit directly from the abstract domain class **FlowElement**, and two concrete domain classes (**Task** and **ObjectInState**) that inherit indirectly from it. There is also a **Flow** reference relationship that takes **FlowElement** domain classes in both its source role and target role. However, an instance of an **EndPoint** domain class should not be the source of an instance of a **Flow** relationship, nor should an instance of a **StartPoint** class be the target of an instance of a **Flow** relationship. The **FlowBuilder** connection builder has a link connect directive named **Flow** that specifies which domain classes can play the source role (**Task**, **MergeBranch**, **StartPoint**, and **Synchronization**) and which can play the target role(**MergeBranch**, **Endpoint**, and **Synchronization**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>여러 링크 연결 지시문이 포함된 연결 작성기
 연결 작성기에 링크 연결 지시문을 두 개 이상 추가할 수 있습니다. This can help you hide some of the complexities of the domain model from users and keep the **Toolbox** from getting too cluttered. 서로 다른 여러 도메인 관계에 대한 링크 연결 지시문을 단일 연결 작성기에 추가할 수 있습니다. 그러나 대략적으로 비슷한 기능을 수행하는 도메인 관계는 결합해야 합니다.

 In the Task Flow solution, the **Flow** connection tool is used to draw instances of both the **Flow** and the **ObjectFlow** domain relationships. The **FlowBuilder** connection builder has, in addition to the **Flow** link connect directive described earlier, two link connect directives named **ObjectFlow**. These directives specify that an instance of an **ObjectFlow** relationship may be drawn between instances of the **ObjectInState** domain class, or from an instance of an **ObjectInState** to an instance of a **Task**, but not between two instances of a **Task**, or from an instance of a **Task** to an instance of an **ObjectInState**. However, an instance of a **Flow** relationship may be drawn between two instances of a **Task**. If you compile and run the Task Flow solution, you can see that drawing a **Flow** from an instance of an **ObjectInState** to an instance of a **Task** creates an instance of an **ObjectFlow**, but drawing a **Flow** between two instances of a **Task** creates an instance of a **Flow**.

### <a name="custom-code-for-connection-builders"></a>연결 작성기용 사용자 지정 코드
 사용자 인터페이스에는 연결 작성기의 여러 사용자 지정 형식을 정의하는 4개 확인란이 있습니다.

- the **Custom accept** check box on a source or target role directive

- the **Custom connect** check box on a source or target role directive

- the **Uses custom connect** check box on a connect directive

- the **Is Custom** property of the connection builder

  이러한 사용자 지정을 수행하려면 프로그램 코드를 입력해야 합니다. 입력해야 하는 코드를 확인하려면 위의 확인란 중 하나를 선택하고 모든 템플릿 변환을 클릭한 후에 솔루션을 빌드합니다. 그러면 오류 보고서가 표시됩니다. 오류 보고서를 두 번 클릭하면 추가해야 하는 코드를 설명하는 주석이 표시됩니다.

> [!NOTE]
> 사용자 지정 코드를 추가하려면 GeneratedCode 폴더의 코드 파일이 아닌 별도의 코드 파일에 부분 클래스 정의를 만듭니다. 작업 내용 손실을 방지하려면 생성된 코드 파일을 편집해서는 안 됩니다. For more information, see [Overriding and Extending the Generated Classes](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>사용자 지정 연결 코드 만들기
 In each link connect directive, the **Source role directives** tab defines from what types you can drag. Similarly, the **Target role directives** tab defines to what types you can drag. For each type, you can further specify whether to allow the connection (for that link connect directive) by setting the **Custom Accept** flag and then supplying the extra code.

 연결 설정 시 수행되는 작업도 사용자 지정할 수 있습니다. 예를 들어 특정 클래스에서/클래스로 끌기가 수행되는 경우만 사용자 지정하거나 단일 링크 연결 지시문이 적용되는 모든 경우를 사용자 지정하거나 전체 FlowBuilder 연결 작성기를 사용자 지정할 수 있습니다. 이러한 각 옵션에 대해 사용자 지정 플래그를 적절한 수준으로 설정할 수 있습니다. 모든 템플릿을 변환하고 솔루션 빌드를 시도하는 경우 오류 메시지에 생성된 코드의 주석이 표시됩니다. 이러한 주석을 통해 입력해야 하는 코드를 확인할 수 있습니다.

 구성 요소 다이어그램 샘플에서는 Connection 도메인 관계의 연결 작성기가 사용자 지정되어 포트 간에 설정할 수 있는 연결을 제한합니다. 다음 그림에서는 `OutPort` 요소에서 `InPort` 요소로만 연결할 수 있지만 각 요소를 서로 중첩할 수 있음을 보여줍니다.

 **Connection Coming in to an OutPort from a Nested Component**

 ![Connection Builder](../modeling/media/connectionbuilder-3.png "ConnectionBuilder_3")

 따라서 중첩된 구성 요소에서 OutPort로의 연결이 가능하도록 지정할 수 있습니다. To specify such a connection, you set **Uses Custom Accept** on the **InPort** type as source role and the **OutPort** type as target role in the **DSL Details** window as shown in the following illustrations:

 **Link Connect Directive in DSL Explorer**

 ![Connection builder image](../modeling/media/connectionbuilder-4a.png "ConnectionBuilder_4a")

 **Link Connect Directive in DSL Details Window**

 ![](../modeling/media/connectionbuilder-4b.png "ConnectionBuilder_4b")

 그런 다음 ConnectionBuilder 클래스에서 메서드를 입력해야 합니다.

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts…
```

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

 예를 들어 비슷한 코드를 통해 사용자가 부모-자식 링크를 포함하는 루프를 만들지 못하도록 지정할 수 있습니다. 이러한 제한은 사용자가 어떤 경우에도 위반할 수 없으므로 '하드' 제한으로 간주됩니다. 사용자가 저장할 수 없는 잘못된 구성을 만들어 일시적으로 건너뛸 수 있는 '소프트' 유효성 검사를 만들 수도 있습니다.

### <a name="good-practice-in-defining-connection-builders"></a>적절한 연결 작성기 정의 사례
 개념적으로 관련이 있는 경우에만 단일 연결 작성기가 여러 관계 형식을 만들도록 정의해야 합니다. 작업 흐름 샘플에서는 같은 작성기를 사용하여 작업 간에 그리고 작업과 개체 간에 흐름을 만듭니다. 그러나 같은 작성기를 사용해 주석과 작업 간에 관계를 만들면 관계를 혼동할 수도 있습니다.

 여러 관계 형식에 대해 연결 작성기 하나를 정의하는 경우에는 연결 작성기가 같은 소스 및 대상 개체 쌍의 형식 두 개 이상과 일치하지 않도록 해야 합니다. 이렇게 하지 않으면 결과를 예측할 수가 없습니다.

 사용자 지정 코드를 사용하면 '하드' 제약 조건을 적용할 수 있지만 이 경우 사용자가 일시적으로 잘못된 연결을 설정할 수 있어야 하는지를 고려해야 합니다. 사용자가 일시적으로 잘못된 연결을 설정할 수 있어야 하는 경우에는 사용자가 변경 내용을 저장할 때까지 연결 유효성을 검사하지 않도록 제약 조건을 수정할 수 있습니다.

## <a name="see-also"></a>관련 항목:
 [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md) [Customizing Copy Behavior](../modeling/customizing-copy-behavior.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)
