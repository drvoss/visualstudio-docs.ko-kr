---
title: '연습: Word 작업 창의 컨트롤에 데이터 바인딩'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ddeba1539cf68d53f4b9f931d2bcd18a159028fd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438692"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>연습: Word 작업 창의 컨트롤에 데이터 바인딩
  이 연습에서는 word에서 작업 창의 컨트롤에 대 한 데이터 바인딩을 보여 줍니다. 컨트롤은 SQL Server 데이터베이스의 테이블 간 마스터/세부 관계를 보여 줍니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 데이터 바인딩된 Windows Forms 컨트롤을 사용 하 여 작업창을 만드는 중입니다.

- 마스터/세부 관계를 사용 하 여 컨트롤에 데이터를 표시 합니다.

- 응용 프로그램을 열 때 작업창을 표시 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스를 사용 하 여 서버에 액세스 합니다.

- SQL Server 데이터베이스에서 읽고 권한입니다.

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 첫 번째 단계에서는 Word 문서 프로젝트를 만듭니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름을 사용 하 여 Word 문서 프로젝트를 만듭니다 **My Word 작업 창의**합니다. 마법사에서 선택 **새 문서 만들기**합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

     Visual Studio 디자이너에서 새 Word 문서가 열리고 추가 합니다 **My Word 작업창** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="add-controls-to-the-actions-pane"></a>작업 창에 컨트롤 추가
 이 연습에서는 데이터 바인딩된 Windows Forms 컨트롤을 포함 하는 작업 창 컨트롤이 필요 합니다. 프로젝트에 데이터 원본을 추가 하 고 다음에서 컨트롤을 끌어 합니다 **데이터 원본** 작업 창 컨트롤에 창.

### <a name="to-add-an-actions-pane-control"></a>작업 창 컨트롤을 추가 하려면

1. 선택 된 **My Word 작업창** 프로젝트 **솔루션 탐색기**.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. 에 **새 항목 추가** 대화 상자에서 **작업 창 컨트롤**, 이름을 **actionscontrol로 지정한**를 클릭 하 고 **추가**합니다.

### <a name="to-add-a-data-source-to-the-project"></a>데이터 원본을 프로젝트에 추가 하려면

1. 경우는 **데이터 원본** 창이 표시 되지 않으면, 메뉴 모음에 의해 표시 **뷰** > **기타 Windows**  >   **데이터 원본**합니다.

   > [!NOTE]
   > 하는 경우 **데이터 소스 표시** 를 사용할 수 없는 Word 문서를 클릭 한 다음 다시 확인 합니다.

2. 클릭 **새 데이터 원본 추가** 시작 하는 **데이터 소스 구성 마법사**합니다.

3. 선택 **데이터베이스** 을 클릭 한 다음 **다음**합니다.

4. Northwind 샘플 SQL Server 데이터베이스에 데이터 연결을 선택 하거나 새 연결을 사용 하 여 추가 합니다 **새 연결** 단추입니다.

5. **다음**을 클릭합니다.

6. 선택 되어 있으면 연결을 저장 하는 옵션을 지우고 클릭 **다음**합니다.

7. 확장 된 **테이블** 에서 노드를 **데이터베이스 개체** 창입니다.

8. 옆에 확인란을 선택 합니다 **공급 업체** 하 고 **제품** 테이블입니다.

9. **마침**을 클릭합니다.

   마법사에 추가 합니다 **공급 업체** 테이블 및 **제품** 테이블을 **데이터 원본** 창. 또한 형식화 된 데이터 집합에 표시 되는 프로젝트를 추가 **솔루션 탐색기**합니다.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>작업 창 컨트롤에 데이터 바인딩된 Windows Forms 컨트롤을 추가 하려면

1. 에 **데이터 원본** 창 확장 합니다 **공급 업체** 테이블입니다.

2. 드롭다운 화살표를 클릭 합니다 **Company Name** 노드를 선택한 **콤보 상자**합니다.

