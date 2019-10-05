---
title: FxCop 분석기 설치
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b5cb0fa5985cbc923713330289d7f83ed1fd954e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551099"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Visual Studio에서 FxCop 분석기 설치

Microsoft는 레거시 분석에서 가장 중요 한 "FxCop" 규칙을 포함 하는 [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)라는 분석기 집합을 만들었습니다. 이러한 분석기는 코드에서 보안, 성능 및 디자인 문제를 확인 합니다.

이러한 FxCop 분석기를 NuGet 패키지 또는 Visual Studio에 대 한 VSIX 확장으로 설치할 수 있습니다. 각각의 장점과 단점에 대 한 자세한 내용은 [NuGet 패키지 및 VSIX 확장](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>FxCop 분석기를 NuGet 패키지로 설치 하려면

1. 사용자의 Visual Studio 버전에 따라 설치할 [분석기 패키지 버전을 결정](#fxcopanalyzers-package-versions) 합니다.

2. 패키지 [관리자 콘솔](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 또는 [패키지 관리자 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)를 사용 하 여 Visual Studio에서 패키지를 설치 합니다.

   > [!NOTE]
   > 각 분석기 패키지의 nuget.org 페이지에는 **패키지 관리자 콘솔**에 붙여 넣을 수 있는 명령이 표시 됩니다. 텍스트를 클립보드에 복사 하는 편리한 단추도 있습니다.
   >
   > ![패키지 관리자 콘솔 명령을 표시 하는 NuGet.org 페이지](media/nuget-package-manager-command.png)

   분석기 어셈블리는 설치 되며 **참조** > **분석기**아래 **솔루션 탐색기** 에 나타납니다.

   ![솔루션 탐색기의 분석기 노드](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers 패키지 버전

다음 지침에 따라 사용 중인 Visual Studio 버전에 대해 설치할 FxCop 분석기 패키지의 버전을 확인 합니다.

| Visual Studio 버전 | FxCop analyzer 패키지 버전 |
| - | - |
| Visual Studio 2019 (모든 버전)<br />Visual Studio 2017 버전 15.8 이상 | [2.9.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.3) |
| Visual Studio 2017 버전 15.5에서 15.7로 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 버전 15.3에서 15.4로 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 버전 15.0에서 15.2로 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 업데이트 2 및 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 업데이트 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>FxCop 분석기를 VSIX로 설치 하려면

::: moniker range="vs-2017"

Visual Studio 2017 버전 15.5 이상에서는 관리 되는 프로젝트에 대 한 모든 FxCop 분석기를 포함 하는 [Microsoft 코드 분석 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) 확장을 설치할 수 있습니다.

1. Visual Studio에서 **도구** > **확장 및 업데이트**를 선택 합니다.

   **확장명 및 업데이트** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)에서 직접 확장을 다운로드 합니다.

2. 왼쪽 창에서 **온라인** 을 확장 한 다음 **Visual Studio Marketplace**를 선택 합니다.

3. 검색 상자에 "코드 분석"을 입력 하 고 **Microsoft 코드 분석 2017** 확장을 찾습니다.

   ![Microsoft 코드 분석 2017 확장](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft 코드 분석 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) 확장에는 관리 되는 프로젝트에 대 한 모든 FxCop 분석기가 포함 되어 있습니다. 이 확장을 설치 하려면:

1. Visual Studio에서 **확장** > **확장 관리**를 선택 합니다.

   **확장 관리** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)에서 직접 확장을 다운로드 합니다.

2. 왼쪽 창에서 **온라인** 을 확장 한 다음 **Visual Studio Marketplace**를 선택 합니다.

3. 검색 상자에 "코드 분석"을 입력 하 고 **Microsoft 코드 분석 2019** 확장을 찾습니다.

   ![Microsoft 코드 분석 2019 확장](media/manage-extensions-code-analysis.png)

::: moniker-end

4. **다운로드**를 선택 합니다.

   확장이 다운로드 됩니다.

5. **확인** 을 선택 하 여 대화 상자를 닫은 다음 Visual Studio의 모든 인스턴스를 닫아 **VSIX 설치 관리자**를 시작 합니다.

   **VSIX 설치 관리자** 대화 상자가 열립니다.

   ::: moniker range="vs-2017"

   ![Microsoft Code 분석용 VSIX 설치 관리자](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. **수정을** 선택 하 여 설치를 시작 합니다.

   1 ~ 2 분 후 설치가 완료 됩니다.

7. **닫기**를 선택 하 고 Visual Studio를 다시 엽니다.

::: moniker range="vs-2017"

확장이 설치 되어 있는지 여부를 확인 하려면 **도구** > **확장 및 업데이트**를 선택 합니다. **확장 및 업데이트** 대화 상자에서 왼쪽에 있는 **설치** 된 범주를 선택 하 고 이름으로 확장을 검색 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

확장이 설치 되어 있는지 여부를 확인 하려면 확장 확장**관리**를 > 선택 합니다. **확장 관리** 대화 상자에서 왼쪽에 있는 **설치** 된 범주를 선택 하 고 이름으로 확장을 검색 합니다.

::: moniker-end

## <a name="see-also"></a>참고자료

- [Visual Studio의 코드 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [Visual Studio에서 코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)
- [레거시 분석에서 코드 분석기로 마이그레이션](../code-quality/fxcop-analyzers.yml)
