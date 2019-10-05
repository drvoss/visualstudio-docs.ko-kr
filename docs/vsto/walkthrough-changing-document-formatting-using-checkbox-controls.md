---
title: CheckBox 컨트롤을 사용 하 여 문서 서식 변경
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24c3cb8d76551bb477f9c13cc56c313519f3b617
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328720"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>연습: CheckBox 컨트롤을 사용 하 여 문서 서식 변경
  이 연습에서는 Microsoft Office Word 용 문서 수준 사용자 지정에서 Windows Forms 컨트롤을 사용 하 여 텍스트 서식을 변경 하는 방법에 설명 합니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 디자인 타임에 문서 수준 프로젝트에서 문서에 텍스트 및 컨트롤을 추가 합니다.

- 옵션을 선택할 때 텍스트의 서식을 지정 합니다.

  결과 전체 샘플을 보려면 Word 컨트롤 샘플을 참조 하세요 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 첫 번째 단계에서는 Word 문서 프로젝트를 만듭니다.

### <a name="create-a-new-project"></a>새 프로젝트 만들기

1. 이름을 사용 하 여 Word 문서 프로젝트를 만듭니다 **My Word 서식이**합니다. 마법사에서 선택 **새 문서 만들기**합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

     Visual Studio 디자이너에서 새 Word 문서가 열리고 추가 합니다 **My Word 서식이** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="add-text-and-controls-to-the-word-document"></a>Word 문서에 텍스트 및 컨트롤 추가
 이 연습에서는 세 개의 확인란 및 일부 텍스트에 추가 된 <xref:Microsoft.Office.Tools.Word.Bookmark> Word 문서에 컨트롤입니다. 확인란의 텍스트 서식 지정에 대 한 사용자에 게 옵션을 제공 합니다.

### <a name="add-three-check-boxes"></a>확인란 세 개를 추가 합니다.

1. Visual Studio 디자이너에서 문서가 열려 있는지 확인합니다.

2. **공용 컨트롤** 탭을 **도구 상자**을 끌어 첫 번째 <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> 컨트롤을 문서로.

3. **속성** 창에서 다음 속성을 변경합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyBoldFont**|
    |**텍스트**|**굵게**|

4. 키를 눌러 **Enter** 첫 번째 확인란 아래 삽입 지점을 이동 합니다.

5. 아래 문서에 두 번째 확인란을 추가 합니다 `ApplyBoldFont` 확인란을 선택 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyItalicFont**|
    |**텍스트**|**기울임꼴**|

6. 키를 눌러 **Enter** 아래 두 번째 확인란 삽입 지점을 이동 합니다.

7. 세 번째 확인란 아래의 문서에 추가 된 `ApplyItalicFont` 확인란을 선택 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyUnderlineFont**|
    |**텍스트**|**밑줄**|

### <a name="add-text-and-a-bookmark-control"></a>텍스트 및 책갈피 컨트롤 추가

1. 삽입 지점을 check box 컨트롤 아래로 이동한 다음 텍스트를 입력:

    **이 텍스트의 서식을 변경 하는 확인란을 클릭 합니다.**

2. **Word 컨트롤** 탭의 **도구 상자**, 끌어를 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤을 문서.

    합니다 **책갈피 컨트롤 추가** 대화 상자가 나타납니다.

3. 문서에 추가한 텍스트를 선택 하 고 클릭 **확인**합니다.

    A <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤인 **Bookmark1** 문서에서 선택한 텍스트에 추가 됩니다.

4. 에 **속성** 창에서의 값을 변경 합니다 **(이름)** 속성을 **fontText.**

   그런 다음 확인란을 선택 하거나 취소 하는 경우 텍스트의 서식을 지정 하는 코드를 작성 합니다.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>확인란을 선택 하거나 취소 하는 경우 텍스트의 서식을 지정합니다
 사용자가 서식 옵션을 선택 하면 문서에서 텍스트의 형식을 변경 합니다.

### <a name="change-formatting-when-a-check-box-is-selected"></a>확인란을 선택 하면 서식 변경

1. 마우스 오른쪽 단추로 클릭 `ThisDocument` 에 **솔루션 탐색기**를 클릭 하 고 **코드 보기** 바로 가기 메뉴.

2. 에 대 한 C# 만 다음 상수를 추가 합니다 **ThisDocument** 클래스.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기는 `applyBoldFont` 확인란 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기는 `applyItalicFont` 확인란 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기는 `applyUnderlineFont` 확인란 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. C#를 텍스트 상자에 대 한 이벤트 처리기를 추가 해야 합니다 <xref:Microsoft.Office.Tools.Word.Document.Startup> 이벤트입니다. 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 텍스트를 선택 하거나 확인란의 선택을 취소 하면 올바르게 형식이 확인 하려면 문서를 테스트할 수 있습니다.

### <a name="test-your-document"></a>문서를 테스트 합니다.

1. 키를 눌러 **F5** 프로젝트를 실행 합니다.

2. 선택 하거나 확인란의 선택을 취소 합니다.

3. 텍스트 형식이 확인 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 확인란을 사용 하 여 프로그래밍 방식으로 Word 문서에 형식을 지정 하는 텍스트를 변경 하는 기본적인 방법을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 단추를 사용 하 여 텍스트 상자를 채웁니다. 자세한 내용은 [연습: 단추를 사용 하 여 문서에서 텍스트 상자에 텍스트 표시](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)합니다.

- 라디오 단추를 사용하여 차트 스타일 선택. 자세한 내용은 [연습: 라디오 단추를 사용 하 여 문서에서 차트를 업데이트](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)합니다.

## <a name="see-also"></a>참고자료
- [Word를 사용 하 여 연습](../vsto/walkthroughs-using-word.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 문서의 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
