---
title: '방법: 프로그래밍 방식으로 최근에 사용한 파일 목록에서 통합 문서'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3e909ad3e1509689d953e0ad6c6b8346ff97f91
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257591"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>방법: 프로그래밍 방식으로 최근에 사용한 파일 목록에서 통합 문서
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> 속성 최근에 사용한 파일의 Microsoft Office Excel 목록에 표시 되는 모든 파일의 이름이 들어 있는 컬렉션을 반환 합니다. 목록의 길이 유지 하려면 사용자가 선택한 파일의 수에 따라 달라 집니다. 범위에서 결과 표시할 수 있습니다.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>범위 개체의 목록 최근에 사용한 통합 문서에  
  
1.  최근에 사용한 파일 목록을 반복 하 고 이름을 기준으로 셀에 표시 된 <xref:Microsoft.Office.Interop.Excel.Range> 개체입니다.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>참고자료  
 [통합 문서를 사용 하 여 작동 합니다.](../vsto/working-with-workbooks.md)   
 [NamedRange 컨트롤](../vsto/namedrange-control.md)   
 [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)  
  
  