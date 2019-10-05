---
title: '방법: 프로그래밍 방식으로 통합 문서 열기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: facf3cbeb6635324e74244983fcb33138ad64cfe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812383"
---
# <a name="how-to-programmatically-open-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서 열기
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Microsoft Office Excel에서 컬렉션을 사용 하면 열려 있는 모든 통합 문서를 사용 하 여 작동 하 고 통합 문서를 열 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>기존 통합 문서를 열려면

1. 사용 하 여는 <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> 메서드는 <xref:Microsoft.Office.Interop.Excel.Workbooks> 컬렉션, 통합 문서에 경로 전달 합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에는 다음이 필요합니다.

- 명명 된 통합 문서 `YourWorkbook.xls` 라는 디렉터리에 있어야 `Test` 에서 C 드라이브입니다.

## <a name="see-also"></a>참고자료
- [통합 문서를 사용 하 여 작동 합니다.](../vsto/working-with-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서로 텍스트 파일 열기](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [방법: 프로그래밍 방식으로 새 통합 문서 만들기](../vsto/how-to-programmatically-create-new-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 저장](../vsto/how-to-programmatically-save-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 닫기](../vsto/how-to-programmatically-close-workbooks.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
