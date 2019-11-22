---
title: Analyze and model your architecture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49c421af5aa6c91535b05f0beca88099ea7a2eaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297946"
---
# <a name="analyze-and-model-your-architecture"></a>아키텍처 분석 및 모델링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 아키텍처 및 모델링 도구를 사용하여 앱을 디자인 및 모델링하는 방식으로 앱이 사용자 요구 사항을 충족하는지 확인합니다. Visual Studio를 사용하여 코드의 구조, 동작 및 관계를 시각화하는 방식으로 기존 프로그램 코드를 더 쉽게 이해할 수 있습니다.

 개발 프로세스의 일부로 애플리케이션 수명 주기 전체에 걸쳐 다양한 상세 수준으로 모델을 만듭니다. 모델 요소를 Team Foundation Server 작업 항목 및 개발 계획에 연결하여 요구 사항, 작업, 테스트 사례, 버그 및 모델과 연결된 기타 작업을 추적합니다. See [Scenario: Change your design using visualization and modeling](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 각 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="to"></a>대상

|||
|-|-|
|**코드 시각화**:<br /><br /> -   See the code's organization and relationships by creating code maps. 어셈블리, 네임스페이스, 클래스, 메서드 간의 종속성을 시각화합니다.<br />-   See the class structure and members for a specific project by creating class diagrams from code.<br />-   Find conflicts between your code and its design by creating layer diagrams to validate code.<br /><br /> **참고**: 이 Visual Studio 릴리스에서는 *종속성 그래프* 대신에 *코드 맵*이 사용됩니다. 단독으로 사용될 경우 *그래프* 는 일반적으로 방향성 그래프 또는 DGML 다이어그램(또는 문서)을 나타냅니다. 코드 맵은 DGML 다이어그램의 특수화된 형식입니다.|-   [코드 시각화](../modeling/visualize-code.md)<br />-   [Working with Classes and Other Types (Class Designer)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Understand your code dependencies through visualization (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Video: Visualize the impact of a change (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252068)|
|**사용자 요구 사항 설명 및 전달**:<br /><br /> -   Clarify user stories, business rules, and other requirements and help ensure their consistency by drawing UML diagrams such as use case, activity, and class diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model user requirements](../modeling/model-user-requirements.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)|
|**아키텍처 정의**:<br /><br /> -   Model the large-scale structure of your software system and the design patterns by drawing UML component, class, and sequence diagrams.<br />-   Define and enforce constraints on dependencies between the components of your code by creating layer diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model your app's architecture](../modeling/model-your-app-s-architecture.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**요구 사항 및 의도한 디자인을 사용하여 시스템의 유효성을 검사합니다.**<br /><br /> -   Define acceptance tests or system tests based on the requirements models. 이렇게 하면 테스트와 사용자 요구 사항 간에 강력한 관계가 생성되고 요구 사항이 변경될 때 시스템을 더 쉽게 업데이트할 수 있습니다.<br />-   Validate code dependencies with layer diagrams that describe the intended architecture and prevent changes that might conflict with the design.|-   [Validate your system during development](../modeling/validate-your-system-during-development.md)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Team Foundation 버전 제어를 사용하여 모델, 다이어그램 및 코드 맵 공유**:<br /><br /> -   Put code maps, modeling projects, UML diagrams, and layer diagrams under Team Foundation version control so you can share them.|Team Foundation 버전 제어에서 이들 항목을 사용하는 여러 사용자가 있으면 지침에 따라 버전 제어 문제를 방지합니다.<br /><br /> -   [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**UML 및 도메인 특정 언어에서 애플리케이션 파트 생성 또는 구성**:<br /><br /> -   Make your design more responsive to requirements changes and easily variable across a product line.|-   [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md)|
|**모델 및 다이어그램 사용자 지정**:<br /><br /> -   Adapt models to how your project uses them by defining additional properties for UML elements, validation constraints to make sure that your models conform to your business rules, and additional menu commands and toolbox items.<br />-   Create your own domain-specific languages.|-   [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**T4 템플릿을 사용하여 텍스트 생성**:<br /><br /> -   Use text blocks and control logic inside templates to generate text-based files.|-   [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>모델 형식 및 해당 용도

|**모델 형식 및 일반적인 용도**|
|-------------------------------------|
|**코드 맵**<br /><br /> 코드 맵을 통해 코드의 구성과 관계를 확인할 수 있습니다.<br /><br /> 일반적인 용도:<br /><br /> -   Examine program code so you can better understand its structure and its dependencies, how to update it, and estimate the cost of proposed changes.<br /><br /> 참조<br /><br /> -   [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Layer diagram**<br /><br /> 레이어 다이어그램을 통해 애플리케이션 구조를 명시적 종속성이 포함된 레이어 또는 블록 집합으로 정의할 수 있습니다. 유효성 검사를 실행하여 코드의 종속성과 레이어 다이어그램에 설명된 종속 간 충돌을 검색할 수 있습니다.<br /><br /> 일반적인 용도:<br /><br /> -   Stabilize the structure of the application through numerous changes over its life.<br />-   Discover unintentional dependency conflicts before checking in changes to the code.<br /><br /> 참조<br /><br /> -   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|
|**UML model**<br /><br /> UML 모델에는 클래스, 구성 요소, 사용 사례, 동작 및 시퀀스 다이어그램을 비롯한 여러 뷰가 포함됩니다. 애플리케이션 도메인에 맞게 UML을 사용자 지정할 수 있습니다. 예를 들어 태그, 추가 정보 및 제약 조건을 모델 요소에 연결할 수 있습니다. 모델에서 작동하는 도구를 정의할 수도 있습니다. See [Create models for your app](../modeling/create-models-for-your-app.md).<br /><br /> 일반적인 용도:<br /><br /> -   Describe requirements and design. 애플리케이션 개발에 UML을 빠르게 적용할 수 있습니다. See [Use models in your development process](../modeling/use-models-in-your-development-process.md).<br />-   Generate or configure tests or parts of an application. 표기법을 사용자 지정하고 생성 템플릿 또는 구성 가능한 애플리케이션을 개발하려면 몇 가지 작업이 필요합니다. See [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md).<br />-   For general description and for code generation or configuration in smaller projects.|
|**DSL(도메인 특정 언어)**<br /><br /> DSL은 특정 용도에 맞게 디자인하는 표기법입니다. Visual Studio에서는 일반적으로 그래픽으로 표시됩니다.<br /><br /> 일반적인 용도:<br /><br /> -   Generate or configure parts of the application. 표기법 및 도구를 개발하려면 작업이 필요합니다. 결과는 UML 사용자 지정보다 도메인에 더 적합할 수 있습니다.<br />-   For large projects or in product lines where the investment in developing the DSL and its tools is returned by its use in more than one project.<br /><br /> 참조<br /><br /> -   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>추가 정보는 어디서 확인할 수 있나요?

|||
|-|-|
|**포럼**|-   [Visual Studio 시각화 및 모델링 도구](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio 시각화 및 모델링 SDK(DSL 도구)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>관련 항목:

- [What's new for modeling in Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 및 애플리케이션 수명 주기 관리](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
