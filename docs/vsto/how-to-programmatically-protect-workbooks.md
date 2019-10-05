---
title: '방법: 프로그래밍 방식으로 통합 문서를 보호'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad45097146a7566f2d043fba5e14265c05dc4d7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955913"
---
# <a name="how-to-programmatically-protect-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서를 보호
  사용자 수 없습니다. 추가 하거나 워크시트를 삭제 한도 프로그래밍 방식으로 통합 문서 보호 해제 되도록 Microsoft Office Excel 통합 문서를 보호할 수 있습니다. 필요에 따라 암호를 지정 수를 구조를 (따라서 사용자 시트를 이동할 수 없습니다) 보호와 보호 된 통합 문서의 windows 것인지 여부를 나타냅니다 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 통합 문서를 보호 하는 셀을 편집할 수 없도록 중지 되지 않습니다. 데이터를 보호 하려면 워크시트를 보호 해야 합니다. 자세한 내용은 [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)합니다.

 다음 코드 예제에서는 변수를 사용 하 여 사용자 로부터 얻은 암호를 포함 합니다.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>통합 문서 수준 사용자 지정의 일부인 문서 보호

### <a name="to-protect-a-workbook"></a>통합 문서를 보호 하려면

1. 호출을 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 메서드 통합 문서의 암호를 포함 합니다. 다음 코드 예제를 사용 하려면 실행을 `ThisWorkbook` 시트 클래스에 없는 클래스입니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>통합 문서 보호를 해제 하려면

1. 호출 된 <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> 메서드를 필요한 경우 암호를 전달 합니다. 다음 코드 예제를 사용 하려면 실행을 `ThisWorkbook` 시트 클래스에 없는 클래스입니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>응용 프로그램 수준 추가 기능을 사용 하 여 통합 문서를 보호 합니다.

### <a name="to-protect-a-workbook"></a>통합 문서를 보호 하려면

1. 호출을 <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> 메서드 통합 문서의 암호를 포함 합니다. 이 코드 예제에서는 활성 통합 문서를 사용 합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>통합 문서 보호를 해제 하려면

1. 호출 된 <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> 필요한 경우 암호를 전달 하 여 활성 통합 문서의 메서드. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>참고자료
- [통합 문서를 사용 하 여 작동 합니다.](../vsto/working-with-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 보호](../vsto/how-to-programmatically-protect-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 숨기기](../vsto/how-to-programmatically-hide-worksheets.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
