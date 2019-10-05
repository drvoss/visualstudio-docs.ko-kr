---
title: '방법: 프로그래밍 방식으로 워크시트에서 행을 그룹화'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 269ecdb67fe58a5ad2aff6af63ba6ea45647811a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412613"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>방법: 프로그래밍 방식으로 워크시트에서 행을 그룹화
  하나 이상의 전체 행을 그룹화 할 수 있습니다. 워크시트에 그룹을 만들려면 사용을 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤 또는 네이티브 Excel 범위 개체입니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange 컨트롤을 사용 하 여
 추가 하는 경우는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤 디자인 타임에 문서 수준 프로젝트에 프로그래밍 방식으로 그룹을 만들고 컨트롤을 사용할 수 있습니다. 다음 예제는 세 가지 가정 <xref:Microsoft.Office.Tools.Excel.NamedRange> 동일한 워크시트에 컨트롤: `data2001`, `data2002`, 및 `dataAll`합니다. 각 명명 된 범위는 워크시트의 전체 행을 가리킵니다.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>워크시트에 NamedRange 컨트롤의 그룹을 만들려면

1. 세 개의 명명 된 범위를 호출 하 여 그룹을 <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> 각 범위의 메서드. 이 코드는 `ThisWorkbook` 클래스가 아니라 시트 클래스에 배치해야 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > 행 그룹 해제 호출을 <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> 메서드.

## <a name="use-native-excel-ranges"></a>사용 하 여 네이티브 Excel 범위
 코드 라는 세 가지 Excel 범위에 있다고 가정 `data2001`하십시오 `data2002`, 및 `dataAll` 워크시트에.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>워크시트에서 Excel 범위 그룹을 만들려면

1. 세 개의 명명 된 범위를 호출 하 여 그룹을 <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> 각 범위의 메서드. 다음 예제에서는 세 가지는 것으로 가정 <xref:Microsoft.Office.Interop.Excel.Range> 라는 컨트롤 `data2001`, `data2002`, 및 `dataAll` 동일한 워크시트에 합니다. 각 명명 된 범위는 워크시트의 전체 행을 가리킵니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > 행 그룹 해제 호출을 <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> 메서드.

## <a name="see-also"></a>참고자료
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
