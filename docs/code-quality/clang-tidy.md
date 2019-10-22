---
title: Visual Studio에서 Clang 사용
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.workload:
- cplusplus
ms.openlocfilehash: 430d0e271f83332f7163c9c0c947f96756ca7a7d
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72165142"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Visual Studio에서 Clang 사용

코드 분석은 Clang 또는 MSVC 도구 집합을 사용 하는지 여부에 관계 없이 MSBuild 및 CMake 프로젝트 모두에 대해 [Clang](https://clang.llvm.org/extra/clang-tidy/) 를 기본적으로 지원 합니다. Clang 검사는 백그라운드 코드 분석의 일부로 실행 될 수 있으며, 편집기에서 경고 (물결선)로 표시 되 고 오류 목록 표시 됩니다.

Clang를 사용 하려면 Visual Studio 설치 관리자를 통해 "C++ Clang Tools for Windows" 구성 요소를 설치 해야 합니다.

Clang-LLVM/Clang 도구 집합을 사용 하는 경우 MSBuild와 CMake 모두에서 사용할 수 있는 기본 분석 도구입니다. MSVC 도구 집합을 사용 하는 경우이를 함께 실행 하거나 표준 코드 분석 환경을 대체 하도록 구성할 수 있습니다. clang 도구 집합을 사용 하는 경우 Microsoft 코드 분석을 사용할 수 없습니다.

컴파일이 성공적으로 완료 된 후 Clang 실행 됩니다. Clang 결과를 얻기 위해 소스 코드 오류를 해결 해야 할 수도 있습니다.


## <a name="msbuild"></a>MSBuild

프로젝트 속성 창의 **코드 분석** > **일반** 페이지에서 코드 분석 및 빌드의 일부로 Clang을 구성할 수 있습니다. 도구를 구성 하는 옵션은 Clang 하위 메뉴 아래에서 찾을 수 있습니다.

자세한 내용은 [방법: C/C++ 프로젝트에 대 한 코드 분석 속성 설정](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)합니다.

## <a name="cmake"></a>CMake

CMake 프로젝트에서는 `CMakeSettings.json` 내에서 Clang 정리 검사를 구성할 수 있습니다. 열리고 나면 CMake 프로젝트 설정 편집기의 오른쪽 위 모서리에서 "JSON 편집"을 클릭 합니다. 다음 키를 인식할 수 있습니다.

- `enableMicrosoftCodeAnalysis`: Microsoft 코드 분석 사용
- `enableClangTidyCodeAnalysis`: Clang 정리 분석 사용
- `clangTidyChecks`: Clang – 쉼표로 구분 된 목록으로 지정 됩니다. 즉, 사용 또는 사용 안 함으로 확인 합니다.

"사용 안 함" 옵션을 지정 하지 않은 경우 Visual Studio는 사용 된 플랫폼 도구 집합과 일치 하는 분석 도구를 선택 합니다.

## <a name="warning-display"></a>경고 표시

Clang 실행 하면 오류 목록에 경고가 표시 되 고 코드의 관련 섹션 아래에 편집기 내 물결선로 표시 됩니다. 오류 목록에서 "Category" 열을 사용 하 여 Clang 경고를 정렬 하 고 구성할 수 있습니다. **도구** > **옵션**에서 "코드 분석 물결선 사용 안 함" 설정을 전환 하 여 편집기 내 경고를 구성할 수 있습니다.

## <a name="clang-tidy-configuration"></a>Clang 구성

**Clang 검사** 옵션을 통해 Visual Studio 내에서 clang 실행 되는 검사를 구성할 수 있습니다. 이 입력은 도구의 **--검사만** 인수에 제공 됩니다. 추가 구성은 사용자 지정 **. clang** 파일에 포함 될 수 있습니다. 자세한 내용은 [LLVM.org에 대 한 Clang 설명서](https://clang.llvm.org/extra/clang-tidy/) 를 참조 하세요.

## <a name="see-also"></a>관련 항목

- [MSBuild 프로젝트에 대 한 Clang/LLVM 지원](https://aka.ms/cpp/clangmsbuild)
- [CMake 프로젝트에 대 한 Clang/LLVM 지원](https://aka.ms/cpp/clangcmake)
