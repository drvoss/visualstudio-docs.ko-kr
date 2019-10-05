---
title: 코드 메트릭 창
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe2c216a9293ddc8c5c1212957c2987924d14e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825073"
---
# <a name="use-the-code-metrics-results-window"></a>코드 메트릭 결과 창 사용

합니다 **코드 메트릭 결과** 코드 메트릭 분석 하 여 생성 되는 데이터 창에 표시 됩니다. 코드 메트릭 데이터 값에 대 한 자세한 내용은 참조 하세요. [메트릭 값을 코드](../code-quality/code-metrics-values.md)합니다.

## <a name="display-code-metrics-results"></a>코드 메트릭 결과 표시 합니다.

합니다 **코드 메트릭 결과** 코드 메트릭 결과 생성할 때 창이 자동으로 표시 됩니다. 또한 언제 든 지 창을 표시할 수 있습니다.

다음 메뉴 시퀀스 중 하나를 사용 하 여 코드 메트릭 결과 창을 표시할 수 있습니다.

- 에 **분석** 메뉴 선택 **Windows** > **코드 메트릭 결과**합니다.

- 에 **뷰** 메뉴 선택 **기타 Windows** > **코드 메트릭 결과**합니다.

합니다 **코드 메트릭 결과** 결과가 포함 된 경우에 창이 열립니다.

### <a name="to-view-code-metrics-details"></a>코드 메트릭 세부 정보를 보려면

코드 메트릭 결과 생성 한 경우에서 트리를 확장 합니다 **계층** 열입니다.

## <a name="filter-code-metrics-results"></a>코드 메트릭 결과 필터링

에 표시 되는 결과 필터링 할 수 있습니다 합니다 **코드 메트릭 결과** 창 맨 위에 있는 도구 모음을 사용 합니다. 예를 들어, 다음 65 아래 유지 관리 인덱스가 있는 결과만 표시 하는 것이 좋습니다.

합니다 **필터** 드롭다운 상자 결과 열의 이름을 포함 합니다. 필터를 정의할 때 들여쓰기 된 목록 맨 아래에 추가 됩니다. 목록에 정의 된 마지막 10 개의 필터를 포함할 수 있습니다.

### <a name="to-filter-the-code-metrics-results"></a>코드 메트릭 결과 필터링

1. **필터** 목록에서 열 이름을 선택 합니다.

2. **Min**, 표시할 최소 값을 입력 합니다.

3. **최대**에 표시할 최대 값을 입력 합니다.

4. 클릭 합니다 **필터 적용** 단추입니다.

5. 결과 세부 정보를 보려면 계층 구조 트리를 확장 합니다.

## <a name="add-remove-and-rearrange-data-columns"></a>추가, 제거 및 데이터 열 다시 정렬

추가 하거나 제거 결과에서 열을 **코드 메트릭 결과** 창입니다. 또한 원하는 순서로 표시 되도록 결과 열을 다시 정렬할 수 있습니다.

### <a name="add-or-remove-a-column"></a>추가 하거나 열 제거

1. 클릭 합니다 **열 추가/제거** 단추, 또는 열 머리글을 마우스 오른쪽 단추로 클릭 한 다음 클릭 **열 추가/제거**합니다.

1. 에 **열 추가/제거** 확인란을 추가 또는 제거 하 고 선택한 열에 대 한 대화 상자, 선택 또는 선택 취소 **확인**합니다.

### <a name="rearrange-columns"></a>열 다시 정렬

1. 클릭 합니다 **열 추가/제거** 단추입니다.

1. 에 **열 추가/제거** 대화 상자에서 이동한 다음 위쪽 화살표 또는 아래쪽 화살표를 선택 하려는 열을 선택 합니다.

1. 열을 원하는 위치에 위치할 때 선택할 **확인**합니다.

## <a name="copy-data-to-the-clipboard-or-excel"></a>클립보드 또는 Excel로 데이터 복사

선택 하 고 이름 및 각 데이터 열의 값에 대 한 한 줄을 포함 하는 텍스트 문자열로 코드 메트릭 데이터의 선택된 된 행을 클립보드로 복사할 수 있습니다. 클릭할 수도 있습니다 **Microsoft Excel에서 선택 내용 열기** Excel 스프레드시트로 내보내려면 모든 코드 메트릭 결과입니다.

## <a name="create-a-work-item-based-on-code-metric-results"></a>코드 메트릭 결과에 따라 작업 항목 만들기

만들 수 있습니다는 [Azure 보드](/azure/devops/boards/index?view=vsts) 기반으로 하는 작업 항목 결과 **코드 메트릭 결과** 창입니다. 작업 항목을 만들 때 Visual Studio에서 제목을 자동으로 입력 합니다 **제목** 필드 및 코드 메트릭 데이터를 **기록** 탭 합니다.

Azure 보드에 대 한 자세한 내용은 작업 항목을 참조 하십시오 [작업 항목](/azure/devops/boards/work-items/index?view=vsts)합니다.

### <a name="to-create-a-work-item-based-on-a-result"></a>결과에 따라 작업 항목을 만들려면

1. 결과 마우스 오른쪽 단추로 클릭 합니다.

2. 가리킨 **작업 항목 만들기**를 만들려는 작업 항목의 종류를 클릭 하 고 (**버그**를 **태스크**등).

3. 모든 필수 필드에 입력 하 여 작업 항목 폼을 완료 합니다.

4. 에 **파일** 메뉴에서 클릭 **모두 저장** 작업 항목을 저장 합니다.

### <a name="to-create-a-bug-based-on-a-result"></a>결과 기반으로 버그를 만들려면

1. 결과 선택를 클릭 합니다.

2. 클릭 합니다 **작업 항목 만들기** 단추입니다.

3. 모든 필수 필드에 입력 하 여 작업 항목 폼을 완료 합니다.

4. 에 **파일** 메뉴에서 클릭 **모두 저장** 작업 항목을 저장 합니다.

## <a name="see-also"></a>참고자료

- [코드 메트릭 값](../code-quality/code-metrics-values.md)
- [방법: 코드 메트릭 데이터 생성](../code-quality/how-to-generate-code-metrics-data.md)