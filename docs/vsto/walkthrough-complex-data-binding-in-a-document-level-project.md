---
title: '연습: 문서 수준 프로젝트의 복합 데이터 바인딩'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 026dc77573bbedce7882f9b3cceab049ef1066e4
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692349"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>연습: 문서 수준 프로젝트의 복합 데이터 바인딩
  이 연습에서는 문서 수준 프로젝트에서 복잡 한 데이터 바인딩의 기본 사항을 보여 줍니다. Northwind SQL Server 데이터베이스의 필드에 Microsoft Office Excel 워크시트에서 여러 셀을 바인딩할 수 있습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 통합 문서 프로젝트 데이터 소스를 추가 합니다.

- 워크시트에 데이터 바인딩된 컨트롤을 추가 합니다.

- 데이터 변경 내용을 다시 데이터베이스에 저장 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- Northwind SQL Server 예제 데이터베이스를 사용 하 여 서버에 액세스 합니다.

- SQL Server 데이터베이스에서 읽고 권한입니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 첫 번째 단계는 Excel 통합 문서 프로젝트를 만드는 것입니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름의 Excel 통합 문서 프로젝트를 만듭니다 **복잡 한 데이터 바인딩 내**합니다. 마법사에서 선택 **새 문서 만들기**합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

     Visual Studio가 디자이너에서 새 Excel 통합 문서를 열고 추가 합니다 **복합 데이터 바인딩 내** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기
 **데이터 원본** 창을 사용하여 형식화된 데이터 집합을 프로젝트에 추가합니다.

### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. 경우는 **데이터 원본** 창이 표시 되지 않으면, 메뉴 모음에 의해 표시 **뷰** > **기타 Windows**  >   **데이터 원본**합니다.

2. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

3. 선택 **데이터베이스** 을 클릭 한 다음 **다음**합니다.

4. Northwind 샘플 SQL Server 데이터베이스에 데이터 연결을 선택 하거나 새 연결을 사용 하 여 추가 합니다 **새 연결** 단추입니다.

5. 연결을 선택 했거나 만든 후 클릭 **다음**합니다.

6. 선택 되어 있으면 연결을 저장 하는 옵션을 지우고 클릭 **다음**합니다.

7. 확장 된 **테이블** 에서 노드를 **데이터베이스 개체** 창입니다.

8. 옆에 확인란을 선택 합니다 **직원** 테이블입니다.

9. **마침**을 클릭합니다.

   마법사에 추가 합니다 **직원** 테이블의 **데이터 원본** 창. 또한 형식화 된 데이터 집합에 표시 되는 프로젝트를 추가 **솔루션 탐색기**합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 워크시트에 표시 됩니다는 **직원** 통합 문서가 열릴 때 테이블입니다. 사용자 수는 데이터를 변경 하 고 다음 단추를 클릭 하 여 이러한 변경 내용을 다시 데이터베이스에 저장 됩니다.

 테이블에 워크시트를 자동으로 바인딩하려면 추가할 수 있습니다는 <xref:Microsoft.Office.Tools.Excel.ListObject> 에서 워크시트에 컨트롤을 **데이터 원본** 창입니다. 사용자 변경 내용을 저장 하는 옵션을 제공 하려면 추가 된 <xref:System.Windows.Forms.Button> 에서 제어 합니다 **도구 상자**.

#### <a name="to-add-a-list-object"></a>목록 개체를 추가 하려면

1. 있는지 확인 합니다 **내 복잡 한 데이터 Binding.xlsx** Visual Studio 디자이너에 통합 문서가 열려 사용 하 여 **Sheet1** 표시 합니다.

2. 엽니다는 **데이터 원본** 창과 선택 합니다 **직원** 노드.

3. 표시 되는 드롭다운 화살표를 클릭 합니다.

4. 선택 **ListObject** 드롭 다운 목록에서.

5. 끌어서 합니다 **직원** 셀에는 테이블 **A6**합니다.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤인 `EmployeesListObject` 셀에 작성 됩니다 **A6**합니다. 동시에 <xref:System.Windows.Forms.BindingSource> 라는 `EmployeesBindingSource`, 테이블 어댑터 및 <xref:System.Data.DataSet> 인스턴스 프로젝트에 추가 됩니다. 컨트롤이 바인딩되는 <xref:System.Windows.Forms.BindingSource>, 차례로에 바인딩된는 <xref:System.Data.DataSet> 인스턴스.

### <a name="to-add-a-button"></a>단추를 추가 하려면

1. **공용 컨트롤** 탭의 **도구 상자**, 추가 <xref:System.Windows.Forms.Button> 컨트롤을 셀 **A4** 워크시트의 합니다.

   워크시트를 열면 텍스트는 단추를 추가 하려면 다음 단계가입니다.

## <a name="initialize-the-control"></a>컨트롤 초기화
 텍스트에 있는 단추를 추가 합니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 이벤트 처리기입니다.

### <a name="to-initialize-the-control"></a>컨트롤을 초기화 하려면

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 **Sheet1.vb** 또는 **Sheet1.cs**를 클릭 하 고 **코드 보기** 바로 가기 메뉴.

