---
title: '방법: 프로그래밍 방식으로 문서의 텍스트에 주석 추가'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5aba4c6446b2dbcfcb31c423a28eedd552799b4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967672"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>방법: 프로그래밍 방식으로 문서의 텍스트에 주석 추가
  문서 클래스의 주석 속성 다양 한 Microsoft Office Word 문서에서 텍스트에 메모를 추가 합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 다음 예제에서는 문서의 첫 번째 단락에 메모를 추가합니다.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 텍스트에 새 메모를 추가하려면

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 속성의 <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> 메서드를 호출하고 범위 및 메모 텍스트를 제공합니다. 다음 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>VSTO 추가 기능에서 텍스트에 새 메모를 추가 하려면

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 속성의 <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> 메서드를 호출하고 범위 및 메모 텍스트를 제공합니다.

     다음 코드 예제에서는 활성 문서에 메모를 추가합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>강력한 프로그래밍
 Word에서 메모에 추가하는 사용자 이니셜을 변경하려면 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> 속성을 사용합니다.

## <a name="see-also"></a>참고자료
- [방법: 프로그래밍 방식으로 문서에서 모든 메모 제거](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [문서 호스트 항목](../vsto/document-host-item.md)
