---
title: 코드 분석 구성
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe144e8de67264c9d89f6a240ef815afac9a4655
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587565"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>방법: 관리 코드에 대 한 레거시 분석 구성

Visual Studio에서 코드 분석 [규칙 집합](../code-quality/rule-set-reference.md) 목록 중에서 선택 하 여 관리 코드 프로젝트에 적용할 수 있습니다. 기본적으로 **Microsoft 최소 권장 규칙** 규칙 집합 선택 되어 있지만 원하는 경우 설정 하는 다른 규칙을 적용할 수 있습니다. 솔루션의 프로젝트에 하나 이상의 규칙 집합을 적용할 수 있습니다.

> [!NOTE]
> 이 문서는 레거시 분석에 적용 되며 [.NET Compiler Platform 기반 코드 분석기](use-roslyn-analyzers.md)에는 적용 되지 않습니다.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework 프로젝트에 대 한 규칙 집합 구성

1. 엽니다는 **코드 분석** 프로젝트의 속성 페이지의 탭 합니다. 다음 방법 중 하나로 이 작업을 수행할 수 있습니다.

   - **솔루션 탐색기**, 프로젝트를 선택 합니다. 메뉴 모음에서 선택 **분석** > **코드 분석 구성** > **에 대 한 \<projectname >** 합니다.

   - 프로젝트를 마우스 오른쪽 단추로 클릭 **솔루션 탐색기** 선택한 **속성**를 선택한 후는 **코드 분석** 탭 합니다.

2. 에 **구성** 하 고 **플랫폼** 목록에서 빌드 구성과 대상 플랫폼을 선택 합니다.

::: moniker range="vs-2017"

3. 선택한 구성을 사용 하 여 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 **빌드 시 코드 분석 사용**을 선택 합니다. 선택 하 여 코드 분석을 수동으로 실행할 수도 있습니다 **분석** > **코드 분석 실행** > **에서 코드 분석 실행 \<projectname >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. 선택한 구성을 사용 하 여 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 **이진 분석기** 섹션에서 **빌드 시 실행** 을 선택 합니다. 선택 하 여 코드 분석을 수동으로 실행할 수도 있습니다 **분석** > **코드 분석 실행** > **에서 코드 분석 실행 \<projectname >** .

::: moniker-end

4. 생성 된 코드에서 발생 한 경고를 보려면의 선택을 취소 합니다 **생성 된 코드 결과 표시 안 함** 확인란 합니다.

    > [!NOTE]
    > 이 옵션을 선택하더라도 폼 및 템플릿에 오류와 경고가 나타날 경우에는 생성된 코드에서 발생한 코드 분석 오류 및 경고가 계속 표시됩니다. 양식이 나 템플릿에 대 한 소스 코드를 보고 유지 관리할 수 있으며 해당 코드를 덮어쓰지 않습니다.

::: moniker range="vs-2017"

5. 에 **이 규칙 집합 실행** 목록에서 다음 중 하나를 수행 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

5. **활성 규칙** 목록에서 다음 중 하나를 수행 합니다.

::: moniker-end

   - 사용 하려는 규칙 집합을 선택 합니다.

   - **\<찾아보기 >** 를 선택 하 여 목록에 없는 기존 사용자 지정 규칙 집합을 찾습니다.

   - 정의 된 [사용자 지정 규칙 집합](../code-quality/how-to-create-a-custom-rule-set.md)합니다.

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>솔루션의 여러 프로젝트에 대 한 규칙 집합 지정

기본적으로 솔루션의 관리 되는 모든 프로젝트는 할당 된 *Microsoft 최소 권장 규칙* 코드 분석 규칙 집합입니다. 솔루션의 프로젝트에 할당 되는 규칙 집합을 변경할 수 있습니다 합니다 **속성** 솔루션에 대 한 대화 상자.

1. Visual Studio에서 솔루션을 엽니다.

2. 에 **분석** 메뉴에서 **솔루션에 대 한 코드 분석 구성**합니다.

3. 필요한 경우 확장 **공용 속성**를 선택한 후 **코드 분석 설정**합니다.

4. 하나 이상의 프로젝트에 대해 설정 하는 규칙을 지정할 수 있습니다.

    - 개별 프로젝트에 대해 설정 하는 규칙을 지정 하려면 프로젝트 이름을 선택 합니다.

    - 여러 프로젝트를 설정 하는 규칙을 지정 하려면 누른 **Ctrl** 프로젝트 이름을 선택 합니다.

    - 솔루션의 모든 프로젝트를 지정 하려면 누른 **Shift** 프로젝트 목록에서 클릭 합니다.

5. 선택 된 **규칙 집합** 규칙의 이름을 적용 하려는 프로젝트의 필드 및 선택 설정 합니다.

## <a name="see-also"></a>참조

- [코드 분석 규칙 집합 참조](../code-quality/rule-set-reference.md)
