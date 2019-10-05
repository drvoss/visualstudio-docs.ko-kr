---
title: '연습: 라디오 단추를 사용 하 여 문서에서 차트를 업데이트 합니다.'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88f7bb81557db813912fe4470e63b8d52c0c9371
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981051"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>연습: 라디오 단추를 사용 하 여 문서에서 차트를 업데이트 합니다.
  이 연습에서는 Microsoft Office Word의 문서 수준 사용자 지정에서 라디오 단추를 사용하여 문서에서 차트 스타일 선택 옵션을 사용자에게 제공하는 방법을 보여줍니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 디자인 타임에 문서 수준 프로젝트에서 문서에 차트를 추가합니다.

- 라디오 단추를 사용자 컨트롤에 추가하여 그룹화합니다.

- 옵션을 선택할 때 차트 스타일을 변경합니다.

  결과 전체 샘플을 보려면 Word 컨트롤 샘플을 참조 하세요 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 첫 번째 단계에서는 Word 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름을 사용 하 여 Word 문서 프로젝트를 만듭니다 **My Chart Options**합니다. 마법사에서 선택 **새 문서 만들기**합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

     Visual Studio 디자이너에서 새 Word 문서가 열리고 추가 합니다 **My Chart Options** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="add-a-chart-to-the-document"></a>문서에 차트 추가

### <a name="to-add-a-chart"></a>차트를 추가하려면

1. 리본 메뉴에서 Visual Studio 디자이너에 호스트 된 Word 문서에서를 클릭 합니다 **삽입** 탭 합니다.

2. 에 **텍스트** 그룹에서 클릭 합니다 **개체 삽입** 드롭다운 단추를 클릭 **개체**합니다.

     합니다 **개체** 대화 상자가 열립니다.

3. 에 **개체 유형** 목록에서 합니다 **새로 만들기** 탭을 선택 **Microsoft Graph 차트** 클릭 하 고 **확인**합니다.

     문서의 삽입 지점에 차트가 추가 됩니다 및 **데이터 시트** 일부 기본 데이터가 포함 된 창이 나타납니다.

4. 닫기 합니다 **데이터 시트** 창의 차트에서 기본값을 적용 하 여 차트에서 포커스를 이동 하려면 문서 안을 클릭 합니다.

5. 차트를 마우스 오른쪽 단추로 누른 **형식 개체**합니다.

6. 에 **레이아웃** 탭의 **형식 개체** 대화 상자에서 **사각형** 클릭 **확인**합니다.

## <a name="add-a-user-control-to-the-project"></a>프로젝트에 사용자 정의 컨트롤 추가
 기본적으로 문서에서는 여러 라디오 단추를 함께 사용할 수 있습니다. 라디오 단추를 사용자 컨트롤에 추가한 다음 컨택을 제어하는 코드를 작성하여 해당 단추가 올바르게 작동하도록 지정할 수 있습니다.

### <a name="to-add-a-user-control"></a>사용자 컨트롤을 추가하려면

1. 선택 된 **My Chart Options** 프로젝트 **솔루션 탐색기**합니다.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. 에 **새 항목 추가** 대화 상자, 클릭 **사용자 정의 컨트롤**, 컨트롤의 이름을 **ChartOptions** 클릭 **추가**합니다.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>사용자 컨트롤에 Windows Form 컨트롤을 추가하려면

1. 사용자 정의 컨트롤 디자이너에 표시 되지 않으면 두 번 클릭 **ChartOptions** 에 **솔루션 탐색기**합니다.

2. **공용 컨트롤** 탭을 **도구 상자**를 끌어 첫 번째 **라디오 단추** 사용자 컨트롤을 제어 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**columnChart**|
    |**텍스트**|**세로 막대형 차트**|

3. 두 번째 추가 **라디오 단추** 사용자에 게 제어 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**barChart**|
    |**텍스트**|**가로 막대형 차트**|

4. 세 번째 추가 **라디오 단추** 사용자에 게 제어 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**lineChart**|
    |**텍스트**|**꺾은선형 차트**|

5. 네 번째 추가 **라디오 단추** 사용자에 게 제어 하 고 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**areaBlockChart**|
    |**텍스트**|**영역 블록 차트**|

## <a name="add-references"></a>참조 추가
 에 대 한 참조 문서에서 사용자 정의 컨트롤에서 차트에 액세스 하려면 해야는 `Microsoft.Office.Interop.Graph` 프로젝트 어셈블리에에서 있습니다.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Microsoft.Office.Interop.Graph 어셈블리에 대한 참조를 추가하려면

