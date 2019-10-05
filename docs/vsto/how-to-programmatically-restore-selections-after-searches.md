---
title: '방법: 프로그래밍 방식으로 검색 후 선택 영역 복원'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 672c66fef5d7400601ce69270b5cd4f525b34c7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955704"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>방법: 프로그래밍 방식으로 검색 후 선택 영역 복원
  을 찾아서 문서에서 텍스트를 바꾸는 경우 검색이 완료 되 면 사용자의 원래 선택 항목을 복원 하는 것이 좋습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 샘플 프로시저의 코드에서는 두 개의 활용 <xref:Microsoft.Office.Interop.Word.Range> 개체입니다. 현재 저장소 하나 <xref:Microsoft.Office.Interop.Word.Selection>을 하나 검색 범위를 사용 하려면 전체 문서를 가져오거나 설정 합니다.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>검색 한 후 사용자의 원래 선택 항목을 복원 하려면

1. 만들기는 <xref:Microsoft.Office.Interop.Word.Range> 문서 및 현재 선택 영역에 대 한 개체입니다.

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. 검색 및 바꾸기 작업입니다.

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. 사용자의 원래 선택 항목을 복원 하려면 시작 범위를 선택 합니다.

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   다음 예제에서는 전체 메서드를 보여 줍니다.

## <a name="example"></a>예제
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>참고자료
- [방법: 프로그래밍 방식으로 검색 하 고 문서에서 텍스트 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [방법: 프로그래밍 방식으로 Word에서 검색 옵션 설정](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [방법: 프로그래밍 방식으로 문서에서 찾은 항목 반복](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
