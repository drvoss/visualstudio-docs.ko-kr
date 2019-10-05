---
title: CheckBox 컨트롤을 사용 하 여 워크시트 서식 변경
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 42d2c46f6fd61d74476933cfda3dea8c62b00c95
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328697"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>연습: CheckBox 컨트롤을 사용 하 여 워크시트 서식 변경
  이 연습에서는 Microsoft Office Excel 워크시트에서 확인란을 사용 하 여 서식을 변경 하려면의 기본 사항을 보여 줍니다. 만들고 프로젝트에 코드를 추가 하려면 Visual Studio에서 Office 개발 도구를 사용 합니다. 결과 전체 샘플을 보려면 Excel 컨트롤 샘플을 참조 하세요 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)합니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 워크시트에 텍스트 및 컨트롤을 추가 합니다.

- 옵션을 선택할 때 텍스트의 서식을 지정 합니다.

- 프로젝트를 테스트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 이 단계에서는 Visual Studio를 사용 하 여 Excel 통합 문서 프로젝트를 만들려는 합니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름으로 Excel 통합 문서 프로젝트를 만듭니다 **내 Excel 서식을**합니다. 했는지 **새 문서 만들기** 을 선택 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

     Visual Studio 디자이너에서 새 Excel 통합 문서를 열고 사이트를 추가 합니다 **내 Excel 서식을** 프로젝트가 **솔루션 탐색기**.

## <a name="add-text-and-controls-to-the-worksheet"></a>워크시트에 텍스트 및 컨트롤 추가
 이 연습에서는 해야 세 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 컨트롤 및 일부 텍스트를 <xref:Microsoft.Office.Tools.Excel.NamedRange> 제어 합니다.

### <a name="to-add-three-check-boxes"></a>확인란 세 개를 추가 하려면

1. 통합 문서는 Visual Studio 디자이너에 열려 있는지 확인 `Sheet1` 열려 있습니다.

2. **공용 컨트롤** 탭을 **도구 상자**, 끌어를 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 컨트롤 또는 셀 근처 **B2** 에서 **Sheet1**합니다.

3. **뷰** 메뉴에서 **속성** 창입니다.

4. 해야 **Checkbox1** 의 개체 이름 목록 상자에 표시 되는 **속성** 창에서 다음 속성을 변경:

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyBoldFont**|
    |**텍스트**|**굵게**|

5. 위 또는 주변 셀에 두 번째 확인란을 끌어 놓고 **B4** 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyItalicFont**|
    |**텍스트**|**기울임꼴**|

6. 세 번째 확인란으로 끌거나 셀 근처 **B6** 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**applyUnderlineFont**|
    |**텍스트**|**밑줄**|

7. 보유 하는 동안 모든 세 개의 확인란 컨트롤을 선택 합니다 **Ctrl** 키입니다.

8. Excel의 서식 탭의 정렬 그룹에서 클릭 **Align**를 클릭 하 고 **왼쪽 맞춤**합니다.

     세 개의 확인란 컨트롤에서 선택한 첫 번째 컨트롤의 위치에 있는 왼쪽 정렬 됩니다.

     끌어 다음으로 <xref:Microsoft.Office.Tools.Excel.NamedRange> 워크시트에 컨트롤입니다.

    > [!NOTE]
    > 추가할 수도 있습니다는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 를 입력 하 여 컨트롤 **텍스트 글꼴** 에 **이름** 상자입니다.

#### <a name="to-add-text-to-a-namedrange-control"></a>NamedRange 컨트롤에 텍스트를 추가 하려면

1. **Excel 컨트롤** 끌어서 도구 상자 탭을 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 셀 **b 9**합니다.

2. 확인 **$B$ 9** 편집 가능한 텍스트 상자 및 해당 셀에 표시 됩니다 **b 9** 을 선택 합니다. 없는 경우 셀을 클릭 **b 9** 하 여 선택 합니다.

3. **확인**을 클릭합니다.

4. 셀 **b 9** 명명 된 범위가 됩니다 `NamedRange1`합니다.

    워크시트로 표시 표시가 없습니다 하지만 `NamedRange1` 나타나는 합니다 **이름 상자** (워크시트 바로 위 왼쪽) 셀 **b 9** 선택 합니다.

5. 해야 **NamedRange1** 의 개체 이름 목록 상자에 표시 되는 **속성** 창에서 다음 속성을 변경:

   |속성|값|
   |--------------|-----------|
   |**이름**|**textFont**|
   |**Value2**|**이 텍스트의 서식을 변경 하는 확인란을 클릭 합니다.**|

   그런 다음 옵션을 선택할 때 텍스트의 서식을 지정 하는 코드를 작성 합니다.

## <a name="format-the-text-when-an-option-is-selected"></a>옵션을 선택할 때 텍스트의 서식을 지정합니다
 이 섹션에서는 워크시트에 있는 텍스트의 형식이 변경 되는 사용자가 서식 옵션을 선택 하면 되도록 코드를 작성 합니다.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>선택한 경우 확인란을 서식을 변경 하려면

1. 마우스 오른쪽 단추로 클릭 **Sheet1**를 클릭 하 고 **코드 보기** 바로 가기 메뉴.

2. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기는 `applyBoldFont` 확인란:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기는 `applyItalicFont` 확인란:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기는 `applyUnderlineFont` 확인란:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. C#에서는 확인란에 대 한 이벤트 처리기를 추가 해야 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 아래와 같이 이벤트입니다. 이벤트 처리기를 만드는 방법에 대 한 정보를 참조 하세요. [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 텍스트를 선택 하거나 확인란의 선택을 취소 하면 올바르게 형식이 되도록 통합 문서를 테스트할 수 있습니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. 키를 눌러 **F5** 프로젝트를 실행 합니다.

2. 선택 하거나 확인란의 선택을 취소 합니다.

3. 텍스트 형식이 확인 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 확인란을 사용 하 고 Excel 워크시트에 텍스트 서식 지정의 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 프로젝트를 배포 합니다. 자세한 내용은 [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)합니다.
- 단추를 사용하여 텍스트 상자를 채웁니다. 자세한 내용은 [연습: 단추를 사용 하 여 워크시트에 텍스트 상자에 텍스트 표시](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)합니다.

## <a name="see-also"></a>참고자료
- [Excel을 사용 하 여 연습](../vsto/walkthroughs-using-excel.md)
- [NamedRange 컨트롤](../vsto/namedrange-control.md)
- [Office 문서의 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
