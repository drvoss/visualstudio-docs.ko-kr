---
title: EditorConfig와 분석기 비교
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26e48664c40db018df60f2b6d600fab0767a7b72
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062171"
---
# <a name="code-analysis-faq"></a>코드 분석 FAQ

이 페이지에는 Visual Studio의 .NET Compiler Platform 기반 코드 분석에 대 한 몇 가지 질문과 대답을 포함 합니다.

## <a name="code-analysis-versus-editorconfig"></a>코드 분석 및 EditorConfig

**Q**: 코드 스타일을 확인 하는 데 코드 분석 또는 EditorConfig를 사용 해야 하나요?

**A**: 코드 분석 및 EditorConfig 파일은 직접 작동 합니다. [EditorConfig 파일](../ide/editorconfig-code-style-settings-reference.md) 또는 [텍스트 편집기 옵션](../ide/code-styles-and-code-cleanup.md) 페이지에서 코드 스타일을 정의 하는 경우 실제로는 Visual Studio에 기본 제공 되는 코드 분석기를 구성 하는 것입니다. EditorConfig 파일은 [FxCop](configure-fxcop-analyzers.md)분석기와 같은 일부 NuGet analyzer 패키지를 구성 하는 데에도 사용할 수 있습니다.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig와 규칙 집합 비교

**Q**: 규칙 집합이 나 EditorConfig 파일을 사용 하 여 분석기를 구성 해야 하나요?

**A**: 규칙 집합 및 EditorConfig 파일은 공존할 수 있으며 분석기를 구성 하는 데 사용할 수 있습니다. 규칙 [집합](analyzer-rule-sets.md) 을 사용 하 여 규칙을 사용 하거나 사용 하지 않도록 설정 하 고 심각도를 설정할 수 있습니다. EditorConfig 파일은 규칙을 구성 하는 다른 방법을 제공 합니다. FxCop 분석기의 경우 EditorConfig 파일을 사용 하 [여 분석할 코드 형식을 정의할](fxcop-analyzer-options.md)수 있습니다. Visual Studio에 기본 제공 되는 코드 스타일 분석기의 경우 EditorConfig 파일을 사용 하 여 코드 베이스에 대해 [기본 설정 된 코드 스타일을 정의할](../ide/editorconfig-code-style-settings-reference.md) 수 있습니다.

규칙 집합 및 EditorConfig 파일 외에도 일부 분석기는 C# 및 VB 컴파일러에 대 한 [추가 파일로](../ide/build-actions.md#build-action-values) 표시 된 텍스트 파일을 사용 하 여 구성 됩니다.

> [!NOTE]
> EditorConfig 파일은 레거시 분석을 구성 하는 데 사용할 수 없지만 규칙 집합은 사용할 수 있습니다.

## <a name="code-analysis-in-ci-builds"></a>CI 빌드에서 코드 분석

**Q**: CI (연속 통합) 빌드에서 .NET Compiler Platform 기반 코드 분석이 작동 하나요?

**A**: 예. NuGet 패키지에서 설치 된 분석기의 경우 이러한 규칙은 CI 빌드 중을 포함 하 여 [빌드 시에 적용](roslyn-analyzers-overview.md#build-errors)됩니다. CI 빌드에서 사용 되는 분석기는 [규칙 집합과](analyzer-rule-sets.md) [. editorconfig 파일](configure-fxcop-analyzers.md)의 규칙 구성을 모두 고려 합니다. 현재 Visual Studio에 기본 제공 되는 코드 분석기는 NuGet 패키지로 사용할 수 없으므로 이러한 규칙은 CI 빌드에서 시행 되지 않습니다.

## <a name="ide-analyzers-versus-stylecop"></a>IDE 분석기와 StyleCop 비교

**Q**: Visual Studio IDE 코드 분석기와 StyleCop 분석기 간의 차이점은 무엇 인가요?

**A**: Visual Studio IDE에는 코드 스타일 및 품질 문제를 모두 검색 하는 기본 제공 분석기가 포함 되어 있습니다. 이러한 규칙은 도입 된 새로운 언어 기능을 사용 하 고 코드의 유지 관리 효율성을 향상 시키는 데 도움이 됩니다. IDE 분석기는 Visual Studio 릴리스 마다 지속적으로 업데이트 됩니다.

[StyleCop 분석기](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) 는 코드에서 스타일 일관성을 검사 하는 NuGet 패키지로 설치 된 타사 분석기입니다. 일반적으로 StyleCop 규칙을 사용 하 여 코드 베이스에 대 한 특정 스타일을 권장 하지 않고 개인 기본 설정을 지정할 수 있습니다.

## <a name="code-analyzers-versus-legacy-analysis"></a>코드 분석기와 레거시 분석 비교

**Q**: 레거시 분석과 .NET Compiler Platform 기반 코드 분석의 차이점은 무엇 인가요?

**A**: .NET Compiler Platform 기반 코드 분석은 컴파일 중에 소스 코드를 실시간으로 분석 하는 반면 레거시 분석은 빌드가 완료 된 후 이진 파일을 분석 합니다. 자세한 내용은 [.NET Compiler Platform 기반 분석 및 레거시 분석](roslyn-analyzers-overview.md#net-compiler-platform-based-analysis-versus-legacy-analysis) 및 [FxCop 분석기 FAQ](fxcop-analyzers-faq.md)를 참조 하세요.

## <a name="see-also"></a>참고자료

- [분석기 개요](roslyn-analyzers-overview.md)
- [EditorConfig에 대한 .NET 코딩 규칙 설정](../ide/editorconfig-code-style-settings-reference.md)
