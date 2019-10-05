---
title: '방법: 문서에서 프로그래밍 방식으로 텍스트 서식 지정'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9f0f64f47317b5712c34d8aca4ea6f64191438e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971136"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>방법: 문서에서 프로그래밍 방식으로 텍스트 서식 지정
  <xref:Microsoft.Office.Interop.Word.Range> 개체를 사용하여 Microsoft Office Word 문서의 텍스트에 서식을 지정할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 다음 예제에서는 문서의 첫 번째 단락을 선택하고 글꼴 크기, 글꼴 이름 및 맞춤을 변경합니다. 그런 다음 범위를 선택하고 메시지 상자를 표시하여 코드의 다음 섹션을 실행하기 전에 일시 중지합니다. 다음 섹션의 실행 취소 메서드를 호출 합니다 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목 (문서 수준 사용자 지정) 또는 <xref:Microsoft.Office.Interop.Word.Document> 3 번 (에 대 한 VSTO 추가 기능) 클래스입니다. 표준 들여쓰기 스타일을 적용하고 메시지 상자를 표시하여 코드를 일시 중지합니다. 그런 다음 코드에서 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> 메서드를 한 번 호출하고 메시지 상자를 표시합니다.

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="to-format-text-using-a-document-level-customization"></a>문서 수준 사용자 지정을 사용하여 텍스트의 서식을 지정하려면

1. 다음 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다. 이 코드를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="to-format-text-using-a-vsto-add-in"></a>VSTO 추가 기능을 사용하여 텍스트의 서식을 지정하려면

1. 다음 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다. 이 코드를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>참고자료
- [방법: 프로그래밍 방식으로 정의 하 고 문서에서 범위를 선택 합니다.](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 Word 문서에 텍스트 삽입](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [방법: 프로그래밍 방식으로 검색 하 고 문서에서 텍스트 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
