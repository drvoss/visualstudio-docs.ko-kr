---
title: XmlMappedRange 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cde5489d970de02afbce28ab9c60c677ab199c84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810758"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange 컨트롤
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤은 반복 되지 않는 스키마 요소는 Microsoft Office Excel에서 셀에 매핑될 때에 생성 되는 범위입니다. 예를 들어 경우는 `maxOccurs` 스키마 요소의 특성에는 1과 같습니다. Visual Studio에서 XML이 매핑된 범위의 만든 후 Excel 개체 모델을 트래버스 하지 않고 직접 프로그래밍할 수 있습니다. 삭제할 수 있습니다는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 요소 매핑이 제거 되는 경우 Excel 내에서 제어 합니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 ![비디오 링크](../vsto/media/playvideo.gif "비디오 링크") 관련된 비디오 데모를 참조 하세요. [어떻게 할까요? Excel에서 XML 매핑 사용 ](http://go.microsoft.com/fwlink/?LinkID=130288).

## <a name="bind-data-to-the-control"></a>컨트롤에 데이터 바인딩
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤은 단일 데이터 필드 (단순 데이터 바인딩)에 대 한 바인딩을 지원 합니다. <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤 수 복잡 한 데이터 바인딩을 지원 하 고 반복 스키마 요소는 셀에 매핑될 때 자동으로 만들어집니다. 자세한 내용은 [ListObject 컨트롤](../vsto/listobject-control.md)합니다.

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤을 사용 하 여 데이터 원본에 바인딩되는 <xref:System.Windows.Forms.Control.DataBindings%2A> 속성. 경우는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Visual Studio에서 자동으로 매핑된 셀을 데이터에서 데이터 집합을 생성 하 고 해당 데이터 집합에 컨트롤을 바인딩하는 워크시트 셀에 추가 됩니다. 기본 데이터 바인딩 속성을 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>합니다.

 바인딩된 데이터 집합의 데이터가 임의 메커니즘을 통해 업데이트 되는 경우는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤이 변경 내용을 반영 합니다.

## <a name="formatting"></a>서식
 동일한 서식을 적용할 수 있습니다는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 에 적용할 수 있는 컨트롤을 <xref:Microsoft.Office.Interop.Excel.Range>입니다. 여기에는 테두리, 글꼴, 숫자 서식 및 스타일이 포함됩니다.

## <a name="events"></a>이벤트
 에 사용할 수 있는 이벤트는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 제어 됩니다.

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>참고자료
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [방법: 워크시트에 XMLMappedRange 컨트롤 추가](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [방법: Visual Studio 내에서 워크시트에 스키마 매핑](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
