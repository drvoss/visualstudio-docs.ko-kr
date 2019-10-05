---
title: '방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6e3b66bfd7f3f5d0ef0f4893efeb81c80df5d4ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961877"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정
  Microsoft Office Word 문서에서 선택 항목에 대 한 검색 옵션을 설정 하는 방법은 두 가지 있습니다.

- 개별 속성을 설정 된 <xref:Microsoft.Office.Interop.Word.Find> 개체입니다.

- 인수를 사용 합니다 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 메서드는 <xref:Microsoft.Office.Interop.Word.Find> 개체입니다.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>찾기 개체의 속성을 사용 하 여
 속성을 설정 하는 다음 코드는 <xref:Microsoft.Office.Interop.Word.Find> 현재 선택 영역 내에서 텍스트를 검색할 개체입니다. 검색 조건을 검색할 정방향, 래핑 및 텍스트를 검색 하는 등의 속성은는 <xref:Microsoft.Office.Interop.Word.Find> 개체입니다.

 각 속성을 설정 합니다 <xref:Microsoft.Office.Interop.Word.Find> 개체에 매개 변수로 동일한 속성을 지정 해야 하기 때문에 C# 코드를 작성 하 여 유용 하지 않습니다는 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 메서드. 따라서이 예제에서는 Visual Basic 코드에만 포함합니다.

### <a name="to-set-search-options-using-a-find-object"></a>Find 개체를 사용 하 여 검색 옵션을 설정 하려면

1. 속성을 설정 된 <xref:Microsoft.Office.Interop.Word.Find> 텍스트에 대 한 선택을 통해 앞으로 검색 하는 개체 **오세요**.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Execute 메서드 인수를 사용 합니다.
 다음 코드에서는 합니다 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 메서드는 <xref:Microsoft.Office.Interop.Word.Find> 현재 선택 영역 내에서 텍스트를 검색할 개체입니다. 검색 조건을 검색할 정방향, 래핑 및 텍스트를 검색 하는 등의 매개 변수로 전달 되는 공지를 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 메서드.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Execute 메서드 인수를 사용 하 여 검색 옵션을 설정 하려면

1. 검색 조건 매개 변수로 전달 합니다 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 텍스트에 대 한 선택을 통해 앞으로 검색 하는 방법 **오세요**합니다.

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>참고자료
- [방법: 프로그래밍 방식으로 검색 하 고 문서에서 텍스트 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [방법: 프로그래밍 방식으로 검색 후 선택 영역 복원](../vsto/how-to-programmatically-restore-selections-after-searches.md)