3. 끌기 **CompanyName** 에서 합니다 **데이터 원본** 작업 창 컨트롤에 창.

     <xref:System.Windows.Forms.ComboBox> 작업 창 컨트롤에 컨트롤이 만들어집니다. 같은 시간에는 <xref:System.Windows.Forms.BindingSource> 라는 `SuppliersBindingSource`, 테이블 어댑터 및 <xref:System.Data.DataSet> 구성 요소 트레이에 프로젝트에 추가 됩니다.

4. 선택 `SuppliersBindingNavigator` 에 **구성 요소** 트레이 누릅니다 **삭제**합니다. 사용 하지 것입니다는 `SuppliersBindingNavigator` 이 연습 합니다.

    > [!NOTE]
    > 삭제 된 `SuppliersBindingNavigator` 모든 것에 대해 생성 된 코드를 제거 하지 않습니다. 이 코드를 제거할 수 있습니다.

5. 레이블 및 변경에는 콤보 상자를 이동 합니다 **크기** 속성을 **171, 21**합니다.

6. 에 **데이터 원본** 창 확장 합니다 **제품** 자식 테이블에를 **공급 업체** 테이블.

7. 드롭다운 화살표를 클릭 합니다 **ProductName** 노드를 선택한 **ListBox**합니다.

8. 끌기 **ProductName** 작업 창 컨트롤에 있습니다.

     <xref:System.Windows.Forms.ListBox> 작업 창 컨트롤에 컨트롤이 만들어집니다. 같은 시간에는 <xref:System.Windows.Forms.BindingSource> 라는 `ProductBindingSource` 테이블 어댑터 구성 요소 트레이에 프로젝트에 추가 됩니다.

9. 레이블 및 변경에는 목록 상자를 이동 합니다 **크기** 속성을 **171, 95**합니다.

10. 끌어서를 <xref:System.Windows.Forms.Button> 에서 **도구 상자** 작업창을 제어 하 고 목록 상자 아래에 배치 합니다.

11. 마우스 오른쪽 단추로 클릭 합니다 <xref:System.Windows.Forms.Button>, 클릭 **속성** 바로 가기 메뉴에서 다음 속성을 변경 합니다.

    |속성|값|
    |--------------|-----------|
    |**이름**|**삽입**|
    |**텍스트**|**삽입**|

12. 컨트롤에 맞게 사용자 정의 컨트롤의 크기를 조정 합니다.

## <a name="set-up-the-data-source"></a>데이터 원본 설정
 데이터 소스를 설정 하려면 코드를 추가 하는 <xref:System.Windows.Forms.UserControl.Load> 컨트롤을 데이터로 채울 작업 창 컨트롤의 이벤트를 <xref:System.Data.DataTable>, 설정 및 합니다 <xref:System.Windows.Forms.Binding.DataSource%2A> 및 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 각 컨트롤에 대 한 속성.

### <a name="to-load-the-control-with-data"></a>컨트롤에 데이터를 로드 하려면

1. 에 <xref:System.Windows.Forms.UserControl.Load> 이벤트 처리기는 `ActionsControl` 클래스에 다음 코드를 추가 합니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. C#에서 이벤트 처리기를 연결 해야 합니다는 <xref:System.Windows.Forms.UserControl.Load> 이벤트입니다. 이 코드를 배치할 수 있습니다 합니다 `ActionsControl` 생성자를 호출한 후 `InitializeComponent`합니다. 이벤트 처리기를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>컨트롤의 데이터 바인딩 속성을 설정 하려면

1. `CompanyNameComboBox` 컨트롤을 선택합니다.

2. 에 **속성** 창 오른쪽의 단추를 클릭 합니다 **DataSource** 속성을 선택 **suppliersBindingSource**합니다.

3. 오른쪽의 단추를 클릭 합니다 **DisplayMember** 속성과 선택 **CompanyName**합니다.

