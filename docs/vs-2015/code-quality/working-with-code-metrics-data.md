---
title: 코드 메트릭 데이터 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b53e6a5c7ce65675037aac8c6fc4812f895d3b7b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703719"
---
# <a name="working-with-code-metrics-data"></a>코드 메트릭 데이터 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 **코드 메트릭 결과** 코드 메트릭 분석 하 여 생성 되는 데이터 창에 표시 됩니다. 코드 메트릭 데이터 값에 대 한 자세한 내용은 참조 하세요. [코드 메트릭 값](../code-quality/code-metrics-values.md)합니다.  
  
 이 항목에는 다음과 같은 단원이 포함되어 있습니다.  
  
- [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
- [코드 메트릭 결과 표시합니다.](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
- [코드 메트릭 결과 필터링](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
- [추가, 제거 및 데이터 열을 다시 정렬](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
- [클립보드 또는 Excel 데이터를 복사합니다.](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
- [코드 메트릭 결과에 따라 작업 항목 만들기](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
## <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 합니다 **코드 메트릭 결과** 창에는 맨 위 및 열 계산된 결과 표시 하려면 도구 모음입니다.  
  
|Column|설명|  
|------------|-----------------|  
|**계층 구조**|합니다 **계층** 열에는 코드 계층 세무 정보가 있는 트리 뷰를 포함 합니다. 나머지 열은 계산된 된 결과 보여 줍니다. 숨기 거 나 원하는 만큼 결과 열을 정렬할 수 있습니다.|  
|**유지 관리**|합니다 **유지 관리** 열 숫자 결과 함께 아이콘을 포함 합니다. 녹색 아이콘은 상대적으로 높은 유지 관리를 나타냅니다. 노란색 아이콘의 편의성이 보통임을 나타냅니다. 빨간색 아이콘 낮은 유지 관리 하 고는 잠재적인 문제 지점을 나타냅니다. 이러한 색 표시기 AvoidUnmaintainableCode FxCop 규칙에 의해 사용 되는 심각도 범주에 해당 합니다. 이 규칙은 유지 관리 인덱스 사이 있으면 인덱스 10 및 20 및 오류가 아니고 경고 인덱스 20 개 이상 있으면 경고가 10 보다 작으면 오류가 발생 합니다. 유지 관리 인덱스가 3 개 메트릭은의 합성: 순환 복잡성, 줄의 코드와 복잡 한 계산 합니다. 해당 값은 단위로 표시 되지 않습니다.|  
  
## <a name="BKMK_DisplayingCodeMetricsResults"></a> 코드 메트릭 결과 표시합니다.  
 코드 메트릭 결과 창 코드 메트릭 결과 생성 하는 경우 자동으로 표시 됩니다. 또한 언제 든 지 창을 표시할 수 있습니다.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>코드 메트릭 결과 창을 표시 하려면  
  
- 에 **분석** 메뉴에서 클릭 **Windows** 을 클릭 한 다음 **코드 메트릭 결과**합니다.  
  
     \- 또는 -  
  
- 에 **뷰** 메뉴에서 **기타 Windows** 클릭 하 고 **코드 메트릭 결과**합니다.  
  
     코드 메트릭 결과 창에는 결과가 없으면 포함 하는 경우에 표시 됩니다.  
  
#### <a name="to-view-code-metrics-details"></a>코드 메트릭 세부 정보를 보려면  
  
- 코드 메트릭 결과 생성 한 경우에서 트리를 확장 합니다 **계층** 열입니다.  
  
## <a name="BKMK_FilteringCodeMetricsResults"></a> 코드 메트릭 결과 필터링  
 에 표시 되는 결과 필터링 할 수 있습니다 합니다 **코드 메트릭 결과** 창 맨 위에 있는 도구 모음을 사용 합니다. 예를 들어, 다음 65 아래 유지 관리 인덱스가 있는 결과만 표시 하는 것이 좋습니다.  
  
 합니다 **필터** 드롭다운 상자 결과 열의 이름을 포함 합니다. 필터를 정의할 때 들여쓰기 된 목록 맨 아래에 추가 됩니다. 목록에 정의 된 마지막 10 개의 필터를 포함할 수 있습니다.  
  
#### <a name="to-filter-the-code-metrics-results"></a>코드 메트릭 결과 필터링  
  
1. **필터** 목록에서 열 이름을 선택 합니다.  
  
2. **Min**, 표시할 최소 값을 입력 합니다.  
  
3. **최대**에 표시할 최대 값을 입력 합니다.  
  
4. 클릭 합니다 **필터 적용** 단추입니다.  
  
5. 결과 세부 정보를 보려면 계층 구조 트리를 확장 합니다.  
  
## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> 추가, 제거 및 데이터 열을 다시 정렬  
 추가 하거나 제거 결과에서 열을 **코드 메트릭 결과** 창입니다. 또한 원하는 순서로 표시 되도록 결과 열을 다시 정렬할 수 있습니다.  
  
#### <a name="to-remove-a-column"></a>열을 제거 하려면  
  
1. 클릭 합니다 **열 추가/제거** 단추입니다.  
  
     \- 또는 -  
  
     열 머리글을 마우스 오른쪽 단추로 누른 **열 추가/제거**합니다.  
  
2. 에 **열 추가/제거** 대화 상자에서 확인란의 선택을 취소는 열에 대 한 제거 하 고 클릭 하려는 **확인**합니다.  
  
#### <a name="to-add-a-previously-removed-column"></a>이전에 제거한 열을 추가 하려면  
  
1. 클릭 합니다 **열 추가/제거** 단추입니다.  
  
     \- 또는 -  
  
     열 머리글을 마우스 오른쪽 단추로 누른 **열 추가/제거**합니다.  
  
2. 에 **열 추가/제거** 대화 상자를 추가 하 고 클릭 하려는 열의 확인란을 선택 **확인**합니다.  
  
#### <a name="to-rearrange-columns"></a>열 다시 정렬 하려면  
  
1. 클릭 합니다 **열 추가/제거** 단추입니다.  
  
     \- 또는 -  
  
     열 머리글을 마우스 오른쪽 단추로 누른 **열 추가/제거**합니다.  
  
2. 에 **열 추가/제거** 대화 상자에서 이동한 다음 위쪽 화살표 또는 아래쪽 화살표를 클릭 하려는 열을 선택 합니다.  
  
3. 열을 원하는 위치에 위치할 때 클릭 **확인**합니다.  
  
## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> 클립보드 또는 Excel 데이터를 복사합니다.  
 선택 하 고 이름 및 각 데이터 열의 값에 대 한 한 줄을 포함 하는 텍스트 문자열로 코드 메트릭 데이터의 선택된 된 행을 클립보드로 복사할 수 있습니다. 클릭할 수도 있습니다 **Microsoft Excel에서 목록 열기** 코드 메트릭 결과의 모든 Excel 스프레드시트를 내보내려면  
  
## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> 코드 메트릭 결과에 따라 작업 항목 만들기  
 만들 수 있습니다는 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 기반으로 하는 작업 항목 결과 **코드 메트릭 결과** 창입니다. 작업 항목이 만들어지면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 제목에 자동으로 입력 합니다 **제목** 필드 및 코드 메트릭 데이터를 **기록** 탭 합니다.  
  
 작업 항목을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [작업 항목 만들기 &#91;리디렉션&#93;](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b)합니다.  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>결과에 따라 작업 항목을 만들려면  
  
1. 결과 마우스 오른쪽 단추로 클릭 합니다.  
  
2. 가리킨 **작업 항목 만들기**를 만들려는 작업 항목의 종류를 클릭 하 고 (**버그**를 **태스크**등).  
  
3. 모든 필수 필드에 입력 하 여 작업 항목 폼을 완료 합니다.  
  
4. 에 **파일** 메뉴에서 클릭 **모두 저장** 작업 항목을 저장 합니다.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>결과 기반으로 버그를 만들려면  
  
1. 결과 선택를 클릭 합니다.  
  
2. 클릭 합니다 **작업 항목 만들기** 단추입니다.  
  
3. 모든 필수 필드에 입력 하 여 작업 항목 폼을 완료 합니다.  
  
4. 에 **파일** 메뉴에서 클릭 **모두 저장** 작업 항목을 저장 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [복잡성 및 관리 되는 코드 관리 용이성 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [방법: 코드 메트릭 데이터 생성](../code-quality/how-to-generate-code-metrics-data.md)