1. **프로젝트** 메뉴에서 **참조 추가**를 클릭합니다.

     **참조 추가** 대화 상자가 나타납니다.

2. 에 **.NET** 탭을 선택 **Microsoft.Office.Interop.Graph** 누릅니다 **확인**합니다. 어셈블리의 14.0.0.0 버전을 선택합니다.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>라디오 단추를 선택할 때 차트 스타일 변경
 단추가 정상적으로 작동하도록 하려면 사용자 컨트롤에 대한 공용 이벤트를 만들고 선택 유형을 설정하는 속성을 추가한 다음 각 라디오 단추의 `CheckedChanged` 이벤트에 대해 프로시저를 만듭니다.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>사용자 컨트롤에서 이벤트와 속성을 만들려면

1. **솔루션 탐색기**사용자 정의 컨트롤을 마우스 오른쪽 단추로 클릭 한 다음 클릭 **코드 보기**합니다.

2. `SelectionChanged` 이벤트와 `Selection` 속성을 만드는 코드를 `ChartOptions` 클래스에 추가합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>라디오 단추의 CheckedChange 이벤트를 처리하려면

1. `CheckedChanged` 라디오 단추의 `areaBlockChart` 이벤트 처리기에서 차트 종류를 설정한 다음 이벤트를 발생시킵니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]

2. `CheckedChanged` 라디오 단추의 `barChart` 이벤트 처리기에서 차트 종류를 설정합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]

3. `CheckedChanged` 라디오 단추의 `columnChart` 이벤트 처리기에서 차트 종류를 설정합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]

4. `CheckedChanged` 라디오 단추의 `lineChart` 이벤트 처리기에서 차트 종류를 설정합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]

5. C#에서는 라디오 단추에 대해 이벤트 처리기를 추가해야 합니다. `ChartOptions` 생성자의 `InitializeComponent` 호출 아래에 코드를 추가할 수 있습니다. 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]

## <a name="add-the-user-control-to-the-document"></a>문서에 사용자 정의 컨트롤 추가
 새 사용자 정의 컨트롤은 자동으로 추가할 솔루션을 빌드할 때 합니다 **도구 상자**합니다. 컨트롤을 끌어 놓을 수 있습니다 합니다 **도구 상자** 문서.

### <a name="to-add-the-user-control-your-document"></a>문서에 사용자 정의 컨트롤을 추가하려면

1. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

     **ChartOptions** 사용자 컨트롤이 추가 되는 **도구 상자**합니다.

2. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 **ThisDocument.vb** 또는 **ThisDocument.cs**를 클릭 하 고 **뷰 디자이너**합니다.

3. 끌어서 합니다 `ChartOptions` 에서 제어 합니다 **도구 상자** 문서.

     에 **속성** 창, 문서에 추가 하 여 방금 컨트롤 이름 `ChartOptions1`합니다.

## <a name="change-the-chart-type"></a>차트 종류 변경
 사용자 컨트롤에서 선택하는 옵션에 따라 차트 종류를 변경하는 이벤트 처리기를 만듭니다.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>문서에 표시되는 차트의 종류를 변경하려면

1. `ThisDocument` 클래스에 다음 이벤트 처리기를 추가합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]

2. C#에서는 사용자 컨트롤에 대한 이벤트 처리기를 <xref:Microsoft.Office.Tools.Word.Document.Startup> 이벤트에 추가해야 합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 문서를 테스트하여 라디오 단추를 선택할 때 차트 스타일이 올바르게 업데이트되는지 확인할 수 있습니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. 키를 눌러 **F5** 프로젝트를 실행 합니다.

2. 여러 라디오 단추를 선택합니다.

3. 선택 항목과 일치하도록 차트 스타일이 변경되는지 확인합니다.

## <a name="next-steps"></a>다음 단계
 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 단추를 사용하여 텍스트 상자를 채웁니다. 자세한 내용은 [연습: 단추를 사용 하 여 문서에서 텍스트 상자에 텍스트 표시](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)합니다.

- 콤보 상자에서 스타일을 선택하여 서식을 변경합니다. 자세한 내용은 [연습: CheckBox 컨트롤을 사용 하 여 변경 문서 서식](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)합니다.

## <a name="see-also"></a>참고자료
- [Word를 사용 하 여 연습](../vsto/walkthroughs-using-word.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [Office 문서의 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
