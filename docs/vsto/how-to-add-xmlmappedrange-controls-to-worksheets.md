---
title: '방법: 워크시트에 XMLMappedRange 컨트롤 추가'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60f1fe8330e3a40676738c4187273ee60215db6d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427438"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>방법: 워크시트에 XMLMappedRange 컨트롤 추가
  Visual Studio 자동으로 추가 Microsoft Office Excel에서 셀으로 XML 요소를 매핑하는 경우는 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 워크시트에 컨트롤입니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> 합니다 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤에서 사용할 수 없는 합니다 **도구 상자** 또는 **데이터 원본** 창입니다. 만들 수 없습니다는 또한 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 프로그래밍 방식으로 제어 합니다.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>워크시트에 XMLMappedRange 컨트롤을 추가 하려면

1. Visual Studio 디자이너에서 Excel 통합 문서를 엽니다.

2. 컨트롤을 추가 하려는 워크시트를 엽니다.

3. 에 **개발자** 탭을 클릭 **원본**합니다.

    > [!NOTE]
    > 경우는 **개발자** 탭이 리본 메뉴에 표시 되지 않으면, 사용 하도록 설정 해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발 도구 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)합니다.

     합니다 **XML 원본** 작업창 표시 됩니다.

4. 에 **XML 원본은** 작업창에서 **XML 맵을**합니다.

5. 에 **XML 맵을** 대화 상자, 클릭 **추가**합니다.

     합니다 **XML 원본** 대화 상자가 나타납니다.

6. XML 스키마를 선택 합니다 **XML 원본은** 대화 상자를 클릭 **오픈**합니다.

     스키마에 추가 되는 **XML 맵을** 대화 상자.

7. 에 **XML 맵을** 대화 상자, 클릭 **확인**합니다.

8. 요소를 끌어 합니다 **XML 원본** 워크시트의 셀에 작업창 합니다.

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 만들어지고 프로젝트에 추가 합니다.

    > [!NOTE]
    > 부모 요소를 끌면 합니다 **XML 원본은** 작업창을 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 만들어집니다.

## <a name="see-also"></a>참고자료
- [XmlMappedRange 컨트롤](../vsto/xmlmappedrange-control.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [방법: Visual Studio 내에서 워크시트에 스키마 매핑](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
