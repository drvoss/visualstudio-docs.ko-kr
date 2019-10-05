---
title: '연습: 문서 수준 프로젝트의 단순 데이터 바인딩'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3b573842aee5f00f161213cf3e01dfcc4c8ba93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981064"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>연습: 문서 수준 프로젝트의 단순 데이터 바인딩
  이 연습에서는 문서 수준 프로젝트의 데이터 바인딩의 기본 사항을 보여 줍니다. SQL Server 데이터베이스에서 단일 데이터 필드는 Microsoft Office Excel에서 명명된 된 범위에 바인딩되어 있습니다. 이 연습에는 테이블의 모든 레코드를 스크롤할 수 있도록 하는 컨트롤을 추가 하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- Excel 프로젝트에 대 한 데이터 소스를 만드는 중입니다.

- 워크시트에 컨트롤을 추가 합니다.

- 데이터베이스 레코드 스크롤입니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스를 사용 하 여 서버에 액세스 합니다.

- SQL Server 데이터베이스에서 읽고 권한입니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 이 단계에서는 Excel 통합 문서 프로젝트를 만들게 됩니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름의 Excel 통합 문서 프로젝트를 만듭니다 **단순 데이터 바인딩 내**, Visual Basic 또는 C#을 사용 하 여 합니다. 했는지 **새 문서 만들기** 을 선택 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

   Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 추가 합니다 **단순 데이터 바인딩 내** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기
 **데이터 원본** 창을 사용하여 형식화된 데이터 집합을 프로젝트에 추가합니다.

### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. 경우는 **데이터 원본** 창이 표시 되지 않으면, 메뉴 모음에 의해 표시 **뷰** > **기타 Windows**  >   **데이터 원본**합니다.

2. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

3. 선택 **데이터베이스** 을 클릭 한 다음 **다음**합니다.

4. Northwind 샘플 SQL Server 데이터베이스에 데이터 연결을 선택 하거나 사용 하 여 새 연결을 추가 합니다 **새 연결** 단추입니다.

5. 연결을 선택 했거나 만든 후 클릭 **다음**합니다.

6. 선택 되어 있으면 연결을 저장 하는 옵션을 지우고 클릭 **다음**합니다.

7. 확장 된 **테이블** 에서 노드를 **데이터베이스 개체** 창입니다.

8. 옆에 확인란을 선택 합니다 **고객** 테이블입니다.

9. **마침**을 클릭합니다.

   마법사에 추가 합니다 **고객** 테이블을 **데이터 원본** 창. 또한 형식화 된 데이터 집합에 표시 되는 프로젝트를 추가 **솔루션 탐색기**합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 이 연습에서는 두 개의 명명 된 범위와 첫 번째 워크시트에서 단추 4 개 필요합니다. 먼저에서 두 개의 명명 된 범위를 추가 합니다 **데이터 원본** 창은 자동으로 데이터 소스를 바인딩할 수 있도록 합니다. 다음으로에서 단추를 추가 합니다 **도구 상자**합니다.

### <a name="to-add-two-named-ranges"></a>두 개의 명명 된 범위를 추가 하려면

1. 있는지 확인 합니다 *내 간단한 데이터 Binding.xlsx* Visual Studio 디자이너에 통합 문서가 열려 사용 하 여 **Sheet1** 표시 합니다.

2. 열기는 **데이터 원본** 창 확장 및 합니다 **고객** 노드.

3. 선택 합니다 **CompanyName** 열에 표시 되는 드롭다운 화살표를 클릭 하 고 합니다.

4. 선택 **NamedRange** 확인 하 고 다음 끌어서 드롭 다운 목록에는 **CompanyName** 셀으로 열 **A1**합니다.

     A <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤인 `companyNameNamedRange` 셀에 작성 됩니다 **A1**합니다. 동시에 <xref:System.Windows.Forms.BindingSource> 라는 `customersBindingSource`, 테이블 어댑터 및 <xref:System.Data.DataSet> 인스턴스 프로젝트에 추가 됩니다. 컨트롤이 바인딩되는 <xref:System.Windows.Forms.BindingSource>, 차례로에 바인딩된는 <xref:System.Data.DataSet> 인스턴스.

