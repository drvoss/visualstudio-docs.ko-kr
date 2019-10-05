---
title: 텍스트 템플릿 사용 방법
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3bbcbb078925f36204c472c27821e6ba94fa4e0
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747545"
---
# <a name="how-to--with-text-templates"></a>텍스트 템플릿 사용 방법
Visual Studio에서 텍스트 템플릿은 모든 종류의 텍스트를 생성 하는 데 도움이 제공합니다. 텍스트 템플릿 텍스트를 생성 하려면 프로젝트 코드의 일부를 생성 하기 위해 디자인 타임 및 런타임에 응용 프로그램의 일부로 사용할 수 있습니다. 이 항목에서는 가장 자주 요약 "어떻게 할까요?" 라는 메시지가 표시 질문입니다.

 이 항목에서는 여러 개의 답변 글머리 기호 뒤에 나오는 제안이 대체 합니다.

 텍스트 템플릿에 대 한 일반 소개를 읽어보세요 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)합니다.

## <a name="how-to-"></a>어떻게...

### <a name="generate-part-of-my-application-code"></a>내 응용 프로그램 코드의 일부를 생성 합니다.
 구성이 있는데 또는 *모델* 파일이 나 데이터베이스입니다. 내 코드의 부분을 하나 이상의 모델에 따라 달라 집니다.

- 텍스트 템플릿에서 코드 파일의 일부를 생성 합니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md) 하 고 [템플릿으로 작성을 시작 하는 가장 좋은 방법은 무엇입니까?](#starting)합니다.

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>템플릿에 데이터를 전달 합니다. 런타임 시 파일을 생성 합니다.
 런타임 시 응용 프로그램 혼합 표준 텍스트 및 데이터를 포함 하는 보고서와 같은 텍스트 파일을 생성 합니다. 수백 개의 쓰기 방지 하려는 `write` 문입니다.

- 런타임 텍스트 템플릿 프로젝트에 추가 합니다. 이 템플릿을 인스턴스화하고 사용 하 여 텍스트를 생성할 수 있는 코드에서 클래스를 만듭니다. 생성자 매개 변수에서 데이터를 전달할 수 있습니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)합니다.

- 런타임에만 사용할 수 있는 템플릿에서 생성 하려는 경우에 표준 텍스트 템플릿을 사용할 수 있습니다. Visual Studio 확장을 작성 하는 경우에 텍스트 템플릿 서비스를 호출할 수 있습니다. 자세한 내용은 [VS 확장에서 텍스트 변환 호출](../modeling/invoking-text-transformation-in-a-vs-extension.md)합니다. 다른 컨텍스트에서 텍스트 템플릿 엔진을 사용할 수 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>을 참조하세요.

     사용 합니다 \<#@parameter#> 이러한 템플릿에 매개 변수를 전달 하는 지시문입니다. 자세한 내용은 [T4 매개 변수 지시문](../modeling/t4-parameter-directive.md)합니다.

### <a name="read-another-project-file-from-a-template"></a>템플릿에서 다른 프로젝트 파일 읽기
 템플릿으로 동일한 Visual Studio 프로젝트에서 파일을 읽기:

- 먼저 `hostSpecific="true"`를 `<#@template#>` 지시문에 삽입합니다.

     코드에서 사용 하 여 `this.Host.ResolvePath(filename)` 파일의 전체 경로를 가져옵니다.

### <a name="invoke-methods-from-a-template"></a>템플릿에서 메서드를 호출 합니다.

메서드가 이미 있는 경우, 예를 들어,.NET 클래스:

- 사용 합니다 \<#@assembly#> 어셈블리를 로드 하 고 사용 하는 지시문 \<#@import#> 네임 스페이스 컨텍스트를 설정 합니다. 자세한 내용은 [T4 Import 지시문](../modeling/t4-import-directive.md)합니다.

   자주 어셈블리의 동일한 집합을 사용 하 고 import 지시문, 경우에 지시문 프로세서를 작성 하는 것이 좋습니다. 각 템플릿에 모델 파일과 어셈블리를 로드 하 고 네임 스페이스 컨텍스트를 설정할 수는 지시문 프로세서를 호출할 수 있습니다. 자세한 내용은 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기](../modeling/creating-custom-t4-text-template-directive-processors.md)합니다.

작성 하는 경우 메서드를 직접.

- 런타임 텍스트 템플릿을 작성 하는 경우에 런타임 텍스트 템플릿에 같은 이름을 가진 partial 클래스 정의 작성 합니다. 이 클래스에 추가 메서드를 추가 합니다.

- 클래스 기능 제어 블록 쓰기 `<#+ ... #>` 를 선언할 수 있는 메서드, 속성 및 개인 클래스에 있습니다. 텍스트 템플릿이 컴파일되면 클래스로 변환 합니다. 표준 제어 블록 `<#...#>` 텍스트는 단일 메서드를 변환 하 고 클래스 기능 블록은 별도 구성원으로 삽입 됩니다. 자세한 내용은 [텍스트 템플릿 제어 블록](../modeling/text-template-control-blocks.md)합니다.

   메서드 정의 클래스 기능 포함 된 텍스트 블록을 포함할 수도 있습니다.

   클래스 기능 수 있는 별도 파일에 배치 하는 것이 좋습니다. `<#@include#>` 하나 이상의 템플릿 파일에 있습니다.