4. 확장를 **DataBindings** 속성 오른쪽의 단추를 클릭 합니다 **텍스트** 속성을 선택 **없음**.

5. `ProductNameListBox` 컨트롤을 선택합니다.

6. 에 **속성** 창 오른쪽의 단추를 클릭 합니다 **DataSource** 속성을 선택 **productsBindingSource**합니다.

7. 오른쪽의 단추를 클릭 합니다 **DisplayMember** 속성과 선택 **ProductName**합니다.

8. 확장를 **DataBindings** 속성 오른쪽의 단추를 클릭 합니다 **SelectedValue** 속성을 선택 **없음**.

## <a name="add-a-method-to-insert-data-into-a-table"></a>테이블에 데이터를 삽입 하는 메서드 추가
 다음 태스크는 바인딩된 컨트롤에서 데이터를 읽을 Word 문서에서 테이블을 채우는를 하는 것입니다. 먼저 테이블의 머리글에 서식을 적용 하는 절차를 만들고 추가 하는 `AddData` 메서드를 만들고 Word 표 서식을 지정 합니다.

### <a name="to-format-the-table-headings"></a>테이블 머리글의 서식을 지정 하려면

1. 에 `ActionsControl` 클래스를 테이블의 머리글의 서식을 지정 하는 메서드를 만듭니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>테이블을 만들려면

1. 에 `ActionsControl` 클래스, 아직 존재 하 고 작업 창에서 데이터를 테이블에 추가 하나는 테이블을 만듭니다는 메서드를 작성 합니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>텍스트를 Word 테이블에 삽입 하려면

1. 다음 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기는 **삽입** 단추입니다.

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. C#에서 이벤트 처리기를 만들어야 합니다를 <xref:System.Windows.Forms.Control.Click> 단추의 이벤트입니다.  이 코드를 배치할 수 있습니다 합니다 <xref:System.Windows.Forms.UserControl.Load> 이벤트 처리기는 `ActionsControl` 클래스입니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>작업 창 표시
 작업 창 컨트롤에 추가 된 후 표시 됩니다.

### <a name="to-show-the-actions-pane"></a>작업 창을 표시 하려면

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 **ThisDocument.vb** 또는 **ThisDocument.cs**를 클릭 하 고 **코드 보기** 바로 가기 메뉴.

2. 맨 위에 있는 컨트롤의 새 인스턴스를 만들고는 `ThisDocument` 다음과 같이 표시 되도록 클래스입니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. 코드를 추가 합니다 <xref:Microsoft.Office.Tools.Word.Document.Startup> 이벤트 처리기 `ThisDocument` 다음과 같이 표시 되도록 합니다.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 문서를 열 때 작업 창이 표시 되는지 확인 하려면 문서를 테스트할 수 있습니다. 작업 창 컨트롤에 마스터/세부 관계를 테스트 하 고 데이터는 단어에서 채워졌는지 확인 하면 테이블의 **삽입** 단추를 클릭 합니다.

### <a name="to-test-your-document"></a>문서를 테스트하려면

1. 키를 눌러 **F5** 프로젝트를 실행 합니다.

2. 작업 창이 표시 되는지 확인 합니다.

3. 콤보 상자에 회사를 선택 하 고 확인 하는 항목에는 **제품** 목록 상자의 변경 합니다.

4. 제품 선택, 클릭 **삽입** 작업 창에서 제품 세부 정보는 Word의 테이블에 추가 확인 합니다.

5. 여러 회사에서 추가 제품을 삽입 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 word에서 작업 창의 컨트롤에 데이터 바인딩의 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- Excel에서 컨트롤의 데이터 바인딩 자세한 내용은 [연습: Excel 작업 창의 컨트롤에 데이터 바인딩할](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)합니다.

- 프로젝트를 배포 합니다. 자세한 내용은 [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)합니다.

## <a name="see-also"></a>참고자료
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
