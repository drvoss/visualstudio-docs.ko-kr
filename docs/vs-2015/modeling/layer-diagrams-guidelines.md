---
title: 'Layer Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51cb71d4bc2f66377b677d5be292c4eafa1dbd18
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299457"
---
# <a name="layer-diagrams-guidelines"></a>레이어 다이어그램: 지침
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Describe your app's architecture at a high level by creating *layer diagrams* in Visual Studio. 레이어 다이어그램에서 코드의 유효성을 검사하여 코드가 디자인과 일치하는지 확인합니다. 빌드 프로세스에 레이어 유효성 검사를 포함할 수도 있습니다. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="what-is-a-layer-diagram"></a>레이어 다이어그램의 정의
 전형적인 아키텍처 다이어그램처럼 레이어 다이어그램은 디자인의 주요 구성 요소나 기능 단위와 해당 상호 종속성을 식별합니다. Each node on the diagram, called a *layer*, represents a logical group of namespaces, projects, or other artifacts. 디자인에 존재해야 하는 종속성을 그릴 수 있습니다. 전형적인 아키텍처 다이어그램과 달리 소스 코드의 실제 종속성이 사용자가 지정한 의도한 종속성에 부합되는지 확인할 수 있습니다. 유효성 검사를 [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]에 대한 정기 빌드의 일부로 포함하여 프로그램 코드가 향후 변경되더라도 시스템의 아키텍처와 계속 일치하도록 할 수 있습니다. See [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).

## <a name="Update"></a> How to design or update your app with layer diagrams
 다음 단계는 개발 프로세스 내에서 레이어 다이어그램의 사용 방법을 간단히 설명합니다. 이 항목의 뒷부분에 나오는 섹션에서는 각 단계에 대해 좀 더 자세히 설명합니다. 새 디자인을 개발하는 경우 기존 코드를 참조하는 단계는 생략하도록 합니다.

> [!NOTE]
> 이러한 단계는 대략적인 순서로 나타납니다. 작업을 중복하고 상황에 맞게 순서를 변경하며 프로젝트에서 각 반복이 시작될 때 다시 확인할 수 있습니다.

