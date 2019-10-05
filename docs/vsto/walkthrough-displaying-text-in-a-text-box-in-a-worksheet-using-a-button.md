---
title: 단추를 사용 하 여 워크시트에 텍스트 상자에 텍스트를 표시 합니다.
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b30eea0152b75cdd0869ececac674ee5aeee7933
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328715"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>연습: 단추를 사용 하 여 워크시트에 텍스트 상자에 텍스트를 표시 합니다.
  이 연습에서는 Visual Studio에서 Office 개발 도구를 사용 하 여 Excel 프로젝트를 만드는 방법과 Microsoft Office Excel 워크시트에서 단추 및 텍스트 상자를 사용 하는 기본 사항을 보여 줍니다. 결과 전체 샘플을 보려면 Excel 컨트롤 샘플을 참조 하세요 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)합니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 워크시트에 컨트롤을 추가 합니다.

- 단추를 클릭할 때 텍스트 상자를 채웁니다.

- 프로젝트를 테스트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 이 단계에서는 Visual Studio를 사용 하 여 Excel 통합 문서 프로젝트를 만들게 됩니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름으로 Excel 통합 문서 프로젝트를 만듭니다 **내 Excel 단추**합니다. 했는지 **새 문서 만들기** 을 선택 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

     Visual Studio 디자이너에서 새 Excel 통합 문서를 열고 사이트를 추가 합니다 **내 Excel 단추** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 이 연습에서는 단추 및 텍스트 상자에 첫 번째 워크시트를 해야 합니다.

### <a name="to-add-a-button-and-a-text-box"></a>단추 및 텍스트 상자를 추가하려면

1. 있는지 확인 합니다 **내 Excel Button.xlsx** Visual Studio 디자이너에 통합 문서가 열려와 `Sheet1` 표시 합니다.

2. **공용 컨트롤** 끌어서 도구 상자 탭을 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> 에 `Sheet1`입니다.

3. **뷰** 메뉴에서 **속성 창**합니다.

4. 있는지 확인 **TextBox1** 에 표시 되는 **속성** 창 드롭다운 상자 및 변경 합니다 **이름** 입력란의 속성 **displayText**.

5. 끌어서를 **단추** 컨트롤을 `Sheet1` 다음 속성을 변경 합니다.

   |속성|값|
   |--------------|-----------|
   |**이름**|**insertText**|
   |**텍스트**|**텍스트 삽입**|

   이제 단추를 클릭할 때 실행할 코드를 작성 합니다.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>단추를 클릭할 때 텍스트 상자 채우기
 사용자가 단추를 클릭할 때마다 **Hello World!** 텍스트 상자에 추가 됩니다.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>단추를 클릭할 때 텍스트 상자에 쓰려면

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 **Sheet1**를 클릭 하 고 **코드 보기** 바로 가기 메뉴.

2. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 단추의 이벤트 처리기:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. C#에서 이벤트 처리기를 추가 해야 합니다는 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 아래와 같이 이벤트입니다. 이벤트 처리기를 만드는 방법에 대 한 정보를 참조 하세요. [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)합니다.

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>애플리케이션 테스트
 통합 문서가 있는지 테스트할 수 있습니다 메시지 **Hello World!** 단추를 클릭할 때 텍스트 상자에 표시 됩니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. 키를 눌러 **F5** 프로젝트를 실행 합니다.

2. 단추를 클릭합니다.

3. 확인 **Hello World!** 텍스트 상자에 표시 됩니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 Excel 워크시트에서 단추 및 텍스트 상자를 사용 하는 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 프로젝트를 배포 합니다. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)합니다.

- 확인란을 사용 하 여 서식을 변경 합니다. 자세한 내용은 [연습: CheckBox 컨트롤을 사용 하 여 변경 워크시트 서식](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Excel을 사용 하 여 연습](../vsto/walkthroughs-using-excel.md)
- [Office 문서의 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
