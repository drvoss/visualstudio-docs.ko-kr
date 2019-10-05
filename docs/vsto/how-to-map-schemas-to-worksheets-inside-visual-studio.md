---
title: '방법: Visual Studio 내에서 워크시트에 스키마 매핑'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80a19924aaf4fa0afe8e809006ada7fada0288f3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428113"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>방법: Visual Studio 내에서 워크시트에 스키마 매핑
  워크시트 Visual Studio에서 열려 있는 동안 워크시트에 XML 스키마를 매핑할 수 있습니다. Visual Studio 외부에서 통합 문서가 열려 있을 때 사용 하는 것과 동일한 Microsoft Office Excel 도구를 사용할 수 있습니다. Office 프로젝트 이전 워크시트에 스키마 매핑 여부 Excel 솔루션을 만든 후 동일한 개체를 만듭니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Excel 솔루션에서 다중 파트 XML 스키마를 사용할 수 없습니다.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Visual Studio에서 Excel 워크시트에 XML 스키마를 매핑하려면

1. Visual Studio 내에서 Excel 통합 문서 또는 서식 파일 프로젝트를 엽니다.

2. 디자이너에 포커스를 이동 하려면 워크시트를 클릭 합니다.

3. 리본에서 **개발자** 탭을 클릭합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발 도구 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)합니다.

4. 에 **XML** 그룹에서 클릭 **원본**합니다.

     합니다 **XML 원본** 창이 열립니다.

5. 에 **XML 원본은** 창에서 클릭 **XML 맵을**합니다.

     합니다 **XML 맵을** 대화 상자가 열립니다.

6. 에 **XML 맵을** 대화 상자, 클릭 **추가**합니다.

7. 스키마 파일을 찾아, 선택 및 클릭 **열려**합니다.

8. **확인**을 클릭합니다.

     스키마에 표시 됩니다는 **XML 원본** 창입니다. 형식화 된 프로젝트에서 <xref:System.Data.DataSet> 스키마에 따라 생성 되 고 <xref:System.Windows.Forms.BindingSource> 만들어집니다.

9. 요소를 끌어 합니다 **XML 원본** 해당 컨트롤을 만들 수 하려는 워크시트에 위치 하는 창입니다.

     Office 프로젝트를 생성 하는 반복 되지 않는 스키마 요소를 끌면를 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 자동으로 바인딩되는 컨트롤을 <xref:System.Windows.Forms.BindingSource>입니다.

     Office 프로젝트를 생성 하는 반복 되는 스키마 요소를 끌면는 <xref:Microsoft.Office.Tools.Excel.ListObject> 데이터 원본에 자동으로 바인딩되지 않은 컨트롤입니다. 자세한 내용은 [에서 데이터 및 XML 스키마 문서 수준 사용자 지정](../vsto/xml-schemas-and-data-in-document-level-customizations.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: Visual Studio 내부의 Word 문서에 스키마 매핑](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [문서 수준 사용자 지정의 XML 스키마 및 데이터](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
