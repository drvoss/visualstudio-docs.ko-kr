---
title: '방법: 프로그래밍 방식으로 Word에서 기본 제공 대화 상자를 사용 하 여'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f8037e4d91aa7706c7ffd7b9f32778dfeac79488
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961643"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>방법: 프로그래밍 방식으로 Word에서 기본 제공 대화 상자를 사용 하 여
  Microsoft Office Word에서 작업할 때 사용자 입력에 대 한 대화 상자를 표시 해야 하는 경우가 있습니다. 만들 수 있지만 사용자 고유의에서 노출 되는 word에서 기본 제공 대화 상자를 사용 하는 방법을 사용 하려면 수도 있습니다는 <xref:Microsoft.Office.Interop.Word.Dialogs> 의 컬렉션을 <xref:Microsoft.Office.Interop.Word.Application> 개체입니다. 이 열거형으로 표현 되는 기본 제공 대화 상자에서는 200에 액세스할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>대화 상자를 표시 합니다.
 대화 상자를 표시 하려면 값 중 하나를 사용 합니다 <xref:Microsoft.Office.Interop.Word.WdWordDialog> 만들려면 열거형을 <xref:Microsoft.Office.Interop.Word.Dialog> 표시할 대화 상자를 나타내는 개체입니다. 그런 다음, 호출을 <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> 메서드는 <xref:Microsoft.Office.Interop.Word.Dialog> 개체.

 다음 코드 예제를 표시 하는 방법에 설명 합니다 **파일 열기** 대화 상자. 이 예제를 사용 하려면에서 실행 합니다 `ThisDocument` 또는 `ThisAddIn` 프로젝트에서 클래스입니다.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>런타임에 바인딩을 통해 사용할 수 있는 액세스 대화 상자 멤버
 일부 속성 및 메서드 Word에서 대화 상자 런타임에 바인딩을 통해서만 사용할 수 있습니다. Visual Basic에서 프로젝트 위치 **Option Strict** 가 on으로 리플렉션을 사용 하면 이러한 멤버에 액세스를 해야 합니다. 자세한 내용은 [Office 솔루션에서 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)합니다.

 다음 코드 예제에 사용 하는 방법을 보여 줍니다.는 **이름** 의 속성을 **파일 열기** 대화 상자에서 Visual Basic 프로젝트 위치 **Option Strict** 는 꺼져 있거나 Visual C# 대상으로 하는 프로젝트를 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]합니다. 이 예제를 사용 하려면에서 실행 합니다 `ThisDocument` 또는 `ThisAddIn` 프로젝트에서 클래스입니다.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 다음 코드 예제에서는 리플렉션을 사용 하 여 액세스 하는 방법에 설명 합니다 **이름** 의 속성을 **파일 열기** 대화 상자에서 Visual Basic 프로젝트 위치 **Option Strict** 는 에 이 예제를 사용 하려면에서 실행 합니다 `ThisDocument` 또는 `ThisAddIn` 프로젝트에서 클래스입니다.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>참고자료
- [방법: 프로그래밍 방식으로 숨김된 모드에서 Word 대화 상자를 사용 하 여](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [리플렉션(C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [리플렉션(Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
