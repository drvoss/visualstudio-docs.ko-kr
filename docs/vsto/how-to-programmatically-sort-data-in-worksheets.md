---
title: '방법: 프로그래밍 방식으로 워크시트에서 데이터 정렬'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 179cf5fab5a1b2690cb4b46160f7a5c3342fe7bc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914218"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>방법: 프로그래밍 방식으로 워크시트에서 데이터 정렬
  런타임에 워크시트 범위와 목록에 포함된 데이터를 정렬할 수 있습니다. 다음 코드에서는 첫 번째 열의 데이터와 두 번째 열의 데이터를 기준으로 차례로 `Fruits`라는 다중 열 범위를 정렬합니다.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sort-data-in-a-document-level-customization"></a>문서 수준 사용자 지정의 데이터 정렬  
  
### <a name="to-sort-data-in-a-namedrange-control"></a>NamedRange 컨트롤의 데이터를 정렬하려면  
  
1. <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤의 <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> 메서드를 호출합니다. 다음 예제에서는 워크시트에 `Fruits`라는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 필요합니다. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
   에 다음 코드를 넣을 *Sheet1.vb* 또는 *Sheet1.cs* 데이터를 정렬 하는 <xref:Microsoft.Office.Tools.Excel.ListObject> 제어 합니다. 코드에서는 `Sheet1` 워크시트에 `fruitList`라는 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 있다고 가정합니다.  
  
### <a name="to-sort-data-in-a-listobject-control"></a>ListObject 컨트롤의 데이터를 정렬하려면  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> 호스트 컨트롤에서 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 속성의 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 메서드를 호출합니다.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sort-data-in-a-vsto-add-in"></a>VSTO 추가 기능에서 데이터 정렬  
  
### <a name="to-sort-data-in-a-native-range"></a>기본 범위의 데이터를 정렬하려면  
  
1.  네이티브 Excel <xref:Microsoft.Office.Interop.Excel.Range> 컨트롤의 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 메서드를 호출합니다. 다음 예제에서는 워크시트에 `Fruits`라는 네이티브 Excel 컨트롤이 필요합니다.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
### <a name="to-sort-data-in-a-listobject-control"></a>ListObject 컨트롤의 데이터를 정렬하려면  
  
1.  네이티브 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 컨트롤에서 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 속성의 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 메서드를 호출합니다. 다음 예제에서는 활성 워크시트에 `fruitList`라는 네이티브 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 컨트롤이 있다고 가정합니다.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>참고자료  
 [워크시트 작업](../vsto/working-with-worksheets.md)   
 [방법: 프로그래밍 방식으로 자동으로 채울 범위 증분 변경 되는 데이터](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [방법: 프로그래밍 방식으로 코드에서 워크시트 범위 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [방법: 프로그래밍 방식으로 통합 문서에서 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange 컨트롤](../vsto/namedrange-control.md)   
 [ListObject 컨트롤](../vsto/listobject-control.md)   
 [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)  
  
  