---
title: FxCop 분석기 설치
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7690d1c67797c3a13dc22364d93d8af686e4f90c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892053"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Visual Studio에서 FxCop 분석기 설치

Microsoft 분석기, 호출 집합을 만들었습니다 [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), 정적 코드 분석, Roslyn 분석기 변환에서 가장 중요 한 "FxCop" 규칙을 포함 하는 합니다. 이러한 분석기는 보안, 성능 및 다른 디자인 문제에 대 한 코드를 확인합니다.

NuGet 패키지 또는 Visual Studio는 VSIX 확장으로 이러한 FxCop 분석기를 설치할 수 있습니다. 각각의 장단점에 대해 알아보려면, [NuGet 패키지 vs. VSIX 확장](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)합니다.

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>NuGet 패키지로 FxCop 분석기를 설치 하려면

1. [분석기 패키지 버전을 결정](#fxcopanalyzers-package-versions) 를 설치 하려면 Visual Studio의 버전에 따라 합니다.

2. 사용 하 여 Visual Studio에서 패키지를 설치 합니다 [패키지 관리자 콘솔](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 또는 [패키지 관리자 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)합니다.

   > [!NOTE]
   > 각 분석기 패키지는 nuget.org 페이지 붙여 명령을 보여 줍니다.는 **패키지 관리자 콘솔**합니다. 클립보드에 텍스트를 복사 하는 유용한 단추는 짝수입니다.
   >
   > ![패키지 관리자 콘솔 명령을 표시 하는 NuGet.org 페이지](media/nuget-package-manager-command.png)

   분석기 어셈블리를 설치 되어 나타나는 **솔루션 탐색기** 아래에서 **참조가** > **분석기**합니다.

   ![솔루션 탐색기에서 노드 분석기](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers 패키지 버전

Visual Studio의 버전에 대 한 설치 FxCop 분석기 패키지의 버전을 확인 하려면 다음 지침을 따르십시오.

| Visual Studio 버전 | FxCop 분석기 패키지 버전 |
| - | - |
| Visual Studio 2017 버전 15.5 이상 | 예를 들어 2.6.2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2 |
| Visual Studio 2017 버전 15.3을 15.4 | 예를 들어 2.3.0-beta1 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1 |
| Visual Studio 2017 버전 15.0을 15.2 | 예를 들어 2.0.0-beta2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2 |
| Visual Studio 2015 업데이트 2와 3 | 예를 들어 버전 1.2.0-beta2 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2 |
| Visual Studio 2015 업데이트 1 | 예를 들어 1.1.0 버전 https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1합니다. |
| Visual Studio 2015 RTW | 예를 들어 버전 1.0.1, https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1 |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>VSIX로 FxCop 분석기를 설치 하려면

Visual Studio 2017 버전 15.5 이상에 설치할 수 있습니다 합니다 [Microsoft 코드 분석 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) 모든 관리 되는 프로젝트에 대 한 FxCop 분석기를 포함 하는 확장 합니다.

1. Visual Studio에서 선택 **도구가** > **확장 및 업데이트**합니다.

   **확장명 및 업데이트** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는에서 직접 확장을 다운로드 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)합니다.

1. 확장 **Online** 한 다음 선택한 왼쪽된 창의 **Visual Studio Marketplace**합니다.

1. 검색 상자에 "코드 분석"을 입력 하 고 검색할 합니다 **Microsoft 코드 분석 2017** 확장 합니다.

   ![Microsoft 코드 분석 확장](media/extensions-and-updates-code-analysis.png)

1. 선택 **다운로드**합니다.

   확장 다운로드 됩니다.

1. 선택 **확인** 대화 상자를 닫은 다음 시작 하려면 Visual Studio의 모든 인스턴스를 닫습니다에 **VSIX 설치 관리자**합니다.

   합니다 **VSIX 설치 관리자** 대화 상자가 열립니다.

   ![Microsoft 코드 분석을 위한 VSIX 설치 관리자](media/vsix-installer-code-analysis.png)

1. 선택 **수정** 설치를 시작 합니다.

1. 2 분 정도 후 설치를 완료 합니다. 선택 **닫기**합니다.

1. Visual Studio를 다시 엽니다.

확장 설치를 선택 하는지 여부를 확인 하려는 경우 **도구가** > **확장 및 업데이트**합니다. 에 **확장 및 업데이트** 대화 상자에서를 **설치 된** 왼쪽의 범주 이름으로 확장 한 다음 검색 합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 Roslyn 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [Visual Studio에서 Roslyn 분석기 사용](../code-quality/use-roslyn-analyzers.md)
- [FxCop에서 Roslyn 분석기로 마이그레이션](../code-quality/fxcop-analyzers.yml)