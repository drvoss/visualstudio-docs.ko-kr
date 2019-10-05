---
title: 코드 분석 사용 또는 사용 안 함
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551038"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>방법: 관리 코드에 대 한 자동 코드 분석 사용 및 사용 안 함

관리 코드 프로젝트의 각 빌드 후에 (정적) 코드 분석을 실행 하도록 구성할 수 있습니다. 각 빌드 구성에 대해 다른 코드 분석 속성을 설정할 수 있습니다 (예: 디버그 및 릴리스).

이 문서는 레거시 분석에만 적용 되 고 [코드 분석기](roslyn-analyzers-overview.md)를 사용 하는 라이브 코드 분석에는 적용 되지 않습니다.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>자동 코드 분석을 사용 하거나 사용 하지 않도록 설정 하려면

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.

1. 프로젝트에 대 한 속성 대화 상자에서 **코드 분석** 탭을 선택 합니다.

   > [!TIP]
   > .NET Core 및 .NET Standard 응용 프로그램과 같은 최신 프로젝트 형식에는 **코드 분석** 탭이 없습니다. 이러한 프로젝트 형식에는 레거시 분석을 사용할 수 없지만 [.NET Compiler Platform 기반 코드 분석기](roslyn-analyzers-overview.md)를 사용 하 여 라이브 코드 분석을 얻을 수 있습니다. 코드 분석기에서 경고를 표시 하지 않으려면이 문서의 끝에 있는 참고를 참조 하세요.

1. **구성** 의 빌드 형식과 **플랫폼**의 대상 플랫폼을 지정 합니다.

1. 자동 코드 분석을 사용 하거나 사용 하지 않도록 설정 하려면 **빌드 시 코드 분석 사용** 확인란을 선택 하거나 선택 취소 합니다.

> [!NOTE]
> **빌드 시 코드 분석 사용** 확인란은 레거시 분석에만 영향을 줍니다. NuGet 패키지로 설치한 경우 항상 빌드에서 실행 되는 [.NET Compiler Platform 기반 코드 분석기](roslyn-analyzers-overview.md)에는 영향을 주지 않습니다. **오류 목록**에서 분석기 오류를 지우려면 메뉴 모음에서 > **코드 분석 실행 및 활성 문제 표시 안 함** 을 선택 하 여 현재 위반을 모두 표시 하지 않을 수 있습니다. 자세한 내용은 [위반 표시 안 함](use-roslyn-analyzers.md#suppress-violations)을 참조 하세요.
