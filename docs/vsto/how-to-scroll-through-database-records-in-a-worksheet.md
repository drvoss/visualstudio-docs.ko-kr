---
title: '방법: 워크시트에서 데이터베이스 레코드 스크롤'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e9ffaffdefda98e3e074467fcd4df8cacce91b4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674873"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>방법: 워크시트에서 데이터베이스 레코드 스크롤
  다음 절차에는 최종 사용자가 모든 레코드를 스크롤할 수 있도록 컨트롤을 사용 하 여 Microsoft Office Excel 워크시트에서 데이터베이스 테이블에서 단일 필드를 표시 하려면 디자이너를 사용 하는 방법을 보여 줍니다.  
  
 문서 수준 프로젝트에만 디자이너를 사용할 수 있습니다. 그러나 또한 컨트롤을 추가한 런타임에 프로그래밍 방식으로 데이터에 바인딩합니다. 자세한 내용은 [연습: VSTO 추가 기능 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)합니다.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>워크시트에서 데이터베이스 레코드를 스크롤할 수  
  
1.  Visual Studio에서 Excel 응용 프로그램 프로젝트를 엽니다.  
  
2.  엽니다는 **데이터 원본** 창 데이터베이스에서 데이터 원본을 만듭니다. 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)합니다.  
  
3.  표시 하려는 데이터가 포함 된 테이블을 확장 하 고 특정 열을 선택 합니다.  
  
4.  선택한 컨트롤의 목록을 엽니다 **NamedRange**합니다.  
  
5.  끌어서는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤 데이터를 표시 하려는 셀을 합니다.  
  
6.  **Windows Forms** 탭의 **도구 상자**, 추가 <xref:System.Windows.Forms.BindingNavigator> 워크시트에 컨트롤을 사용 하려는 컨트롤을 설정 합니다. 자세한 내용은 [BindingNavigator 컨트롤 개요 &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)합니다.  
  
## <a name="see-also"></a>참고자료  
 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  