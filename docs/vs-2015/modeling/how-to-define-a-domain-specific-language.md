---
title: How to Define a Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
ms.assetid: d1772463-0eb1-40a5-b7c0-9a008bc76760
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4bcd1f1f023c9e439fb870c9e31f07aa5be215d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299555"
---
# <a name="how-to-define-a-domain-specific-language"></a>도메인별 언어 정의 방법
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL(Domain-Specific Language)을 정의하려면 템플릿에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션을 만듭니다. 이 솔루션의 중요한 요소는 DslDefinition.dsl에 저장되는 DSL 정의 다이어그램입니다. DSL 정의는 DSL의 클래스와 모양을 정의합니다. 이러한 요소를 수정하고 필요한 내용을 추가한 후에 프로그램 코드를 추가하여 DSL을 보다 자세하게 사용자 지정할 수 있습니다.

 If you are new to DSLs, we recommend that you work through the **DSL Tools Lab**, which you can find in this site: [Visualizaton and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a> Selecting a Template Solution
 DSL을 정의하려면 다음 구성 요소를 설치해야 합니다.

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

 새 DSL(Domain-Specific Language)을 만들려면 DSL 프로젝트 템플릿을 사용하여 새 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션을 만듭니다.

#### <a name="to-create-a-dsl-solution"></a>DSL 솔루션을 만들려면

1. Create a solution with the **Domain-Specific Language** template, which can be found under **Other Project Types/Extensibility** in the **New Project** dialog box.

    ![Create DSL dialog](../modeling/media/create-dsldialog.png "Create_DSLDialog")

    When you click **OK**, the **Domain-Specific Language Wizard** opens and displays a list of template DSL solutions.

2. 각 템플릿을 클릭하여 설명을 확인합니다. 만들려는 DSL과 가장 비슷한 솔루션을 선택합니다.

    각 DSL 템플릿은 기본적인 작업 DSL을 정의합니다. 요구 사항에 맞게 이 DSL을 편집합니다.

    각 샘플을 클릭하면 자세한 내용을 확인할 수 있습니다.

   - Select **Task Flow** to create a DSL that has swimlanes. 스윔 레인은 다이어그램의 수직 또는 수평 파티션입니다.

   - Select **Component Models** to create a DSL that has ports. 포트는 큰 모양의 모서리에 있는 작은 모양입니다.

   - Select **Class Diagrams** to define a DSL that has compartment shapes. 구획 모양에는 항목 목록이 포함됩니다.

   - Select **Minimal Language** in other cases, or if you are uncertain.

       > [!NOTE]
       > 클래스 다이어그램 또는 구성 요소 다이어그램을 만들려는 경우에는 UML 모델을 사용할 수 있습니다. UML 모델링 도구는 단일 모델을 중심으로 통합된 다이어그램 집합을 제공합니다. ModelBus를 사용하면 이러한 다이어그램을 확장할 수 있으며 DSL과 통합할 수 있습니다. For more information, see [Create models for your app](../modeling/create-models-for-your-app.md).

   - Select **Minimal WinForm Designer** or **Minimal WPF Designer** to create a DSL that is displayed on a Windows Forms or WPF surface. 편집기를 정의하려면 코드를 작성해야 합니다. 자세한 내용은 다음 항목을 참조하세요.

        [Windows Forms 기반 도메인별 언어 만들기](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [WPF 기반 도메인별 언어 만들기](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. 해당하는 마법사 페이지에서 DSL의 파일 이름 확장명을 입력합니다. 이 확장명은 DSL의 인스턴스가 포함된 파일에 사용됩니다.

   - 현재 사용 중인 컴퓨터 또는 DSL을 설치할 컴퓨터의 애플리케이션과 연결되지 않은 파일 이름 확장명을 선택합니다. For example, **docx** and **htm** would be unacceptable file name extensions.

   - 입력한 확장명이 DSL로 사용되고 있으면 경고가 표시됩니다. 이 경우 다른 파일 이름 확장명을 사용해야 합니다. Visual Studio SDK 실험적 인스턴스를 다시 설정하여 오래된 실험적 디자이너를 지울 수도 있습니다. Click **Start**, click **All Programs**, **Microsoft Visual Studio 2010 SDK**, **Tools**, and then **Reset the Microsoft Visual Studio 2010 Experimental instance**.

4. 다른 페이지에서 설정을 조정하거나 기본값을 그대로 사용할 수 있습니다.

5. **마침**을 클릭합니다.

    2~3개 프로젝트가 포함된 솔루션이 만들어지고 DSL 정의에서 코드가 생성됩니다.

   이제 사용자 인터페이스는 다음 그림과 같이 표시됩니다.

   ![dsl 디자이너](../modeling/media/dsl-designer.png "dsl_designer")

   이 솔루션은 DSL을 정의합니다. For more information, see [Overview of the Domain-Specific Language Tools User Interface](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>솔루션 테스트
 템플릿 솔루션에서 제공하는 작업 DSL을 수정하거나 그대로 사용할 수 있습니다.

 솔루션을 테스트하려면 F5 키나 Ctrl+F5를 누릅니다. 새 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스가 실험적 모드에서 열립니다.

 새 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스의 솔루션 탐색기에서 샘플 파일을 엽니다. 샘플 파일은 도구 상자가 포함된 다이어그램으로 열립니다.

 If you run a solution that you have created from the **Minimal Language** template, your experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] will resemble the following example:

 ![](../modeling/media/dsl-min.png "DSL_min")

 도구를 사용해 보고 요소를 만들어 서로 연결합니다.

 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스를 닫습니다.

> [!NOTE]
> DSL을 수정하면 샘플 테스트 파일에 모양이 더 이상 표시되지 않습니다. 그러나 새 요소를 만들 수는 있습니다.

### <a name="modifying-the-template-dsl"></a>템플릿 DSL 수정
 템플릿 DSL 정의에서 일부 또는 모든 도메인 클래스 및 모양 클래스의 이름을 바꾸고 저장합니다. 새 클래스 이름은 공백이나 문장 부호가 없는 올바른 CLR 이름이어야 합니다.

 이러한 클래스를 저장하면 특히 다음과 같은 경우에 유용합니다.

- The root class appears at the upper-left of the DSL Definition diagram, under **Classes and Relationships**. 해당 클래스의 이름을 DSL과 다르게 바꿉니다. For example, a DSL named **MusicLibrary** might have a root class named **Music**.

- The diagram class appears at the lower right of the DSL Definition diagram, in the **Diagram Elements** column. 해당 열을 보려면 오른쪽으로 스크롤해야 할 수 있습니다. It is typically named _YourDsl_**Diagram**.

- If you used the **Task Flow** template and you want to create diagrams with swimlanes, keep and rename the Actor domain class and ActorSwimlane shape.

  나머지 클래스는 요구 사항에 맞게 삭제하거나 이름을 바꿉니다.

## <a name="patterns"></a> Patterns for Defining a DSL
 한 번에 1~2개 기능을 추가하거나 조정하여 DSL을 개발하는 것이 좋습니다. 기능 하나를 추가하고 DSL을 실행하여 테스트한 다음 1~2개 기능을 더 추가합니다. DSL의 일반적인 기능은 다음과 같습니다.

- 도메인 클래스, 모델에 요소를 연결하는 포함 관계, 다이어그램에서 해당 클래스의 요소를 표시하는 데 필요한 모양, 사용자가 요소를 만드는 데 사용할 수 있는 요소 도구

- 도메인 클래스의 도메인 속성 및 모양에 이러한 속성을 표시하는 Decorator

- 참조 관계, 다이어그램에 참조 관계를 표시하는 연결선 및 사용자가 링크를 만드는 데 사용할 수 있는 연결선 도구

- 유효성 제약 조건 또는 메뉴 명령과 같이 프로그램 코드가 필요한 사용자 지정 항목

  다음 섹션에서는 가장 유용한 유형의 SDL 기능을 생성하는 방법을 설명합니다. DSL을 생성하는 데 사용할 수 있는 기타 여러 패턴이 있지만 여기서는 가장 자주 사용되는 패턴에 대해 설명합니다.

> [!NOTE]
> After adding a feature, do not forget to click **Transform All Templates** in the toolbar of Solution Explorer before you build and running your DSL.

 다음 그림에는 이 항목에서 예로 사용되는 DSL의 클래스 및 관계 부분이 나와 있습니다.

 ![Embedding and Reference relationships](../modeling/media/music-classes.png "Music_Classes")

 그리고 다음 그림에는 이 DSL의 예제 모델이 나와 있습니다.

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

> [!NOTE]
> 여기서 "모델"은 사용자가 만드는 DSL 인스턴스를 지칭하며 대개 다이어그램으로 표시됩니다. 이 항목에서는 DSL 사용 시에 표시되는 DSL 정의 다이어그램 및 모델 다이어그램 둘 다에 대해 설명합니다.

## <a name="classes"></a> Defining Domain Classes
 도메인 클래스는 DSL의 개념을 나타냅니다. The instances are *model elements*. For example in a **MusicLibrary** DSL you might have Domain Classes named **Album** and **Song**.

 To create a domain class, you can drag from the **Named Domain Class** tool to the diagram, and then rename the class.

 For more information, see [Properties of Domain Classes](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>각 도메인 클래스에 대해 포함 관계 만들기
 루트 클래스를 제외한 모든 도메인 클래스는 하나 이상되는 포함 관계의 대상이거나 포함 관계의 대상인 클래스에서 상속해야 합니다.

 모델에서 모든 모델 요소는 포함 관계의 단일 트리에 포함된 노드입니다. 포함 관계의 소스와 대상을 대개 부모와 자식이라고 합니다.

 도메인 클래스의 부모는 다른 요소를 기준으로 클래스 요소의 수명을 지정할 방법에 따라 선택합니다. 일반적으로 트리의 노드를 삭제하면 해당 하위 트리도 삭제됩니다. 그러므로 독립적인 요소의 클래스는 루트 클래스 바로 아래에 포함됩니다.

 대개 다른 요소 내에 요소를 표시할 때는 소유자 관계를 지정합니다. 이 경우 가장 적절한 부모 클래스는 컨테이너의 클래스입니다. 단, 컨테이너 내에 표시되는 항목이 실제로는 단순히 독립 요소의 참조 링크인 경우는 예외입니다. 이 경우에는 컨테이너를 삭제하면 참조만 삭제되며 대상은 삭제되지 않습니다.

 이 항목에서 설명하는 DSL 정의 패턴에서는 컨테이너를 삭제하면 컨테이너 내에 표시되는 요소도 삭제된다고 가정합니다. 규칙을 정의하면 더 복잡한 체계도 사용할 수 있습니다.

|요소 표시 방식|부모(포함) 클래스|DSL 솔루션 템플릿의 예|
|------------------------------|--------------------------------|--------------------------------------|
|다이어그램에 표시된 모양<br /><br /> 스윔 레인|DSL의 루트 클래스|최소 언어<br /><br /> 작업 흐름: 행위자 클래스|
|스윔 레인의 모양|스윔 레인으로 표시되는 요소의 도메인 클래스|작업 흐름: 작업 클래스|
|컨테이너를 삭제하면 항목도 삭제되는 모양 내 목록의 항목<br /><br /> 모양 모서리의 포트|컨테이너 모양에 매핑되는 도메인 클래스|클래스 다이어그램: 특성 클래스<br /><br /> 구성 요소 다이어그램: 포트 클래스|
|컨테이너를 삭제해도 삭제되지 않는 목록의 항목|DSL의 루트 클래스<br /><br /> 목록에 참조 링크가 표시됩니다.||
|직접 표시되지 않음|부분을 구성하는 클래스||

 MusicLibrary 예에서 앨범은 사각형으로 표시되며 그 안에 노래 제목이 나열됩니다. 따라서 Album의 부모는 루트 클래스인 Music이고 Song의 부모는 Album입니다.

 To create a domain class and its embedding at the same time, click the **Embedding Relationship** tool, then click the parent class, and then click on a blank part of the diagram.

 일반적으로 포함 관계와 해당 역할은 클래스 이름을 자동으로 추적하므로 해당 이름을 조정할 필요가 없습니다.

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> 포함은 상속과는 다릅니다. 포함 관계에 있는 자식은 부모로부터 기능을 상속하지 않습니다.

### <a name="add-domain-properties-to-each-domain-class"></a>각 도메인 클래스에 도메인 속성 추가
 도메인 속성에는 값이 저장됩니다. 예를 들어 이름, 제목, 게시 날짜 등이 저장될 수 있습니다.

 Click **Domain Properties** in the class, press the ENTER key, and then type the name of a property. 도메인 속성의 기본 형식은 문자열입니다. If you want to change the type, select the domain property, and set the **Type** in the **Properties** window. If the type that you want is not in the drop-down list, see [Adding Property Types](#addTypes).

 **Set an Element Name property.** Select a domain property that can be used to identify elements in the language explorer. 예를 들어 Song 도메인 클래스에서는 Title 도메인 속성을 선택할 수 있습니다. In the **Properties** window, set **Is Element Name** to `true`.

### <a name="create-derived-domain-classes"></a>파생된 도메인 클래스 만들기
 도메인 클래스에 해당 속성과 관계를 상속하는 변형을 포함하려면 해당 클래스에서 파생되는 클래스를 만듭니다. 예를 들어 Album에는 WMA 및 MP3 파생 클래스가 포함될 수 있습니다.

 Create the derived class using the **Domain Class** tool.

 Click the **Inheritance** tool, click the derived class, and then click the base class.

 Consider setting the **Inheritance Modifier** of the base class to **abstract**. 기본 클래스 인스턴스가 필요한 경우에는 기본 클래스에 대해 별도의 파생 클래스를 만들 수 있습니다.

 파생 클래스는 기본 클래스의 속성과 역할을 상속합니다.

### <a name="tidy-the-dsl-definition-diagram"></a>DSL 정의 다이어그램 정리
 관계를 추가할 때 일부 클래스는 두 곳 이상에 표시됩니다. To reduce the number of appearances and make the diagram wider, right-click the target class of a relationship, and then click **Bring Tree Here**. For the opposite effect, right-click the target class of a relationship and click **Split Tree**. 이러한 메뉴 명령이 표시되지 않으면 도메인 클래스만 선택했는지 확인하세요.

 Ctrl+위쪽 및 Ctrl+아래쪽 화살표를 사용하여 도메인 클래스와 모양 클래스를 이동합니다.

### <a name="test-the-domain-classes"></a>도메인 클래스 테스트

##### <a name="to-test-the-new-domain-classes"></a>새 도메인 클래스를 테스트하려면

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code. 이 단계는 자동화할 수 있습니다. For more information, see [How to Automate Transform All Templates](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스에서 DSL의 파일 이름 확장명이 지정된 파일을 열거나 만듭니다.

3. **Open the Explorer.** At the side of the diagram is the language explorer window, which is usually named *YourLanguage* Explorer. 이 창이 표시되지 않으면 솔루션 탐색기 아래쪽의 탭에 있을 수 있습니다. If you cannot find it, on the **View** menu, point to **Other Windows**, and then click _YourLanguage_**Explorer**.

     탐색기에 모델의 트리 뷰가 표시됩니다.

4. **Create new elements.** Right-click the root node at the top, and then click **Add New**_YourClass_.

     새 클래스 인스턴스가 언어 탐색기에 표시됩니다.

5. 새 인스턴스를 만들 때는 각 인스턴스의 이름이 서로 다른지 확인합니다. This will occur only if you have set the **Is Element Name** flag on a domain property.

6. **Examine the domain properties. With an instance of your class selected,** inspect the Properties window. 그러면 이 도메인 클래스에 대해 정의한 도메인 속성이 표시되어야 합니다.

7. **Save the file, close it, and re-open it**. 노드를 확장하고 나면 작성한 모든 인스턴스가 탐색기에 표시되어야 합니다.

## <a name="shapes"></a> Defining Shapes on the Diagram
 다이어그램에 사각형, 타원 또는 아이콘으로 표시되는 요소 클래스를 정의할 수 있습니다.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>다이어그램에 모양으로 표시되는 요소 클래스를 정의하려면

1. **Define and test a domain class as described in**  [Defining Domain Classes](#classes) **.**

   - 클래스의 부모는 루트 클래스여야 합니다. 즉 루트 클래스와 새 도메인 클래스 간에 포함 관계가 있어야 합니다.

   - 다이어그램에 스윔 레인이 있으면 부모는 스윔 레인에 매핑되는 도메인 클래스일 수 있습니다. Before continuing with this procedure, see [Defining a DSL that has Swimlanes](#swimlanes).

2. **Add a shape class** to represent the elements on the model diagram. 이렇게 하려면 다음 도구 중 하나에서 DSL 정의 다이어그램으로 클래스를 끌어 놓습니다.

   - **Geometry Shape** provides a rectangle or ellipse.

   - **Image Shape** displays an image that you provide.

   - **Compartment Shape** is a rectangle that contains one or more lists of items.

     모양 클래스의 이름을 바꿉니다. 이 이름은 DSL 정의 다이어그램 오른쪽의 모양 및 연결선 아래에 표시됩니다.

3. **Define an image, if you created an image shape**.

   1. 원하는 크기로 이미지 파일을 만듭니다. BMP, JPEG, GIF, EMF 형식이 지원됩니다.

   2. 솔루션 탐색기의 Dsl\Resources에서 파일을 솔루션에 추가합니다.

   3. DSL 정의 다이어그램으로 돌아와 새 이미지 모양 클래스를 선택합니다.

   4. In the Properties window, click the **Image** property.

   5. In the **Select Image** dialog box, click the drop-down menu under **File name**, and select the image.

4. **Add text decorators to the shape, to display the domain properties.**

    모델 요소의 이름이나 제목을 표시하려면 텍스트 Decorator가 하나 이상 필요할 수 있습니다.

    Right-click the header of the shape class, point to **Add**, and then click **Text Decorator**. Set the name of the decorator, and in the Properties window set its **Position**.

5. **Connect each shape with a Diagram Element Map to the domain class that it should display**.

    Click the **Diagram Element Map** tool, then click the domain class, then click the shape class.

6. **Map the properties to the text decorators.**

   1. 다이어그램 요소 맵을 나타내는 모양 클래스와 도메인 클래스 사이의 회색 선을 선택합니다.

   2. In the **DSL Details** window, click the **Decorator Maps** tab. If you do not see the **DSL Details** window, on the **View** menu, point to **Other Windows** and then click **DSL Details**. 모든 내용을 보려면 이 창 위쪽을 올려야 하는 경우가 많습니다.

   3. Decorator의 이름을 선택합니다. Under **Display property**, select the name of a property of the domain class. 각 Decorator에 대해 이 단계를 반복합니다.

       If you want to display a property of a related element, click the drop-down tree navigator under **Path to display property**.

   4. 각 Decorator 이름 옆에 확인 표시가 나타나는지 확인합니다.

      ![Shape Mappings and DSL Details window](../modeling/media/dsldetailswindow.png "DslDetailsWindow")

7. **Make a toolbox item for creating elements of the domain class.**

   1. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

   2. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

       > [!NOTE]
       > If you right-click the **Tools** node, you will not see **Add Element Tool**. 도구 노드 위의 노드를 클릭해야 합니다.

   3. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

   4. Set **Caption** and **Tooltip**.

   5. Set **Toolbox Icon** to an icon that will appear in the toolbox. 이 아이콘은 새 아이콘 또는 다른 도구에 이미 사용한 아이콘으로 설정할 수 있습니다.

        To create a new icon, open Dsl\Resources in **Solution Explorer**. 기존 요소 도구 BMP 파일 중 하나를 복사하여 붙여넣습니다. 붙여넣은 복사본의 이름을 바꾼 다음 두 번 클릭하여 편집합니다.

        Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

   For more information, see [Properties of Geometry Shapes](../modeling/properties-of-geometry-shapes.md) and [Properties of Image Shapes](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>모양을 테스트하려면

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스에서 DSL의 파일 이름 확장명이 지정된 파일을 열거나 만듭니다.

3. **Verify that the element tools appear on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. 속성 창이나 Decorator에서 속성을 편집하면 다른 뷰가 업데이트됩니다.

   모양을 처음으로 테스트한 후에 일부 속성을 조정하고 몇 가지 고급 기능을 더 추가할 수 있습니다. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a> Defining Reference Relationships
 소스 도메인 클래스와 대상 도메인 클래스 간에 참조 관계를 정의할 수 있습니다. 참조 관계는 보통 다이어그램에 연결선(모양 사이의 선)으로 표시됩니다.

 예를 들어 음악 앨범 및 아티스트가 다이어그램에 모양으로 표시되는 경우에는 아티스트를 참여 앨범에 연결하는 ArtistsAppearedOnAlbums 관계를 정의할 수 있습니다. 아래 그림의 예를 참조하세요.

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

 참조 관계는 같은 유형의 요소를 연결할 수도 있습니다. 예를 들어 가족 구성도를 나타내는 DSL에서는 부모와 자식의 관계가 개인 간 참조 관계입니다.

### <a name="define-a-reference-relationship"></a>참조 관계 정의
 참조 관계 도구, 관계의 소스 도메인 클래스, 대상 도메인 클래스를 차례로 클릭합니다. 대상 클래스는 소스 클래스와 같을 수 있습니다.

 각 관계에는 관계 상자 양쪽에 선으로 표시되는 두 역할이 있습니다. 각 역할을 선택하고 속성 창에서 해당 속성을 설정할 수 있습니다.

 **Consider renaming the roles**. 예를 들어 개인 간 관계에서는 기본 이름을 부모/자식, 관리자/부하 직원, 교사/학생 등으로 변경할 수 있습니다.

 **Adjust the multiplicities of each role**, if it is necessary. 각 개인에게 관리자를 한 명까지만 지정하려면 다이어그램의 관리자 레이블 아래에 표시되는 다중성을 0..1로 설정합니다.

 **Add domain properties to the relationship.** In the figure, the Artist-Album relationship has a property of role.

 **Set the Allows Duplicates property of the relationship,** if more than one link of the same class can exist between the same pair of model elements. 예를 들어 교사 한 명이 같은 학생에게 둘 이상의 과목을 가르치도록 허용할 수 있습니다.

 ![Shape maps for connectors](../modeling/media/music-connector.png "Music_Connector")

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>관계를 표시할 연결선 정의
 연결선은 모델 다이어그램의 두 모양 사이에 선을 표시합니다.

 Drag the **Connector** tool onto the DSL definition diagram.

 연결선에 레이블을 표시하려면 텍스트 Decorator를 추가하고 해당 위치를 설정합니다. To let the user move a text decorator, set its **Is Moveable** property.

 Use the **Diagram Element Map** tool to link the connector to the reference relationship.

 With the diagram element map selected, open the **DSL Details** window, and open the **Decorator Maps** tab.

 Select each **Decorator** and set **Display property** to the correct domain property.

 Make sure that a check mark appears next to each item in the **Decorators** list.

### <a name="define-a-connection-builder-tool"></a>연결 작성기 도구 정의
 In the **DSL Explorer** window, expand the **Editor** node and all its subnodes.

 Right-click the node that has the same name as your DSL, and then click **Add New Connection Tool**.

 새 도구를 선택한 상태로 속성 창에서 다음 단계를 수행합니다.

- Set the **Caption** and **Tooltip**.

- Click **Connection Builder** and select the appropriate builder for the new relationship.

- Set **Toolbox Icon** to the icon that you want to appear in the toolbox. 이 아이콘은 새 아이콘 또는 다른 도구에 이미 사용한 아이콘으로 설정할 수 있습니다.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. 기존 요소 도구 BMP 파일 중 하나를 복사하여 붙여넣습니다. 붙여넣은 복사본의 이름을 바꾼 다음 두 번 클릭하여 편집합니다.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

##### <a name="to-test-a-reference-relationship-and-connector"></a>참조 관계 및 연결선을 테스트하려면

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스에서 DSL의 파일 이름 확장명이 지정된 파일을 열거나 만듭니다.

3. **Verify that the connection tool appears on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Create connections** between the shapes. 연결선 도구와 모양을 차례로 클릭하고 다른 모양을 클릭합니다.

6. **Verify that you cannot create connections between inappropriate classes.** For example, if your relationship is between Albums and Artists, verify that you cannot link Artists to Artists.

7. **Verify that the multiplicities are correct. For example, verify that you cannot connect a Person to more than one manager.**

8. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. 속성 창이나 Decorator에서 속성을 편집하면 다른 뷰가 업데이트됩니다.

   연결선을 처음으로 테스트한 후에 일부 속성을 조정하고 몇 가지 고급 기능을 더 추가할 수 있습니다. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a> Defining Shapes that Contain Lists: Compartment Shapes
 구획 모양은 항목 목록을 하나 이상 포함합니다. 예를 들어 MusicLibrary DSL에서는 구획 모양을 사용하여 음악 Album을 표시할 수 있습니다. 각 Album에는 노래 목록이 있습니다.

 ![Compartment Shape](../modeling/media/compartmentshape.png "CompartmentShape")

 DSL 정의에서 이러한 모양을 적용하는 가장 간단한 방법은 컨테이너와 각 목록에 대해 도메인 클래스를 하나씩 정의하는 것입니다. 컨테이너 클래스는 구획 모양에 매핑됩니다.

 ![Shape map](../modeling/media/music-mapcomp.png "Music_MapComp")

 For more information, see [Properties of Compartment Shapes](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>구획 모양을 정의하려면

1. **Create the container domain class**. Click the **Embedding Relationship** tool, click the root class of the model, and then click a blank part of the DSL definition diagram. 그러면 예제 그림과 같이 Album이라는 도메인 클래스가 만들어집니다.

     루트 클래스에 포함하는 대신 스윔 레인에 매핑되는 도메인 클래스에 컨테이너를 포함할 수 있습니다.

     Add a domain property such as Name to the class, and set its **Is Element Name** flag in the Properties window.

2. **Create the list item domain class**. Click the **Embedding Relationship** tool, click the container class (Album) and then click a blank part of the diagram. 그러면 예제 그림과 같이 Song이라는 도메인 클래스가 만들어집니다.

     Add a domain property such as Title to the class, and set its **Is Element Name** flag.

     다른 도메인 속성을 추가합니다.

     표시할 각 목록에 대해 다른 목록 항목 도메인 클래스를 추가합니다.

3. **To mix several types of item in the list**, create classes that inherit from the list class. Make the list class abstract by setting its **Inheritance Modifier**.

     예를 들어 클래식 음악을 아티스트가 아닌 작곡가를 기준으로 정렬하려면 Song의 두 서브클래스 ClassicalSong 및 NonClassicalSong을 만들 수 있습니다.

4. **Create the compartment shape**. Drag from the **Compartment Shape** tool onto the DSL definition diagram.

     텍스트 Decorator를 추가하고 해당 이름을 설정합니다.

     구획을 추가하고 해당 이름을 설정합니다.

5. To let the user hide the list compartments, right-click the compartment shape class, point to **Add**, and then click **Expand/Collapse Decorator**. 속성 창에서 Decorator의 위치를 설정합니다.

6. Click the **Diagram Element Map** tool, click the container domain class, and then click the compartment shape.

7. 모양과 도메인 클래스 사이의 다이어그램 요소 맵 링크를 선택하고 In the **DSL Details** window:

    1. Click the **Decorators** tab. Click the name of the decorator and then select the appropriate item under **Display Property**. Decorator 이름 옆에 확인 표시가 나타나는지 확인합니다.

    2. Click the **Compartment Maps** tab.

         구획의 이름을 클릭합니다.

         Under **Displayed elements collection path**, navigate to the list element class (Song). 탐색기 도구를 사용하려면 드롭다운 화살표를 클릭합니다.

         Under **Display Property**, select the property that should be displayed in the list. 이 예에서 해당 속성은 Title입니다.

> [!NOTE]
> Decorator 맵의 경로 필드와 구획 맵 필드를 사용하면 도메인 클래스와 구획 모양 간에 더 복잡한 관계를 만들 수 있습니다.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>도형을 만들 도구를 정의하려면

1. **Make a toolbox item for creating elements of the domain class.**

2. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

3. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

    > [!NOTE]
    > If you right-click the **Tools** node, you will not see **Add Element Tool**. 도구 노드 위의 노드를 클릭해야 합니다.

4. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

5. Set **Caption** and **Tooltip**.

6. Set **Toolbox Icon** to an icon that will appear in the toolbox. 이 아이콘은 새 아이콘 또는 다른 도구에 이미 사용한 아이콘으로 설정할 수 있습니다.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. 기존 요소 도구 .BMP 파일 중 하나를 복사하여 붙여넣습니다. 붙여넣은 복사본의 이름을 바꾼 다음 두 번 클릭하여 편집합니다.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your BMP file from the drop-down menu.

#### <a name="to-test-a-compartment-shape"></a>구획 모양을 테스트하려면

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스에서 DSL의 파일 이름 확장명이 지정된 파일을 열거나 만듭니다.

3. **Verify that the tool appears on the toolbox.**

4. 도구를 모델 다이어그램으로 끌어 놓습니다. 모양이 만들어집니다.

    요소 이름이 표시되며 기본값으로 자동 설정되는지 확인합니다.

5. Right-click the header of the new shape, and then click Add *Your List Item.* 이 예제에서 해당 명령은 노래 추가입니다.

    목록에 항목이 표시되며 새 이름이 적용되어 있는지 확인합니다.

6. 목록 항목 중 하나를 클릭하고 속성 창을 점검합니다. 목록 항목의 속성이 표시되어야 합니다.

7. 언어 탐색기를 엽니다. 내부에 목록 항목 노드가 포함된 컨테이너 노드가 표시되는지 확인합니다.

   ![Generated explorer of DSL](../modeling/media/music-explorer.png "Music_Explorer")

   구획 모양을 처음으로 테스트한 후에 일부 속성을 조정하고 몇 가지 고급 기능을 더 추가할 수 있습니다. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>구획에 참조 링크 표시
 일반적으로 구획에 표시하는 요소는 구획 모양으로 표시되는 요소의 자식입니다. 그러나 참조 관계를 통해 구획에 연결되는 요소를 표시하는 경우도 있습니다.

 예를 들어 Album에 연결된 Artist 목록을 표시하는 두 번째 구획을 AlbumShape에 추가할 수 있습니다.

 이 경우 구획에는 참조되는 요소가 아닌 링크가 표시되어야 합니다. 사용자가 구획에서 항목을 선택하고 Delete 키를 누르면 참조되는 요소가 아닌 링크가 삭제되어야 하기 때문입니다.

 참조되는 요소의 이름이 구획에 표시되도록 할 수도 있습니다.

 다음 절차에서는 이 섹션 앞부분에서 설명한 대로 도메인 클래스, 참조 관계, 구획 모양 및 다이어그램 요소 맵을 이미 만들었다고 가정합니다.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>구획에 참조 링크를 표시하려면

1. **Add a compartment to the compartment shape**. On the DSL Definition diagram, right-click the compartment shape class, point to **Add**, and then click **Compartment**.

2. Set **Displayed elements collection path** to navigate to the link, instead of its target element. 드롭다운 메뉴를 클릭한 다음 트리 보기를 사용하여 대상이 아닌 참조 관계를 선택합니다. In the example, the relationship is **ArtistAppearedOnAlbums**.

3. Set **Path to Display Property** to navigate from the link to the target element. In the example, this is **Artist**.

4. Set **Display Property** to the appropriate property of the target element, for example **Name**.

5. **Transform All Templates**, build and run the DSL, and open a test model.

6. 모델 다이어그램에서 모양의 해당 클래스를 만들고 이름을 설정한 후에 클래스 간 링크를 만듭니다. 구획 모양에 연결된 요소의 이름이 표시됩니다.

7. 구획 모양에서 링크나 항목을 선택합니다. 링크와 항목이 모두 사라져야 합니다.

## <a name="ports"></a> Defining Ports on the Boundary of another Shape
 포트는 다른 모양의 경계에 있는 모양입니다.

 포트를 사용하여 다른 모양에 고정 연결점을 제공할 수 있습니다. 사용자는 이 연결점에 연결선을 그릴 수 있습니다. 이 경우 포트 모양을 투명하게 지정할 수 있습니다.

 To see an example that uses ports, select the **Component Diagram** template when you create a new DSL solution. 이 예에서는 포트를 정의할 때 고려할 수 있는 주요 항목을 제시합니다.

- 포트의 컨테이너를 나타내는 `Component` 도메인 클래스가 있습니다.

- 포트를 나타내는 도메인 클래스가 있습니다. 이 예에서 해당 클래스는 `ComponentPort`입니다.

- 컨테이너 도메인 클래스에서 포트 도메인 클래스로의 포함 관계가 있습니다. For more information, see [Defining Domain Classes](#classes).

- 같은 컨테이너에서 여러 포트 형식을 혼합하여 사용하려는 경우 포트 도메인 클래스의 서브클래스를 만들 수 있습니다. 이 예에서는 `InPort` 및 `OutPort`가 `ComponentPort`에서 상속합니다.

- 컨테이너 도메인 클래스를 모든 종류의 모양에 매핑할 수 있습니다. 이 예에서 해당 모양은 `ComponentShape`입니다. For more information, see [Defining Shapes](#shapes).

- 포트 도메인 클래스는 포트 모양에 매핑됩니다. 파생 클래스의 개별 포트 모양 클래스에 매핑할 수도 있고 기본 클래스를 포트 모양 클래스에 매핑할 수도 있습니다.

  In other respects, port shapes behave as described in [Defining Shapes](#shapes).

  For more information, see [Properties of Port Shapes](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a> Defining a DSL that has Swimlanes
 스윔 레인은 다이어그램의 수평 또는 수직 파티션입니다. 각 스윔 레인은 모델 요소에 해당합니다. DSL 정의에서는 스윔 레인 요소당 도메인 클래스가 하나씩 있어야 합니다.

 스윔 레인이 포함된 DSL을 만드는 가장 효율적인 방법은 새 DSL 솔루션을 만들고 작업 흐름 솔루션 템플릿을 선택하는 것입니다. DSL 정의에서 Actor 클래스는 스윔 레인에 매핑되는 도메인 클래스입니다. 이 클래스와 기타 클래스의 이름을 프로젝트에 맞게 바꿉니다.

 스윔 레인 내에 모양으로 표시할 클래스를 추가하려면 스윔 레인 클래스와 새 클래스 간에 포함 관계를 만듭니다. 사용자는 스윔 레인 간에 요소를 끌 수 있지만 각 요소는 항상 특정 스윔 레인 내에 포함됩니다. 작업 흐름 솔루션 템플릿에서 FlowElement는 스윔 레인 클래스의 자식입니다.

 스윔 레인과 독립적인 모양으로 표시할 클래스를 추가하려면 루트 클래스와 새 클래스 간에 포함 관계를 만듭니다. 사용자는 스윔 레인 경계와 외부를 비롯하여 다이어그램의 원하는 위치에 이러한 모양을 배치할 수 있습니다. 작업 흐름 솔루션 템플릿에서 Comment는 루트 클래스의 자식입니다.

 For more information, see [Properties of Swimlanes](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a> Adding Property Types

### <a name="domain-enumerations-and-literals"></a>도메인 열거형 및 리터럴
 도메인 열거형은 여러 리터럴 값을 포함하는 형식입니다.

 To add a domain enumeration, right-click the root of the model in the **DSL Explorer** and then click **Add New Domain Enumeration**. The element will appear in the **DSL Explorer** under the **Domain Types** node. 다이어그램에는 이 요소가 표시되지 않습니다.

 To add enumeration literals to the domain enumeration, right-click the domain enumeration in the **DSL Explorer** and then click **Add New Enumeration Literal**.

 기본적으로 열거형 형식의 속성은 한 번에 하나의 열거형 값으로만 설정할 수 있습니다. If you want users and programmers to be able to set any combination of values - a "bit field" - set the **IsFlags** property of the Enumeration.

### <a name="external-types"></a>외부 형식
 When you set the type of a domain property, if you do not find the type you want in the **Type** drop-down list, you can add an external type. For example, you could add the **System.Drawing.Color** type to the list.

 To add a type, right-click the root of the model in DSL Explorer, and then click **Add New External Type**. In the Properties window, set the name to **Color** and the namespace to **System.Drawing**. This type now appears in DSL Explorer under **Domain Types**. 도메인 속성 형식을 설정할 때마다 이 형식을 선택할 수 있습니다.

## <a name="custom"></a> Customizing the DSL
 이 항목에서 설명하는 기술을 사용하면 다이어그램 표기법, 읽을 수 있는 XML 형식 및 코드와 기타 아티팩트를 생성하는 데 필요한 기본적인 도구를 사용해 DSL을 빠르게 만들 수 있습니다.

 두 가지 방법으로 DSL 정의를 확장할 수 있습니다.

1. DSL 정의 기능을 추가로 사용해 DSL을 미세 조정합니다. 예를 들어 여러 연결선 형식을 만들 수 있는 단일 연결선 도구를 만들고, 특정 요소를 삭제하면 관련 요소도 삭제되는 규칙을 제어할 수 있습니다. 이러한 기술은 대부분 DSL 정의에서 값을 설정하는 방식으로 사용하지만 프로그램 코드를 몇 줄 작성해야 하는 기술도 있습니다.

     For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. 보다 고급 효과를 적용하려면 프로그램 코드를 사용하여 모델링 도구를 확장합니다. 예를 들어 모델을 변경할 수 있는 메뉴 명령을 만들고, 둘 이상의 DSL을 통합하는 도구를 만들 수 있습니다. VMSDK는 DSL 정의에서 생성된 코드를 사용하여 확장을 쉽게 통합할 수 있도록 설계되었습니다.  For more information, see [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>DSL 정의 변경
 DSL 정의에서 항목을 만들면 대부분의 기본값은 자동으로 설정됩니다. 설정된 기본값은 변경할 수 있습니다. 따라서 DSL 개발은 간소화하는 동시에 유용한 사용자 지정 기능을 추가할 수 있습니다.

 예를 들어 모양을 요소에 매핑하면 도메인 클래스의 포함 관계에 따라 매핑의 부모 요소 경로가 자동으로 설정됩니다. 그러나 포함 관계를 나중에 변경하는 경우에는 부모 요소 경로가 자동으로 변경되지 않습니다.

 그러므로 DSL 정의에서 일부 관계를 변경하는 경우 주의해야 합니다. 정의를 저장하거나 모든 템플릿 변환을 실행할 때 오류가 보고되는 경우가 있기 때문입니다. 이러한 오류는 대부분 쉽게 해결할 수 있습니다. 오류 보고서를 두 번 클릭하면 오류의 위치를 확인할 수 있습니다.

 See also [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a> Troubleshooting
 아래 테이블에는 DSL을 디자인할 때 가장 흔히 발생하는 몇 가지 문제와 제안 해결 방법이 나와 있습니다. More advice is available on the [Visualization Tools Extensibililty Forum](https://go.microsoft.com/fwlink/?LinkId=186074).

|문제점|제안 해결 방법|
|-------------|----------------|
|DSL 정의 파일에서 수행한 변경 내용이 적용되지 않습니다.|Click **Transform All Templates** in the toolbar above Solution Explorer, and then rebuild the solution.|
|모양에 속성 값이 아닌 Decorator 이름이 표시됩니다.|Decorator 매핑을 설정합니다. 이렇게 하려면 DSL 정의 다이어그램에서 모양 클래스와 도메인 클래스 사이의 회색 선인 다이어그램 요소 맵을 클릭합니다.<br /><br /> Open the **DSL Details** window. If you cannot see it, on the View menu, point to **Other Windows**, and then click **DSL Details**.<br /><br /> Click the **Decorator Maps** tab. Select the name of the decorator. 이름 옆의 확인란이 선택되어 있는지 확인합니다. Under **Display property**, select the name of a domain property.<br /><br /> For more information, see [Shapes on the Diagram](#shapes).|
|DSL 탐색기에서 컬렉션에 항목을 추가할 수 없습니다. 예를 들어 도구를 마우스 오른쪽 단추로 클릭해도 메뉴에 "도구 추가" 명령이 표시되지 않습니다.<br /><br /> DSL 탐색기에서 목록에 요소를 추가할 수 없습니다.|요소를 추가하려는 노드 위의 항목을 마우스 오른쪽 단추로 클릭합니다. 목록에 항목을 추가하려는 경우 추가 명령은 목록 노드가 아닌 해당 소유자에 있습니다.|
|도메인 클래스를 만들었는데 언어 탐색기에서 인스턴스를 만들 수 없습니다.|루트를 제외한 모든 도메인 클래스는 포함 관계의 대상이어야 합니다.|
|DSL 탐색기에는 요소와 형식 이름만 표시됩니다.|In the DSL Definition, select a domain property of the class and in the Properties window, set **Is Element Name** to true.|
|DSL이 항상 XML 편집기에서 열립니다.|파일을 읽는 동안 오류가 발생하면 이러한 현상이 발생할 수 있습니다. 그러나 해당 오류를 해결한 후에도 명시적으로 편집기를 DSL 디자이너로 다시 설정해야 합니다.<br /><br /> Right-click the project item, click **Open With** and select _YourLanguage_**Designer (Default)** .|
|어셈블리 이름을 변경한 후 DSL의 도구 상자가 표시되지 않습니다.|Inspect and update **DslPackage\GeneratedCode\Package.tt** For more information, see [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|어셈블리 이름을 변경하지 않았는데 DSL의 도구 상자가 표시되지 않습니다.<br /><br /> 또는 확장을 로드하지 못했음을 보고하는 메시지 상자가 표시됩니다.|실험적 인스턴스를 다시 설정하고 솔루션을 다시 빌드합니다.<br /><br /> 1.  At the Windows Start menu, under **All Programs**, expand [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)], then **Tools**, and then click **Reset the Microsoft Visual Studio Experimental Instance**.<br />2.  On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**.|

## <a name="see-also"></a>관련 항목:
 [Getting Started with Domain-Specific Languages](../modeling/getting-started-with-domain-specific-languages.md) [Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md) [Creating a WPF-Based Domain-Specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md)
