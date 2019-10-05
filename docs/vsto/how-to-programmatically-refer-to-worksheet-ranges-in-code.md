---
title: '방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e82b884965c5c7362951c7d94199f90c93fbfc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955963"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조
  비슷한 프로세스를 사용 하 여의 내용을 참조 하는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤 또는 네이티브 Excel 범위 개체입니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤을 사용 하 여
 다음 예제에서는 추가 <xref:Microsoft.Office.Tools.Excel.NamedRange> 워크시트에 다음 범위의 셀에 텍스트를 추가 합니다.

### <a name="to-refer-to-a-namedrange-control"></a>NamedRange 컨트롤에 대 한 참조

1. 에 문자열을 할당 합니다 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 의 속성을 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>사용 하 여 네이티브 Excel 범위
 다음 예제에서는 워크시트에 네이티브 Excel 범위를 추가 하 고 범위에 있는 셀에 텍스트를 추가 합니다.

### <a name="to-refer-to-a-native-range-object"></a>기본 범위 개체를 참조 하려면

1. 문자열을 할당 합니다 <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 범위의 속성입니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>참고자료
- [범위를 사용 하 여 작동 합니다.](../vsto/working-with-ranges.md)
- [방법: 프로그래밍 방식으로 워크시트에서 맞춤법 검사](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [방법: 프로그래밍 방식으로 자동으로 채울 범위 증분 변경 되는 데이터](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [방법: 프로그래밍 방식으로 워크시트 범위에서 텍스트 검색](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