1. [Create a layer diagram](#Create) for the whole application, or for a layer within it.

2. [Define layers to represent primary functional areas or components](#CreateLayers) of your application. 해당 기능에 따라 이러한 레이어의 이름을 지정합니다(예: "프레젠테이션" 또는 "서비스"). If you have a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution, you can associate each layer with a collection of *artifacts*, such as projects, namespaces, files, and so on.

3. [Discover the existing dependencies](#Generate) between layers.

4. [Edit the layers and dependencies](#EditArchitecture) to show the updated design that you want the code to reflect.

5. [Design new areas of your application](#NewAreas) by creating layers to represent the principal architectural blocks or components and defining dependencies to show how each layer uses the others.

6. [Edit the layout and appearance of the diagram](#EditLayout) to help you discuss it with colleagues.

7. [Validate the code against the layer diagram](#Validate) to highlight the conflicts between the code and the architecture you require.

8. [Update the code to conform to your new architecture](#UpdateCode). 유효성 검사 결과로 충돌이 나타나지 않을 때까지 반복적으로 코드를 개발하고 리팩터링합니다.

9. [Include layer validation in the build process](#BuildValidation) to ensure that the code continues to adhere to your design.

## <a name="Create"></a> Create a layer diagram
 레이어 다이어그램은 모델링 프로젝트 내에서 만들어져야 합니다. 기존 모델링 프로젝트에 새 레이어 다이어그램을 추가하거나 레이어 다이어그램에 대해 새 모델링 프로젝트를 만들거나 동일한 모델링 프로젝트 내에서 기존 레이어 다이어그램을 복사할 수 있습니다.

> [!IMPORTANT]
> 한 모델링 프로젝트에서 다른 모델링 프로젝트나 솔루션의 다른 위치로 기존 레이어 다이어그램을 추가하거나 끌어 놓거나 복사하지 않도록 합니다. 이러한 방식으로 복사된 레이어 다이어그램은 다이어그램을 수정하더라도 원본 다이어그램과 동일한 참조를 갖게 됩니다. 그러면 레이어 유효성 검사가 제대로 작동하지 않고 다이어그램을 열려고 할 때 요소 누락이나 기타 오류 등의 다른 문제가 발생할 수 있습니다.

 See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Define layers to represent functional areas or components
 Layers represent logical groups of *artifacts*, such as projects, code files, namespaces, classes, and methods. Visual C# .NET 및 Visual Basic.NET 프로젝트의 아티팩트에서 레이어를 만들거나 문서(예: Word 파일 또는 PowerPoint 프레젠테이션)를 연결하여 사양 또는 계획을 레이어에 연결할 수 있습니다. 각 레이어는 다이어그램에서 직사각형으로 나타나고 그에 연결된 아티팩트의 수를 보여줍니다. 레이어에는 보다 구체적인 작업을 설명하는 중첩된 레이어가 포함될 수 있습니다.

 일반적인 지침대로 해당 기능에 따라 레이어의 이름을 지정합니다(예: "프레젠테이션" 또는 "서비스"). 아티팩트가 밀접하게 상호 종속되는 경우 동일한 레이어에 배치합니다. 아티팩트를 개별적으로 업데이트하거나 별도 애플리케이션에서 사용할 수 있는 경우 다른 레이어에 배치합니다. To learn about layering patterns, visit the Patterns & Practices site at [http://go.microsoft.com/fwlink/?LinkId=145794](https://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> 레이어에 연결할 수 있지만 레이어 다이어그램의 유효성 검사를 지원하지 않는 특정 유형의 아티팩트가 있습니다. To see whether the artifact supports validation, open **Layer Explorer** to examine the **Supports Validation** property of the artifact link. See [Discover existing dependencies between layers](#Generate).

 익숙하지 않은 애플리케이션을 업데이트하는 경우에도 코드 맵을 만들 수 있습니다. 이러한 다이어그램은 코드를 탐색하는 동안 패턴 및 종속성을 검색하는 데 도움이 됩니다. 솔루션 탐색기를 사용하여 네임스페이스와 클래스를 탐색합니다. 이러한 요소는 기존 레이어에 해당하는 경우가 많습니다. 솔루션 탐색기에서 레이어 다이어그램으로 이러한 코드 아티팩트를 끌어와 레이아웃에 할당합니다. 그런 다음 레이어 다이어그램을 사용하여 코드를 업데이트하고 디자인과 일관성을 유지할 수 있습니다.

 참조

- [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)

- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Discover existing dependencies between layers
 한 레이어와 연결된 아티팩트에 다른 레이어와 연결된 아티팩트에 대한 참조가 있을 때마다 종속성이 존재합니다. 예를 들어 한 레이어의 클래스가 다른 레이어의 클래스를 포함하는 변수를 선언하는 경우입니다. 리버스 엔지니어링하여 기존 종속성을 검색할 수 있습니다.

> [!NOTE]
> 일부 아티팩트 종류의 경우 종속성을 리버스 엔지니어링할 수 없습니다. 예를 들어 텍스트 파일에 연결된 레이어를 소스 또는 대상으로 하는 종속성은 리버스 엔지니어링되지 않습니다. To see which artifacts have dependencies that you can reverse-engineer, right-click one or multiple layers, and then click **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>레이어 간 기존 종속성을 리버스 엔지니어링하려면

- Select one layer or multiple layers, right-click a selected layer, and then click **Generate Dependencies**.

  일반적으로 존재할 수 없는 일부 종속성이 나타나는데, 이러한 종속성을 편집하여 계획된 디자인에 맞출 수 있습니다.

## <a name="EditArchitecture"></a> Edit layers and dependencies to show the intended design
 시스템에 대해 변경할 내용 또는 계획된 아키텍처를 나타내려는 경우 다음 단계에 따라 레이어 다이어그램을 편집합니다. 또한 확장하기 전에 리팩터링을 약간 변경하여 코드의 구조를 향상시키는 것도 고려할 수 있습니다. See [Improving the structure of the code](#Improving).

|**대상**|**Perform these steps**|
|------------|-----------------------------|
|있지 말아야 할 종속성 삭제|Click the dependency, and then press **DELETE**.|
|종속성 방향 변경 또는 제한|Set its **Direction** property.|
|새 종속성 만들기|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> 종속성을 여러 개 그리려면 이 도구를 두 번 클릭합니다. When you are finished, click the **Pointer** tool or press the **ESC** key.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스에 종속될 수 없도록 지정합니다.|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스에 속하지 않도록 지정합니다.|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|레이어와 연결된 아티팩트가 지정된 네임스페이스 중 하나에 속해야 하도록 지정합니다.|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

### <a name="Improving"></a> Improving the structure of the code
 리팩터링을 변경하면 애플리케이션의 동작에 영향을 주지 않지만 나중에 코드를 보다 쉽게 변경하고 확장하는 데 도움이 되도록 개선됩니다. 구조가 적절한 코드의 디자인은 레이어 다이어그램으로 추출하기 쉽습니다.

 예를 들어 각 네임스페이스에 대한 레이어를 코드에 만든 다음 종속성을 리버스 엔지니어링하면 레이어 간에 최소한의 단방향 종속성만 존재하게 됩니다. 클래스 또는 메서드를 레이어로 사용하여 더 자세한 다이어그램을 만드는 경우에도 같은 특성을 갖게 됩니다.

 이러한 경우가 아니면 수명 주기 동안 코드를 변경하기가 더 어려우며 레이어 다이어그램을 사용하여 유효성을 검사하는 것이 적절하지 않게 됩니다.

## <a name="NewAreas"></a> Design new areas of your application
 새 프로젝트의 개발을 시작하거나 새 프로젝트에서 새 영역을 개발하게 될 경우 코드 개발을 시작하기 전에 레이어 및 종속성을 그리면 주요 구성 요소를 식별하는 데 도움이 될 수 있습니다.

- **Show identifiable architectural patterns** in your layer diagrams, if possible. 예를 들어 데스크톱 애플리케이션에 설명하는 레이어 다이어그램에 프레젠테이션, 도메인 논리 및 데이터 스토리지와 같은 레이어를 포함할 수 있습니다. 애플리케이션 내의 단일 기능에 대해 설명하는 레이어 다이어그램에는 모델, 뷰 및 컨트롤러와 같은 레이어가 있을 수 있습니다. For more information about such patterns, see [Patterns & Practices: Application Architecture](https://go.microsoft.com/fwlink/?LinkId=145794).

     비슷한 패턴을 자주 만드는 경우 사용자 지정 도구를 만듭니다. See [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Create a code artifact for each layer** such as a namespace, class, or component. 이렇게 하면 보다 쉽게 코드를 따라가고 코드 아티팩트를 레이어에 연결할 수 있습니다. 각 아티팩트를 만드는 즉시 해당 레이어에 연결합니다.

- **You do not have to link most classes and other artifacts to layers** because they fall within larger artifacts such as namespaces that you have already linked to layers.

- **Create a new diagram for a new feature**. 일반적으로 전체 애플리케이션을 설명하는 하나 이상의 레이어 다이어그램이 있게 됩니다. 애플리케이션 내에서 새 기능을 디자인하는 경우 기존 다이어그램에 추가하거나 기존 다이어그램을 변경하지 않도록 합니다. 대신 코드의 새 부분을 반영하는 고유한 다이어그램을 만듭니다. 새 다이어그램의 레이어에는 새로운 기능에 대한 프레젠테이션, 도메인 논리 및 데이터베이스 레이어가 포함될 수 있습니다.

     애플리케이션을 빌드할 경우 전체 다이어그램과 더 자세한 기능 다이어그램에 대해 코드의 유효성을 검사합니다.

## <a name="EditLayout"></a> Edit the layout for presentation and discussion
 레이어 및 종속성을 식별하거나 팀 멤버와 논의하는 데 도움이 되도록 다음과 같은 방법으로 모양 및 다이어그램의 레이아웃을 편집합니다.

- 레이어의 크기, 모양 및 위치를 변경합니다.

- 레이어의 색과 종속성을 변경합니다.

  - Select one or more layers or dependencies, right-click, and then click **Properties**. In the **Properties** window, edit the **Color** property.

## <a name="Validate"></a> Validate the code against the diagram
 다이어그램을 편집한 경우 언제든지 수동으로 또는 로컬 빌드 또는 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]를 실행할 때마다 자동으로 코드에 대해 유효성을 검사할 수 있습니다.

 참조

- [레이어 다이어그램에 대해 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)

- [Include Layer Validation in the Build Process](#BuildValidation)

## <a name="UpdateCode"></a> Update the code to conform to the new architecture
 일반적으로 업데이트된 레이어 다이어그램에 대해 코드 유효성을 처음 검사하면 오류가 표시됩니다. 이러한 오류에는 다음과 같은 여러 원인이 있을 수 있습니다.

- 잘못된 레이어에 아티팩트가 할당되었습니다. 이 경우 아티팩트를 이동합니다.

- 클래스 등의 아티팩트가 아키텍처에 맞지 않는 방식으로 다른 클래스를 사용합니다. 이 경우 코드를 리팩터링하여 종속성을 제거합니다.

  이러한 오류를 해결하려면 유효성 검사 중 더 이상 오류가 나타나지 않을 때까지 코드를 업데이트합니다. 이것은 일반적으로 반복 프로세스입니다. For more information about these errors, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> 코드를 개발하거나 리팩터링할 경우 레이어 다이어그램에 연결할 새 아티팩트가 있을 수 있습니다. 그러나 예를 들어 기존 네임스페이스를 나타내는 레이어가 있고 새 코드가 해당 네임스페이스에 자료만 더 추가한다면 이러한 아티팩트가 필요하지 않을 수 있습니다.

 개발 과정에서 유효성 검사 중 보고된 충돌 문제 중 일부를 표시하지 않을 수 있습니다. 예를 들어 이미 해결되었거나 특정 시나리오와 관계가 없는 오류를 표시하지 않을 수 있습니다. 오류를 표시하지 않는 경우에는 [!INCLUDE[esprfound](../includes/esprfound-md.md)]에 작업 항목을 기록하는 것이 좋습니다. To perform this task, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Include layer validation in the build process
 나중에 코드를 변경할 때도 레이어 다이어그램을 따르게 하려면 솔루션의 표준 빌드 프로세스에 레이어 유효성 검사를 포함합니다. 다른 팀 멤버가 솔루션을 빌드할 때마다 코드 및 레이어 다이어그램의 종속성 간 차이가 빌드 오류로 보고됩니다. For more information about including layer validation in the build process, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>관련 항목:
 [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)
