---
title: '방법: 프로그래밍 방식으로 워크시트 숨기기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1fca54350900b2ed252efc324308d1168c6da53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812471"
---
# <a name="how-to-programmatically-hide-worksheets"></a>방법: 프로그래밍 방식으로 워크시트 숨기기
  통합 문서의 모든 워크시트를 표시하거나 숨길 수 있습니다. 워크시트를 숨기려면 워크시트 호스트 항목을 사용하거나 통합 문서의 시트 컬렉션을 통해 워크시트에 액세스합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>워크시트 호스트 항목을 사용 하 여
 문서 수준 사용자 지정에서 디자인 타임에 워크시트가 추가된 경우 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 속성을 사용하여 지정된 워크시트를 숨깁니다.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>워크시트 호스트 항목을 사용하여 워크시트를 숨기려면

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 호스트 항목의 `Sheet1` 속성을 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 열거형 값으로 설정합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션 사용
 다음과 같은 경우 Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션을 통해 워크시트에 액세스합니다.

- VSTO 추가 기능에서 워크시트를 숨기려면 하려고 합니다.

- 숨기려는 워크시트는 문서 수준 사용자 지정에서 런타임에 생성되었습니다.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션을 사용하여 워크시트를 숨기려면

1. 워크시트의 <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> 속성을 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 열거형 값으로 설정합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>참고자료
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
