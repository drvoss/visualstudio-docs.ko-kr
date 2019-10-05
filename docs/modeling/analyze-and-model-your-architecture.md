---
title: 아키텍처 분석 및 모델링
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be731ea81baaaa6e9f04b7546bc26ccea0549389
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476626"
---
# <a name="analyze-and-model-your-architecture"></a>아키텍처 분석 및 모델링

앱 모델링 디자인 및 응용 프로그램을 모델링 하는 도구 및 Visual Studio 아키텍처를 사용 하 여 아키텍처 요구 사항을 충족 해야 합니다.

* Visual Studio를 사용하여 코드의 구조, 동작 및 관계를 시각화하는 방식으로 기존 프로그램 코드를 더 쉽게 이해할 수 있습니다.

* 아키텍처 종속성을 존중 필요성에 팀을 교육 합니다.

* 개발 프로세스의 일부로 애플리케이션 수명 주기 전체에 걸쳐 다양한 상세 수준으로 모델을 만듭니다.

참조 [시나리오: 모델링 및 시각화를 사용 하 여 디자인 변경](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)합니다.

## <a name="article-reference"></a>문서 참조

|||
|-|-|
|**코드 시각화**:<br /><br />-코드 맵을 만들어서 코드 구성 및 관계 참조 하세요. 어셈블리, 네임스페이스, 클래스, 메서드 간의 종속성을 시각화합니다.<br />-코드에서 클래스 다이어그램을 만들어서 클래스 구조 및 특정 프로젝트에 대 한 멤버를 참조 하세요.<br />-코드의 유효성을 검사 하는 종속성 다이어그램을 만들어 코드와 해당 디자인 간에 충돌을 확인 합니다.|- [코드 시각화](../modeling/visualize-code.md)<br />- [작업 클래스 및 기타 형식 (클래스 디자이너)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [비디오: Visual Studio 2015 코드 맵으로 코드의 디자인 이해](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [비디오: 실시간에서 아키텍처 종속성 유효성 검사](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**아키텍처 정의**:<br /><br />정의 및 종속성 다이어그램을 만들어서 코드 구성 요소 간의 종속성에 제약 조건을 적용 합니다.|- [비디오: Visual Studio (채널 9)를 사용 하 여 아키텍처 종속성 유효성 검사](https://channel9.msdn.com/Events/Connect/2016/170)|
|**요구 사항 및 의도한 디자인을 사용하여 시스템의 유효성을 검사합니다.**<br /><br />-의도 한 아키텍처를 설명 하는 종속성 다이어그램을 사용 하 여 코드 종속성의 유효성을 검사 하 고 디자인과 충돌할 수 있는 변경을 방지 합니다.|- [비디오: Visual Studio (채널 9)를 사용 하 여 아키텍처 종속성 유효성 검사](https://channel9.msdn.com/Events/Connect/2016/170)|
|**모델 및 다이어그램 사용자 지정**:<br /><br />-자체 도메인 특정 언어를 만듭니다.|- [Modeling SDK for Visual Studio-도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**T4 템플릿을 사용하여 텍스트 생성**:<br /><br />-텍스트 기반 파일을 생성 하려면 템플릿의 내부 제어 논리 및 텍스트 블록이 사용 합니다.<br /> -Visual Studio에 포함 하는 MSBuild 사용 하 여 T4 템플릿 빌드|- [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)|
|**Team Foundation 버전 제어를 사용하여 모델, 다이어그램 및 코드 맵 공유**:<br /><br />-추가 코드 맵, 프로젝트 및 종속성 다이어그램에 Team Foundation 버전 제어와 공유할 수 있습니다 합니다.| |

각 기능을 지 원하는 Visual Studio의 버전을 보려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>모델 형식 및 일반적인 용도

### <a name="code-maps"></a>코드 맵

코드 맵을 통해 코드의 구성과 관계를 확인할 수 있습니다.

**일반적으로 사용 합니다.**

- 구조 및 종속성, 업데이트 방법을 더 잘 이해할 수 있도록 프로그램 코드를 검사하고 제안된 변경의 비용을 예측합니다.

**참고:**

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
- [코드 맵을 사용하여 응용 프로그램 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>종속성 다이어그램

종속성 다이어그램에서는 레이어 또는 명시적 종속성을 사용 하 여 블록 집합으로 응용 프로그램의 구조를 정의할 수 있습니다. 라이브 유효성 검사 코드의 종속성과 종속성 다이어그램에 설명 된 종속 간 충돌을 보여 줍니다.

**일반적으로 사용 합니다.**

- 애플리케이션 수명 동안 다양한 변경을 통해 애플리케이션 구조를 안정화합니다.
- 코드에 대한 변경을 확인하기 전에 의도하지 않은 종속성 충돌을 검색합니다.

**참고:**

- [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)
- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [종속성 다이어그램을 사용하여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>DSL(도메인 특정 언어)

DSL은 특정 용도에 맞게 디자인하는 표기법입니다. Visual Studio에서 일반적으로 그래프입니다.

**일반적으로 사용 합니다.**

- 애플리케이션 파트를 생성하거나 구성합니다. 표기법 및 도구를 개발하려면 작업이 필요합니다. 결과는 UML 사용자 지정보다 도메인에 더 적합할 수 있습니다.
- 대규모 프로젝트에 사용되거나, 여러 프로젝트에서 DSL을 사용하여 DSL 및 도구 개발에 대한 투자 수익을 얻는 제품군에 사용됩니다.

**참고:**

- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>참고자료

- [Visual Studio 2017에서 모델링에 대 한 새로운 기능](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 및 응용 프로그램 수명 주기 관리](/azure/devops/user-guide/devops-alm-overview)
