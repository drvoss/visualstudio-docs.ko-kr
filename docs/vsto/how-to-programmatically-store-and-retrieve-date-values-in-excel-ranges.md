---
title: 저장 및 프로그래밍 방식으로 Excel 범위에서 날짜 값 검색
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d855ffd91ccdc07a2d69401d7a8611175cc60941
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328918"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>방법: 프로그래밍 방식으로 저장 하 고 Excel 범위에서 날짜 값 검색
  저장할 수 있으며 값을 검색 한 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤 또는 네이티브 Excel 범위 개체입니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Visual Studio에서 Office 개발 도구를 사용 하 여 범위에서 1900 년 1 월 1 일 이후인 속하는 날짜 값을 저장 하는 경우 OLE Automation (OA) 형식으로 저장 됩니다. 사용 해야는 <xref:System.DateTime.FromOADate%2A> OLE Automation (OA) 날짜 값을 검색 하는 방법입니다. 1900 년 1 월 1 일 보다 이전 날짜인 경우 문자열로 저장 됩니다.

> [!NOTE]
> Excel 날짜는 1900의 첫 2 개월에 대 한 OLE 자동화 날짜에서 다릅니다. 도 차이가 발생 하는 경우는 **1904 날짜 체계** 옵션을 선택 합니다. 아래 코드 예제에서는 이러한 차이점을 다루지 않습니다.

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤을 사용 하 여

- 이 예제에서는 문서 수준 사용자 지정입니다. 아니라 시트 클래스에 배치할 해야 다음 코드는 `ThisWorkbook` 클래스입니다.

### <a name="to-store-a-date-value-in-a-named-range"></a>명명된 된 범위에서 날짜 값을 저장 하려면

1. 만들기는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 셀에서 컨트롤 **A1**합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. 오늘 날짜에 대 한 값으로 설정 `NamedRange1`합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>명명된 된 범위에서 날짜 값을 검색 하려면

1. 날짜 값을 검색 `NamedRange1`합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>사용 하 여 네이티브 Excel 범위

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>네이티브 Excel 범위 개체의 날짜 값을 저장 하려면

1. 만들기는 <xref:Microsoft.Office.Interop.Excel.Range> 셀을 나타내는 **A1**합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. 오늘 날짜에 대 한 값으로 설정 `rng`합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>네이티브 Excel 범위 개체에서 날짜 값을 검색 하려면

1. 날짜 값을 검색 `rng`합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>참고자료
- [범위를 사용 하 여 작동 합니다.](../vsto/working-with-ranges.md)
- [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
