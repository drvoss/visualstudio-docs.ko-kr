---
title: 증분 방식으로 데이터 범위를 프로그래밍 방식으로 변경 하는 자동 채우기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a514f83d12cd00c4a7792ae0bf2483fdd916897a
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177695"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>방법: 프로그래밍 방식으로 자동으로 채울 범위 증분 변경 되는 데이터
  합니다 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 메서드는 <xref:Microsoft.Office.Interop.Excel.Range> 개체 값을 사용 하 여 워크시트의 범위를 자동으로 채울 수 있습니다. 대부분의 경우는 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 메서드 점진적으로 증가 또는 감소 하는 값 범위에서 저장소를 사용 합니다. 선택적 상수를 제공 하 여 동작을 지정할 수는 <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> 열거형입니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 사용 하는 경우에 두 범위를 지정 해야 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:

- 호출 하는 범위는 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 메서드 채우기의 시작 지점을 지정 하며 초기 값을 포함 합니다.

- 채우기 하려는 범위 매개 변수로 전달 된 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 메서드. 이 대상 범위는 초기 값이 포함 된 범위를 포함 해야 합니다.

    > [!NOTE]
    > 전달할 수 없습니다는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤 대신는 <xref:Microsoft.Office.Interop.Excel.Range>합니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)합니다.

## <a name="example"></a>예제
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>코드 컴파일
 채울 범위의 첫 번째 셀에는 초기 값을 포함 해야 합니다.

 이 예제에서는 세 가지 영역을 채워야 필요 합니다.

- B 열 5 월요일부터 금요일까지 포함 하는 것입니다. 초기 값 입력 **월요일** B1 셀에서입니다.

- C 열 5 개월을 포함 하는 것입니다. 초기 값 입력 **월** C1 셀에서입니다.

- 열 D는 일련의 숫자, 각 행 마다 2 씩 증가 포함 하는 것입니다. 초기 값 입력 **4** D1 셀에서 및 **6** D2 셀에서입니다.

## <a name="see-also"></a>참고자료
- [범위를 사용 하 여 작동 합니다.](../vsto/working-with-ranges.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [방법: 프로그래밍 방식으로 Excel 계산 실행](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
