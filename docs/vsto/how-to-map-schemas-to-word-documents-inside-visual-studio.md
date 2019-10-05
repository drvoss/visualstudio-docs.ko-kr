---
title: '방법: Visual Studio 내부의 Word 문서에 스키마 매핑'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c6f9ee9a7b636c6c12bfe2f8debcc05911e3b04
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441764"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>방법: Visual Studio 내부의 Word 문서에 스키마 매핑
  **중요 한** Microsoft Word에 대 한이 항목의 설정 정보가 혜택 및 개인 및 United States 및 해당 지역 외부에 위치한는 또는 사용 하는 조직의 사용에 단독으로 표시 되었거나 개발 실행 되는 프로그램, Microsoft Word 2010 년 1 월, Microsoft 구현의 특정 기능을 제거 하는 경우 하기 전에 Microsoft에서 사용이 허가 된 제품에서에서 관련 된 사용자 지정 XML Microsoft Word입니다. Microsoft Word에 대 한이 정보를 읽거나 개인 이나 조직에서는 미국에 있는 Microsoft Word 2010 년 1 월 10 일 후 Microsoft에서 사용이 허가 된 제품에서 실행 되는 프로그램을 개발 하거나를 사용 하는 해당 지역에서 사용 될 수 있습니다. ; 이러한 제품 구매 및 미국 이외의 용도로 사용이 허가 된 날짜 이전에 사용이 허가 된 제품으로 동일한 작동 하지 않습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 문서가 Visual Studio에서 열려 있는 동안 문서에 XML 스키마를 매핑할 수 있습니다. Visual Studio 외부에서 문서가 열려 있을 때 사용 하는 것과 동일한 Microsoft Office Word 도구를 사용할 수 있습니다. Office 프로젝트 이전 문서에 스키마 매핑 여부 Word 솔루션을 만든 후 동일한 개체를 만듭니다.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Visual Studio에서 Word 문서에 XML 스키마를 매핑하려면

1. Visual Studio 내부의 Word 문서 또는 서식 파일 프로젝트를 엽니다.

2. 문서 디자이너에 포커스를 이동 하려면 클릭 합니다.

3. 리본 메뉴에서를 클릭 합니다 **개발자** 탭 합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발 도구 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)합니다.

4. 에 **XML** 그룹에서 클릭 **스키마**합니다.

     합니다 **템플릿 및 추가 기능의** 대화 상자가 열립니다.

5. 클릭 합니다 **XML 스키마** 탭 합니다.

6. 클릭 **스키마 추가**합니다.

     합니다 **스키마 추가** 대화 상자가 열립니다.

7. 스키마 파일을 찾아, 선택 및 클릭 **열려**합니다.

     합니다 **스키마 설정** 대화 상자가 열립니다.

8. 별칭을 할당 하거나 클릭 **확인** 별칭 없이 스키마를 추가 합니다.

9. **확인**을 클릭합니다.

     합니다 **XML 구조** 창이 열립니다.

10. 요소를 끌어 합니다 **XML 구조** 문서에서 해당 컨트롤을 만들 수 하려는 위치에는 창입니다.

## <a name="see-also"></a>참고자료
- [방법: Visual Studio 내에서 워크시트에 스키마 매핑](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [문서 수준 사용자 지정의 XML 스키마 및 데이터](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
