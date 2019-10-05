---
title: 데이터 및 프로그래밍 방식으로 워크시트 간에 서식 복사
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b90704d6d9fe555920fb042939079bd53884cfbe
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402206"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>방법: 프로그래밍 방식으로 워크시트 간에 데이터 및 서식 복사
  사용 하 여 통합 문서에 있는 모든 시트를 데이터에 하나의 시트를 범위에서 복사할 수는 <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> 메서드. 범위를 지정 및 여부는 데이터, 서식 지정, 또는 둘 다 복사 합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에서는 명명 된 범위를 지정 해야 `rangeData` 워크시트에서 합니다.

## <a name="see-also"></a>참고자료
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에 새 워크시트 추가](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [방법: 프로그래밍 방식으로 선택한 셀이 포함 된 워크시트 행의 서식 변경](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