5. 선택 합니다 **CustomerID** 열에는 **데이터 원본** 창 표시 되는 드롭다운 화살표를 클릭 하 고 합니다.

6. 클릭 **NamedRange** 확인 하 고 다음 끌어서 드롭 다운 목록에는 **CustomerID** 셀으로 열 **B1**합니다.

7. 다른 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤인 `customerIDNamedRange` 셀에 작성 됩니다 **B1**, 바인딩할는 <xref:System.Windows.Forms.BindingSource>합니다.

### <a name="to-add-four-buttons"></a>네 개의 단추를 추가 하려면

1. **공용 컨트롤** 탭의 **도구 상자**, 추가 <xref:System.Windows.Forms.Button> 컨트롤을 셀 **A3** 워크시트의 합니다.

    이 단추 이름이 `Button1`합니다.

2. 표시 된 것 처럼 이름이 되도록이 순서로 다음 셀에 세 개의 추가 단추를 추가 합니다.

   |셀|(이름)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   다음 단계 단추에 텍스트를 추가 하 고 C#에서 이벤트 처리기를 추가 하는 것입니다.

## <a name="initialize-the-controls"></a>컨트롤 초기화
 단추 텍스트를 설정 하 고 하는 동안 이벤트 처리기를 추가 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 이벤트입니다.

### <a name="to-initialize-the-controls"></a>컨트롤을 초기화 하려면

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 **Sheet1.vb** 또는 **Sheet1.cs**를 클릭 하 고 **코드 보기** 바로 가기 메뉴.

2. 다음 코드를 추가 합니다 `Sheet1_Startup` 각 단추에 대 한 텍스트를 설정 하는 방법입니다.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. C#에 해당에 대 한 이벤트 처리기 단추 클릭 이벤트를 추가 합니다 `Sheet1_Startup` 메서드.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   이제 처리 하는 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 단추의 이벤트는 사용자가 레코드를 탐색할 수 있도록 합니다.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>레코드를 스크롤할 수 있도록 코드를 추가 합니다.
 코드를 추가 하 여 <xref:System.Windows.Forms.Control.Click> 레코드 간을 이동 하려면 각 단추의 이벤트 처리기입니다.

### <a name="to-move-to-the-first-record"></a>첫 번째 레코드를 이동 하려면

1. 에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 의 이벤트는 `Button1` 단추를 클릭 한 첫 번째 레코드를 이동 하려면 다음 코드를 추가:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>이전 레코드로 이동 하려면

1. 에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 의 이벤트는 `Button2` 단추 및 씩 위치를 뒤로 이동 하려면 다음 코드를 추가:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>다음 레코드로 이동 하려면

1. 에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 의 이벤트는 `Button3` 단추를 선택한 위치로 이동 하 여 하나에서 다음 코드를 추가:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>마지막 레코드를 이동 하려면

1. 에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 의 이벤트는 `Button4` 단추를 클릭 한 다음 코드를 이동 하는 마지막 레코드를 추가:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 데이터베이스의 레코드를 찾아볼 수 있도록 되도록 통합 문서를 테스트할 수 있습니다.

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. 키를 눌러 **F5** 프로젝트를 실행 합니다.

2. 첫 번째 레코드 셀에 나타나는지 확인 **A1** 하 고 **B1**합니다.

3. 클릭 합니다 **>** (`Button3`) 단추 및 다음 레코드로 셀에 나타나는지 확인 **A1** 고 **B1**합니다.

4. 예상 대로 레코드 변경 되는지 확인 하려면 다른 스크롤 단추를 클릭 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 데이터베이스의 필드에 명명된 된 범위를 바인딩하는 기본적인을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 오프 라인으로 사용할 수 있도록 데이터를 캐시 합니다. 자세한 내용은 [방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터를 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)합니다.

- 테이블의 여러 열에 셀을 하나의 필드에 대신 바인딩하십시오. 자세한 내용은 [연습: 문서 수준 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)합니다.

- 사용 하 여를 <xref:System.Windows.Forms.BindingNavigator> 컨트롤을 레코드를 스크롤합니다. 자세한 내용은 [방법: Windows Forms BindingNavigator 컨트롤을 사용 하 여 데이터를 이동](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)합니다.

## <a name="see-also"></a>참고자료
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [연습: 문서 수준 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
