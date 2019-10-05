---
title: '방법: 프로그래밍 방식으로 워크시트 셀에 문자열을 표시'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9760d019fa80d4ecae63633c38ac9df60932202
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813025"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>방법: 프로그래밍 방식으로 워크시트 셀에 문자열을 표시
  이 예제에서는 프로그래밍 방식으로 셀에 텍스트를 표시 하는 방법에 설명 합니다. 셀에 텍스트를 표시 하려면를 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤 또는 네이티브 Excel 범위 개체입니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤을 사용 하 여
 사용 하 여이 예제는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 라는 컨트롤 `message`합니다. 문서 수준 사용자 지정 디자인 타임에 컨트롤 추가 되어야 합니다. 아니라 시트 클래스에 배치할 해야 다음 코드는 `ThisWorkbook` 클래스입니다.

### <a name="to-display-text-in-a-namedrange-control"></a>NamedRange 컨트롤의 텍스트를 표시 하려면

1. 값을 설정 합니다 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 **Hello World**합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>네이티브 Excel 범위를 사용 합니다.
 다음 코드를 새 범위를 프로그래밍 방식으로 만들고 값을 할당 합니다.

### <a name="to-display-text-in-an-excel-range"></a>Excel 범위에서 텍스트를 표시 하려면

1. 셀 범위를 검색할 **A1** 온 `Sheet1` 값을 설정 하 고 **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>참고자료
- [연습: Windows 폼을 사용 하 여 데이터를 수집 합니다.](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Office 솔루션 문제 해결](../vsto/troubleshooting-office-solutions.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
