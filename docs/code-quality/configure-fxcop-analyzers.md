---
title: Editorconfig를 사용 하 여 FxCop 분석기 구성
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 68c175a55c9e60e870a5466a831aaae50d62dced
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293444"
---
# <a name="configure-fxcop-analyzers"></a>FxCop 분석기 구성

[FxCop 분석기](install-fxcop-analyzers.md) 는 레거시 분석에서 가장 중요 한 "FxCop" 규칙으로 구성 되며 .NET Compiler Platform 기반 코드 분석기로 변환 됩니다. 다음 두 가지 방법으로 FxCop 코드 분석기를 구성할 수 있습니다.

- 규칙 [집합](#fxcop-analyzer-rule-sets)을 사용 하 여 규칙을 사용 하거나 사용 하지 않도록 설정 하 고 개별 규칙 위반의 심각도를 설정할 수 있습니다.

- [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 패키지의 버전 2.6.3에서 [editorconfig 파일](#editorconfig-file)을 통해 시작 합니다. [구성 가능한 옵션](fxcop-analyzer-options.md) 을 사용 하면 분석할 코드 베이스의 부분을 구체화할 수 있습니다.

> [!TIP]
> 레거시 분석과 FxCop 분석기 간의 차이점에 대 한 자세한 내용은 [fxcop 분석기 FAQ](fxcop-analyzers-faq.md)를 참조 하십시오.

## <a name="fxcop-analyzer-rule-sets"></a>FxCop 분석기 규칙 집합

FxCop 분석기를 구성 하는 한 가지 방법은 XML *규칙 집합*을 사용 하는 것입니다. 규칙 집합은 대상 문제 및 특정 조건을 식별 하는 코드 분석 규칙의 그룹입니다. 규칙 집합을 사용 하 여 규칙을 사용 하거나 사용 하지 않도록 설정 하 고 개별 규칙 위반의 심각도를 설정할 수 있습니다.

FxCop analyzer NuGet 패키지에는 다음 규칙 범주에 대 한 미리 정의 된 규칙 집합이 포함 되어 있습니다.

- 디자인
- 문서
- 유지 관리
- 명명
- 성능
- 안정성
- 보안
- 사용법

자세한 내용은 [코드 분석기에 대 한 규칙 집합](analyzer-rule-sets.md)을 참조 하세요.

## <a name="editorconfig-file"></a>EditorConfig 파일

[Editorconfig](https://editorconfig.org) 파일에 키-값 쌍을 추가 하 여 FxCop 분석기 규칙을 구성할 수 있습니다. 구성 파일은 [프로젝트에 특정](#per-project-configuration) 하거나 둘 이상의 프로젝트 간에 [공유](#shared-configuration) 될 수 있습니다.

> [!NOTE]
> Editorconfig 파일을 사용 하 여 레거시 FxCop 규칙을 구성할 수 없습니다.

### <a name="per-project-configuration"></a>프로젝트별 구성

특정 프로젝트에 대 한 editorconfig 기반 분석기 구성을 사용 하도록 설정 하려면 프로젝트의 루트 디렉터리에 *editorconfig* 파일을 추가 합니다.

> [!TIP]
> **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고**새 항목** **추가** > 를 선택 하 여 프로젝트에 editorconfig 파일을 추가할 수 있습니다. **새 항목 추가** 창에서 검색 상자에 **editorconfig** 를 입력 합니다. **Editorconfig 파일 (기본)** 템플릿을 선택 하 고 **추가**를 선택 합니다.
>
> ![Visual Studio에서 프로젝트에 editorconfig 항목 추가](media/add-editorconfig-file.png)

현재는 다른 디렉터리 수준 (예: 솔루션 및 프로젝트 수준)에 있는 "파일 결합"을 위한 계층적 지원이 없습니다.

### <a name="shared-configuration"></a>공유 구성

두 개 이상의 프로젝트 간에 FxCop analyzer 구성에 대 한 editorconfig 파일을 공유할 수 있지만 몇 가지 추가 단계가 필요 합니다.

1. 일반 위치에 *editorconfig* 파일을 저장 합니다.

2. 다음 콘텐츠를 사용 하 여 *props* 파일을 만듭니다.

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. *.Csproj* 또는 *.vbproj* 파일에 줄을 추가 하 여 이전 단계에서 만든 *props* 파일을 가져옵니다. 이 줄은 FxCop 분석기 *. props* 파일을 가져오는 모든 줄 앞에 배치 해야 합니다. 예를 들어, props 파일의 이름이 *editorconfig. props*인 경우:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. 프로젝트를 다시 로드 합니다.

> [!NOTE]
> 여기서 설명 하는 EditorConfig 파일의 임의로 공유 된 위치는 FxCop 분석기 구성에만 적용 됩니다. 들여쓰기 및 코드 스타일과 같은 다른 설정의 경우에는 항상 EditorConfig 파일을 프로젝트 폴더 또는 부모 폴더에 배치 해야 합니다.

## <a name="option-scopes"></a>옵션 범위

모든 규칙, 규칙 범주 (예: 이름 지정 또는 디자인) 또는 특정 규칙에 대해 각 옵션을 구성할 수 있습니다.

### <a name="all-rules"></a>모든 규칙

모든 규칙에 대 한 옵션을 구성 하는 구문은 다음과 같습니다.

|구문|예제|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>규칙 범주

규칙 *범주* 에 대 한 옵션을 구성 하는 구문 (예: 이름 지정, 디자인 또는 성능)은 다음과 같습니다.

|구문|예제|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>특정 규칙

특정 규칙에 대 한 옵션을 구성 하는 구문은 다음과 같습니다.

|구문|예제|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>참고자료

- [분석기 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop 분석기](install-fxcop-analyzers.md)
- [EditorConfig에 대 한 .NET 코딩 규칙](../ide/editorconfig-code-style-settings-reference.md)
