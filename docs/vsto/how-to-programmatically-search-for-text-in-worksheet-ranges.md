---
title: '방법: 프로그래밍 방식으로 워크시트 범위에서 텍스트 검색'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e0befc61b39030bd7144cef10b54e70dc71e33a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419540"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>방법: 프로그래밍 방식으로 워크시트 범위에서 텍스트 검색
  합니다 <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> 메서드는 <xref:Microsoft.Office.Interop.Excel.Range> 개체 범위 내에서 텍스트를 검색할 수 있습니다. 이 텍스트와 같은 워크시트 셀에 표시 될 수 있는 오류 문자열 중 하나 일 수도 있습니다 `#NULL!` 또는 `#VALUE!`합니다. 오류 문자열에 대 한 자세한 내용은 참조 하세요. [오류 값을 셀](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 다음 예제에서는 명명 된 범위 검색 `Fruits` "apples" 단어가 포함 된 셀의 글꼴을 수정 합니다. 이 절차에서는 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 메서드를 사용 하 여 이전에 설정한 검색을 반복 하는 설정을 검색 합니다. 검색할 셀만 지정 하면 및 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 메서드가 나머지를 처리 합니다.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 메서드의 검색 범위의 끝에 도달한 후 검색 범위의 시작 부분에 다시 래핑합니다. 코드는 검색 주위에 배치 되지 무한 루프에 확인 해야 합니다. 예제 프로시저를 사용 하 여 처리 하는 방법을 보여 줍니다는 <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> 속성입니다.

 ![비디오 링크](../vsto/media/playvideo.gif "비디오 링크") 관련된 비디오 데모를 참조 하세요. [어떻게 할까요? Find 메서드를 사용 하 여 Excel 추가 기능에서? ](http://go.microsoft.com/fwlink/?LinkID=130294).

## <a name="to-search-for-text-in-a-worksheet-range"></a>워크시트 범위에서 텍스트를 검색 하려면

1. 전체 범위, 첫 번째는 발견된 범위 및 현재 검색된 범위를 추적 하는 것에 대 한 변수를 선언 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. 다음 검색에 있는 셀을 제외한 모든 매개 변수를 지정 하 여 첫 번째 일치 항목을 검색 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. 계속으로 일치 하는 항목이 검색 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. 첫 번째 검색된 범위를 비교 (`firstFind`)를 **Nothing**합니다. 하는 경우 `firstFind` 에 저장 됩니다 값, 검색된 범위 (`currentFind`).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. 찾은 범위의 주소를 찾은 첫 번째 범위의 주소와 일치 하는 경우에 루프를 종료 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. 검색된 범위의 모양을 설정 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. 다른 검색을 수행 합니다.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   다음 예제에서는 전체 메서드를 보여 줍니다.

## <a name="example"></a>예제
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>참고자료
- [범위를 사용 하 여 작동 합니다.](../vsto/working-with-ranges.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
