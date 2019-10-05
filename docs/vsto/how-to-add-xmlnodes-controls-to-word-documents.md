---
title: '방법: Word 문서에 XMLNodes 컨트롤 추가'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b54a341cd9dd949f892537ee384afb4984aecc02
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419687"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>방법: Word 문서에 XMLNodes 컨트롤 추가
  **중요 한** Microsoft Word에 대 한이 항목의 설정 정보가 혜택 및 개인 및 United States 및 해당 지역 외부에 위치한는 또는 사용 하는 조직의 사용에 단독으로 표시 되었거나 개발 실행 되는 프로그램, Microsoft Word 2010 년 1 월, Microsoft 구현의 특정 기능을 제거 하는 경우 하기 전에 Microsoft에서 사용이 허가 된 제품에서에서 관련 된 사용자 지정 XML Microsoft Word입니다. Microsoft Word에 대 한이 정보를 읽거나 개인 이나 조직에서는 미국에 있는 Microsoft Word 2010 년 1 월 10 일 후 Microsoft에서 사용이 허가 된 제품에서 실행 되는 프로그램을 개발 하거나를 사용 하는 해당 지역에서 사용 될 수 있습니다. ; 이러한 제품 구매 및 미국 이외의 용도로 사용이 허가 된 날짜 이전에 사용이 허가 된 제품으로 동일한 작동 하지 않습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Visual Studio 자동으로 추가 Microsoft Office Word 문서에는 반복 되는 XML 스키마 요소를 매핑하는 경우는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤을 문서로 합니다.

 XML 스키마 요소 반복 되지 않는 매핑에 대 한 자세한 내용은 참조 하세요. [방법: Word 문서에 XMLNode 컨트롤 추가](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)합니다.

> [!NOTE]
> 합니다 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤에서 지원 하지 않는 합니다 **도구 상자** 또는 **데이터 원본** 창 또는 프로그래밍 방식으로 작성할 수 있습니다.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>문서에 XMLNodes 컨트롤을 추가 하려면

1. 리본 메뉴에서 Visual Studio 디자이너에서 문서에서를 클릭 합니다 **개발자** 탭 합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발 도구 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)합니다.

2. 에 **XML** 그룹에서 클릭 **스키마**합니다.

     합니다 **템플릿 및 추가 기능의** 대화 상자가 열립니다.

3. 클릭 합니다 **XML 스키마** 탭 합니다.

4. 클릭 **스키마 추가**합니다.

     합니다 **스키마 추가** 대화 상자가 열립니다.

5. 반복 스키마 요소 및 클릭을 포함 하는 XML 스키마 선택 **열려**합니다.

     합니다 **스키마 설정** 대화 상자가 나타납니다.

6. 별칭을 할당 하거나 클릭 **확인** 별칭 없이 스키마를 추가 합니다.

     스키마에 추가 되는 **스키마 추가** 대화 상자.

7. 에 **스키마 추가** 대화 상자, 클릭 **확인**합니다.

     합니다 **XML 구조** 작업창이 열립니다.

8. 반복 되는 스키마 요소를 클릭 합니다 **XML 구조** 작업창은 문서에 추가 합니다.

     <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤이 만들어지고 프로젝트에 추가 합니다.

## <a name="see-also"></a>참고자료
- [XMLNodes 컨트롤](../vsto/xmlnodes-control.md)
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
