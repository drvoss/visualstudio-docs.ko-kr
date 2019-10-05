---
title: FxCop 분석기 규칙 집합
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 313b578743fd734da3354989a8cee16022779242
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974700"
---
# <a name="rule-sets-for-analyzer-packages"></a>분석기 패키지에 대한 규칙 집합

미리 정의 된 규칙 집합은 일부 NuGet 분석기 패키지에 포함 됩니다. 예를 들어 [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet analyzer 패키지 (버전 2.6.2 critical부터 시작)에 포함 된 규칙 집합은 보안, 이름 지정, 성능 등의 범주에 따라 규칙을 사용 하거나 사용 하지 않도록 설정 합니다. 규칙 집합을 사용 하면 특정 규칙 범주와 관련 된 규칙 위반만 쉽게 확인할 수 있습니다.

규칙 집합은 대상 문제 및 특정 조건을 식별 하는 코드 분석 규칙의 그룹입니다. 규칙 집합을 사용 하 여 규칙을 사용 하거나 사용 하지 않도록 설정 하 고 개별 규칙 위반의 심각도를 설정할 수 있습니다. FxCop analyzer NuGet 패키지에는 다음 규칙 범주에 대 한 미리 정의 된 규칙 집합이 포함 되어 있습니다.

- 디자인
- 문서
- 유지 관리
- 명명
- 성능
- 안정성
- 보안
- 사용법

레거시 "FxCop" 분석에서 .NET Compiler Platform 기반 코드 분석으로 마이그레이션하는 경우 이러한 규칙 집합을 사용 하 여 [이전에 사용한](rule-set-reference.md)것과 비슷한 규칙 구성을 계속 사용할 수 있습니다.

## <a name="use-analyzer-package-rule-sets"></a>분석기 패키지 규칙 집합 사용

[NuGet 분석기 패키지를 설치한](install-roslyn-analyzers.md)후 *에는 해당 규칙 집합 디렉터리에서* 미리 정의 된 규칙 집합을 찾습니다. 예를 들어 `Microsoft.CodeAnalysis.FxCopAnalyzers` 분석기 패키지를 참조 한 경우 *% USERPROFILE% \\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers @ no__t-4 @ no__t-5version @ no__t-6\rulesets*에서 해당 *규칙 집합* 디렉터리를 찾을 수 있습니다. 여기에서 하나 이상의 규칙 집합을 복사 하 고 Visual Studio 프로젝트를 포함 하는 디렉터리 또는 **솔루션 탐색기**에 직접 붙여 넣습니다.

[미리 정의 된 규칙 집합](how-to-create-a-custom-rule-set.md) 을 기본 설정으로 사용자 지정할 수도 있습니다. 예를 들어 위반이 **오류 목록**에 오류 또는 경고로 표시 되도록 하나 이상의 규칙의 심각도를 변경할 수 있습니다.

## <a name="set-the-active-rule-set"></a>활성 규칙 집합 설정

활성 규칙 집합을 설정 하는 프로세스는 .NET Core/.NET Standard 프로젝트 또는 .NET Framework 프로젝트가 있는지 여부에 따라 약간 다릅니다.

### <a name="net-core"></a>.NET Core

규칙을 .NET Core 또는 .NET Standard 프로젝트의 분석에 대해 활성 규칙 집합으로 설정 하려면 **CodeAnalysisRuleSet** 속성을 프로젝트 파일에 수동으로 추가 합니다. 예를 들어 다음 코드 조각은 활성 규칙 집합으로 `HelloWorld.ruleset`을 설정 합니다.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

규칙을 .NET Framework 프로젝트의 분석을 위한 활성 규칙 집합으로 설정 하려면 다음을 수행 합니다.

- **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.

- 프로젝트 속성 페이지에서 **코드 분석** 탭을 선택 합니다.

::: moniker range="vs-2017"

- **이 규칙 집합 실행**에서 **찾아보기**를 선택한 다음 프로젝트 디렉터리에 복사한 원하는 규칙 집합을 선택 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

- **활성 규칙**에서 **찾아보기**를 선택한 다음 프로젝트 디렉터리에 복사한 원하는 규칙 집합을 선택 합니다.

::: moniker-end

   이제 선택한 규칙 집합에서 사용 하도록 설정 된 규칙에 대 한 규칙 위반만 표시 됩니다.

## <a name="available-rule-sets"></a>사용 가능한 규칙 집합

미리 정의 된 분석기 규칙 집합에는 패키지의 모든 규칙에 영향을 주는 세 가지 규칙 집합, 즉 모두 사용 하지 않도록 설정 하 고 각 규칙의 기본 심각도 및 사용 설정을 준수 하는 규칙 집합이 포함 됩니다.

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

또한 패키지의 각 규칙 범주에 대 한 두 가지 규칙 집합 (예: 성능 또는 보안)이 있습니다. 한 규칙 집합은 범주에 대 한 모든 규칙을 사용 하도록 설정 하 고, 하나의 규칙 집합은 범주의 각 규칙에 대 한 기본 심각도 및 사용 설정을 적용 합니다.

[FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet analyzer 패키지에는 다음 범주에 대 한 규칙 집합이 포함 되어 있습니다.

- 디자인
- 문서
- 유지 관리
- 명명
- 성능
- 안정성
- 보안
- 사용법

## <a name="see-also"></a>참조

- [분석기 FAQ](analyzers-faq.md)
- [.NET Compiler Platform 분석기 개요](roslyn-analyzers-overview.md)
- [분석기 설치](install-roslyn-analyzers.md)
- [분석기 구성](use-roslyn-analyzers.md)
- [규칙 집합을 사용 하 여 코드 분석 규칙 그룹화](using-rule-sets-to-group-code-analysis-rules.md)
