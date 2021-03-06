---
title: 차트 컨트롤
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b1adf0d961489b09a9dc01775148636e6d2d231a
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267732"
---
# <a name="chart-control"></a>차트 컨트롤
  <xref:Microsoft.Office.Tools.Excel.Chart> 컨트롤은 이벤트를 노출하는 차트 개체입니다. 워크시트에 차트를 추가하면 Visual Studio에서 Microsoft Office Excel 개체 모델을 트래버스하지 않고 직접 프로그래밍할 수 있는 <xref:Microsoft.Office.Tools.Excel.Chart> 개체를 만듭니다.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>컨트롤 만들기  
 추가할 수 있습니다 <xref:Microsoft.Office.Tools.Excel.Chart> 디자인 타임 또는 런타임에 문서 수준 프로젝트에서 Microsoft Office Excel 워크시트에 컨트롤입니다.  
  
 추가할 수 있습니다 <xref:Microsoft.Office.Tools.Excel.Chart> 런타임에 VSTO 추가 기능에서 워크시트에 컨트롤입니다. 자세한 내용은 참조 [하는 방법: 워크시트에 차트 추가 제어](../vsto/how-to-add-chart-controls-to-worksheets.md)합니다.  
  
> [!NOTE]  
>  동적으로 생성된 차트 개체는 워크시트를 닫을 때 워크시트에서 호스트 컨트롤로 유지되지 않습니다. 자세한 내용은 참조 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)합니다.  
  
## <a name="formatting"></a>서식  
 <xref:Microsoft.Office.Interop.Excel.Chart>에 적용할 수 있는 모든 서식은 <xref:Microsoft.Office.Tools.Excel.Chart> 컨트롤에도 적용할 수 있습니다. 여기에는 테두리, 글꼴, 차트 종류, 눈금선, 범례 및 데이터 레이블이 포함됩니다.  
  
## <a name="events"></a>이벤트  
 <xref:Microsoft.Office.Tools.Excel.Chart> 컨트롤에 대해 다음 이벤트를 사용할 수 있습니다.  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>참고자료  
 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)   
 [Word 문서 및 런타임에 VSTO 추가 기능에서 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)   
 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)   
 [방법: 워크시트에 Chart 컨트롤 추가](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  