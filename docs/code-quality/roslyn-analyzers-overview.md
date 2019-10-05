---
title: Roslyn 분석기를 사용한 코드 분석
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2d4a9bfca972f9c57688b19bd872b31ee5997f76
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550770"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>.NET Compiler Platform 코드 분석기 개요

.NET Compiler Platform(“Roslyn”) 분석기는 스타일, 품질 및 유지 관리, 디자인 및 기타 문제 해결을 위해 코드를 분석합니다. Visual Studio에는 입력한 C# 또는 Visual Basic 코드를 분석하는 기본 제공 분석기 세트가 포함되어 있습니다. [텍스트 편집기 옵션](../ide/code-styles-and-code-cleanup.md) 페이지 또는 [.editorconfig 파일](../ide/editorconfig-code-style-settings-reference.md)에서 이러한 기본 제공 분석기에 대한 기본 설정을 구성합니다. 추가로 분석기를 Visual Studio 확장이나 NuGet 패키지로 설치할 수 있습니다.

분석기에서 규칙 위반을 발견하면 코드 편집기(위반 코드 아래에 ‘물결선’이 표시됨) 및 **오류 목록** 창에 규칙 위반이 보고됩니다. 

여러 분석기 규칙 또는 *진단*에는 문제를 해결하는 데 적용할 수 있는 하나 이상의 연결된 *코드 수정*이 있습니다. Visual Studio에 기본 제공되는 분석기 진단에는 각각 관련된 코드 수정이 있습니다. 코드 수정은 다른 형식의 [빠른 작업](../ide/quick-actions.md)과 함께 전구 아이콘 메뉴에 표시됩니다. 이러한 코드 수정에 대한 정보는 [일반적인 빠른 작업](../ide/common-quick-actions.md)을 참조하세요.

![분석기 위반 및 빠른 작업 코드 수정](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>.NET Compiler Platform 기반 분석 및 레거시 분석

.NET Compiler Platform(“Roslyn”) 코드 분석기는 관리 코드에 대한 [레거시 분석](../code-quality/code-analysis-for-managed-code-overview.md)을 대체합니다. 대부분의 레거시 분석 규칙은 이미 .NET Compiler Platform 기반 코드 분석기로 다시 작성되었습니다.

레거시 분석 규칙 위반과 마찬가지로 .NET Compiler Platform 기반 코드 분석 위반은 Visual Studio의 오류 목록 창에 표시됩니다. 또한 .NET Compiler Platform 기반 코드 분석 위반은 코드 편집기에서 위반 코드 아래에 *물결선*으로 표시됩니다. 물결선의 색은 규칙의 [심각도 설정](../code-quality/use-roslyn-analyzers.md#rule-severity)에 따라 달라집니다. 다음 스크린샷은 3개의 위반&mdash;빨간색 하나, 녹색 하나 및 회색 하나로 표시됩니다.

![코드 편집기의 물결선](media/diagnostics-severity-colors.png)

.NET Compiler Platform 기반 코드 분석기는 사용하도록 설정된 경우 레거시 분석과 같이 빌드할 때 코드를 분석하지만 입력할 때도 실시간으로 코드를 분석합니다. [전체 솔루션 분석](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)을 사용하도록 설정한 경우 코드 분석기는 편집기에 열려 있지 않은 코드 파일에 대한 디자인 타임 분석도 제공합니다.

> [!TIP]
> 코드 분석기의 빌드 시간 오류 및 경고는 분석기가 NuGet 패키지로 설치된 경우에만 표시됩니다.

.NET Compiler Platform 기반 코드 분석기는 레거시 분석에서 수행하는 동일한 유형의 문제를 보고할 뿐만 아니라 파일 또는 프로젝트에서 위반 횟수의 하나 또는 모두를 쉽게 수정할 수 있도록 합니다. 이러한 작업을 *코드 수정*이라고 합니다. 코드 수정은 IDE별로 다르며 Visual Studio에서 [빠른 작업](../ide/quick-actions.md)으로 구현됩니다. 모든 분석기 진단에는 관련된 코드 수정이 있지 않습니다.

> [!NOTE]
> 다음 UI 옵션은 레거시 분석에만 적용됩니다.
>
> - **분석** > **실행 코드 분석** 메뉴 옵션.
> - 프로젝트 속성 페이지의 **코드 분석** 탭에 있는 **빌드 시 코드 분석 사용** 및 **생성된 코드 결과 표시 안 함** 확인란.

오류 목록 창에서 코드 분석기와 레거시 분석의 위반을 구분하려면 **도구** 열을 확인합니다. 도구 값이 **솔루션 탐색기**의 분석기 어셈블리 중 하나와 일치하는 경우(예: **Microsoft.CodeQuality.Analyzers**) 위반은 코드 분석기에서 발생한 것입니다. 그렇지 않으면 위반은 레거시 분석에서 시작됩니다.

![오류 목록의 도구 열](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> 프로젝트 파일의 **RunCodeAnalysis** msbuild 속성은 레거시 분석에만 적용됩니다. 분석기를 설치하는 경우 프로젝트 파일에서 **RunCodeAnalysis**를 **false**로 설정하면 빌드 후에 레거시 분석이 실행되지 않습니다.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet 패키지와 VSIX 확장 비교

.NET Compiler Platform 분석기는 NuGet 패키지 또는 Visual Studio 확장으로 Visual Studio 전체를 통해 프로젝트별로 설치될 수 있습니다. [분석기 설치](../code-quality/install-roslyn-analyzers.md)의 이러한 두 방법 간에 몇 가지 핵심 동작 차이점이 있습니다.

### <a name="scope"></a>범위

Visual Studio 확장으로 분석기를 설치하는 경우 모든 Visual Studio의 인스턴스에 솔루션 수준에서 적용됩니다. 기본 방법인 NuGet 패키지로 분석기를 설치하는 경우 NuGet 패키지가 설치된 프로젝트에만 적용됩니다. 팀 환경에서 NuGet 패키지로 설치된 분석기는 해당 프로젝트에서 작업하는 *모든 개발자*에 대한 범위에 있습니다.

### <a name="build-errors"></a>빌드 오류

명령줄을 통해 또는 CI(지속적인 통합)의 일부로 빌드 시 규칙을 적용하려면 분석기를 NuGet 패키지로 설치합니다. 분석기 경고 및 오류는 분석기를 확장으로 설치하는 경우 빌드 보고서에 나타나지 않습니다.

다음 스크린샷에서는 분석기 규칙 위반을 포함하는 프로젝트 빌드의 명령줄 빌드 출력을 보여줍니다.

![규칙 위반을 사용하여 MSBuild 출력](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>규칙 심각도

Visual Studio 확장으로 설치된 분석기에서 규칙의 심각도를 설정할 수 없습니다. [규칙 심각도](../code-quality/use-roslyn-analyzers.md#rule-severity)를 구성하려면 분석기를 NuGet 패키지로 설치합니다.

## <a name="categories"></a>범주

다음은 코드를 분석하는 데 도움이 되는 다양한 분석기 유형입니다.

- Microsoft 권장 분석기: [FxCop 분석기](../code-quality/fxcop-analyzers.yml)
- Visual Studio IDE 분석기: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- 타사 분석기: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Visual Studio에서 코드 분석기 설치](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio에서 코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>참고 항목

- [분석기 FAQ](analyzers-faq.md)
- [사용자 고유의 코드 분석기 작성](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