- 별도 어셈블리 (클래스 라이브러리)에 메서드를 작성 하 고 템플릿에서 호출 합니다. 사용 된 `<#@assembly#>` 어셈블리를 로드 하는 지시문 및 `<#@import#>` 네임 스페이스 컨텍스트를 설정 합니다. Note는 어셈블리를 디버깅 하는 동안 다시 작성 하기 위해 해야 중지 하 고 Visual Studio를 다시 시작 합니다. 자세한 내용은 [T4 텍스트 템플릿 지시문](../modeling/t4-text-template-directives.md)합니다.

### <a name="generate-many-files-from-one-model-schema"></a>한 모델 스키마에서 여러 파일 생성
 종종 동일한 XML 또는 데이터베이스 스키마가 모델에서 파일 생성:

- 지시문 프로세서를 작성 하는 것이 좋습니다. 이 옵션을 사용 하면 여러 assembly 문을 바꾸고 import 문을 단일 사용자 지정 지시문을 사용 하 여 각 템플릿에 수 있습니다. 또한 지시문 프로세서를 로드 하 고 모델 파일을 구문 분석할 수 있습니다. 자세한 내용은 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기](../modeling/creating-custom-t4-text-template-directive-processors.md)합니다.

### <a name="generate-files-from-a-complex-model"></a>복잡 한 모델에서 파일을 생성 합니다.

- 도메인 특정 언어 (DSL)을 나타내는 모델을 만드는 것이 좋습니다. 따라서 템플릿에서 작성 하기가 훨씬 쉽습니다 형식 및 모델에 있는 요소의 이름을 반영 하는 속성을 사용 하기 때문입니다. XML 노드를 탐색 하거나 파일을 구문 분석할 필요가 없습니다. 예를 들어:

     `foreach (Book book in this.Library) { ... }`

     자세한 내용은 참조 하세요. [도메인별 언어를 사용 하 여 시작](../modeling/getting-started-with-domain-specific-languages.md) 하 고 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)합니다.

### <a name="get-data-from-visual-studio"></a>Visual Studio에서 데이터 가져오기
 집합에서 Visual Studio에서 제공 하는 서비스를 사용 하는 `hostSpecific` 특성과 부하는 `EnvDTE` 어셈블리입니다. 예를 들어:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>텍스트 템플릿 빌드 프로세스에서 실행

- 자세한 내용은 [빌드 프로세스에서 코드 생성](../modeling/code-generation-in-a-build-process.md)합니다.

## <a name="more-general-questions"></a>보다 일반적인 질문

### <a name="starting"></a> 텍스트 템플릿 작성을 시작 하는 가장 좋은 방법은 무엇입니까?

1. 생성된 된 파일의 특정 예제를 작성 합니다.

2. 텍스트 템플릿에 삽입 하 여 설정 된 `<#@template #>` 지시문, 지시문 및 코드 입력된 파일 또는 모델을 로드 하는 데 필요한 합니다.

3. 식 및 코드 블록을 사용 하 여 파일의 부분을 점진적으로 교체 합니다.

### <a name="what-is-a-model"></a>"모델" 이란 무엇 인가요?

- 템플릿을 통해 읽은 입력 합니다. 파일 또는 데이터베이스의 수 있습니다. XML 또는 Visio 드로잉을 또는 도메인 특정 언어 (DSL) 또는 UML 모델을 수 있습니다 또는 일반 텍스트를 수 있습니다. 여러 파일 분산할 수 있습니다. 일반적으로 둘 이상의 템플릿을 모델 하나를 읽습니다.

     "모델" 이라는 용어는 의미는 생성 된 프로그램 코드 또는 기타 파일 보다 더 직접적으로 비즈니스의 일부 측면을 나타내는 것입니다. 예를 들어, 생성 된 소프트웨어에서 감독 하는 통신 네트워크 계획을 나타낼 수도 있습니다.

### <a name="what-is-the-benefit-of-using-text-templates"></a>텍스트 템플릿을 사용 하 여의 이점은 무엇 인가요?
 일반적으로 있습니다 여러 코드나 다른 파일에서에서 생성 한 모델. 모델은 생성된 된 코드 보다 더 직접적 요구를 나타냅니다. 구현 세부 정보를 생략 하 고 코드를 사용 하지 않고 요구 사항을 기준으로 기록 됩니다. 일반적으로-요구 사항을 변경 하는 경우 보다 쉽고 프로그램 코드의 다른 부분 보다 더 안정적으로 모델을 업데이트할 수 있습니다.

 따라서 코드 생성은 민첩 한 개발 방법 측면에서 매우 유용한 도구입니다.

### <a name="what-best-practices-are-there-for-text-templates"></a>텍스트 템플릿에 대 한 어떤 "모범 사례" 있습니까?

- 자세한 내용은 [T4 텍스트 템플릿 작성에 대 한 지침](../modeling/guidelines-for-writing-t4-text-templates.md)합니다.

### <a name="what-is-t4"></a>"T4" 란?

- 여기에 설명 된 Visual Studio 텍스트 템플릿 기능에 대 한 다른 이름입니다. 이전 버전에서 게시 되지 않은 경우 "텍스트 템플릿 변환"에 대 한 약어