2. 다음 코드를 추가 합니다 `Sheet1_Startup` b에 대 한 텍스트를 설정 하는 방법`utton`합니다.

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. C#에 해당 부문에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트는 `Sheet1_Startup` 메서드.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   이제 처리 하는 코드를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 단추의 이벤트입니다.

## <a name="save-changes-to-the-database"></a>변경 내용을 데이터베이스에 저장
 에 변경 사항이 데이터베이스에 다시 명시적으로 저장 될 때까지 데이터가 로컬 데이터 집합에만 존재 합니다.

### <a name="to-save-changes-to-the-database"></a>데이터베이스에 변경 내용을 저장 하려면

1. 에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트를는 `button`, 다시 데이터베이스에 데이터 집합에서 변경 된 모든 변경 내용을 커밋 하도록 다음 코드를 추가 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 목록 개체의 데이터를 조작할 수 있습니다 및 데이터가 예상 대로 나타나는지 확인 하려면 통합 문서를 테스트할 수 있습니다.

### <a name="to-test-the-data-binding"></a>데이터 바인딩을 테스트 하려면

- **F5**키를 누릅니다.

     통합 문서를 열 때 데이터를 사용 하 여 목록 개체 채워지는지 확인 합니다 **직원** 테이블입니다.

### <a name="to-modify-data"></a>데이터를 수정 하려면

1. 셀을 클릭 **B7**, 이름이 포함 되어야 하는 **Davolio**합니다.

2. 이름을 입력 **Anderson**, 누릅니다 **Enter**합니다.

### <a name="to-modify-a-column-header"></a>열 머리글을 수정 하려면

1. 열 머리글을 포함 하는 셀을 클릭 **LastName**합니다.

2. 형식 **성을**, 두 단어 사이 공백을 포함 하 여 누릅니다 **Enter**합니다.

### <a name="to-save-data"></a>데이터를 저장 하려면

1. 클릭 **저장할** 워크시트에 있습니다.

2. Excel을 종료합니다. 클릭 **No** 변경 내용을 저장 하 라는 메시지가 표시 되는 경우.

3. 키를 눌러 **F5** 프로젝트를 다시 실행 합니다.

     목록 개체의 데이터로 채워집니다 합니다 **직원** 테이블입니다.

4. 셀의 이름을 **B7** 그대로 **Anderson**를 수행 하 고 다시 데이터베이스에 저장 된 변경 데이터는 합니다. 열 머리글 **LastName** 공백 없이 원래 형식 데이터베이스에 열 머리글 바인딩되지 않은 워크시트에 대 한 변경 내용을 저장 하지 않은 것 이므로 다시 변경 되었습니다.

### <a name="to-add-new-rows"></a>새 행을 추가 하려면

1. 목록 개체 안의 셀을 선택 합니다.

    별표를 사용 하 여 목록의 맨 아래에 새 행이 나타납니다 ( **\*** ) 새 행의 첫 번째 셀에서입니다.

2. 빈 행의 다음 정보를 추가 합니다.

   |EmployeeID|LastName|FirstName|제목|
   |----------------|--------------|---------------|-----------|
   |10|면적|Shu|영업 관리자|

### <a name="to-delete-rows"></a>행을 삭제 하려면

- 워크시트의 왼쪽에 있는 번호 16 (16 행)를 마우스 오른쪽 단추로 누른 **삭제**합니다.

### <a name="to-sort-the-rows-in-the-list"></a>목록에서 행을 정렬 하려면

1. 목록 내에서 셀을 선택 합니다.

     각 열 머리글에 화살표 단추가 나타납니다.

2. 화살표 단추를 클릭 합니다 **Last Name** 열 머리글입니다.

3. 클릭 **오름차순 정렬**합니다.

     행은 성을 기준으로 사전순으로 정렬 됩니다.

### <a name="to-filter-information"></a>정보를 필터링 하려면

1. 목록 내에서 셀을 선택 합니다.

2. 화살표 단추를 클릭 합니다 **Title** 열 머리글입니다.

3. 클릭 **영업 담당자**합니다.

     목록에 있는 행만 보여 줍니다 **판매 담당자** 에 **Title** 열입니다.

4. 화살표 단추를 클릭 합니다 **Title** 열 머리글을 다시 합니다.

5. 클릭 **(All)** 합니다.

     필터링이 제거 되 고 모든 행이 나타납니다.

## <a name="next-steps"></a>다음 단계
 이 연습에는 목록 개체에는 데이터베이스의 테이블을 바인딩하는 기본적인 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 오프 라인으로 사용할 수 있도록 데이터를 캐시 합니다. 자세한 내용은 [방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터를 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)합니다.

- 솔루션을 배포합니다. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)합니다.

- 필드와 테이블 간 마스터/세부 관계를 만듭니다. 자세한 내용은 [연습: 캐시 된 데이터 집합을 사용 하 여 마스터-세부 관계를 만들고](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)합니다.

## <a name="see-also"></a>참고자료
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [연습: 문서 수준 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
