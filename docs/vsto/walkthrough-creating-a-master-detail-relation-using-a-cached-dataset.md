---
title: 캐시 된 데이터 집합을 사용 하 여 마스터-세부 관계 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0acf84dd983a8c10f2af526ae0bb904eaa90a360
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328362"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>연습: 캐시 된 데이터 집합을 사용 하 여 마스터-세부 관계를 만들려면
  이 연습에서는 워크시트에서 마스터/세부 관계를 만들고 솔루션을 오프 라인으로 사용할 수 있도록 데이터를 캐시 하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 워크시트에 컨트롤을 추가 합니다.

- 워크시트에서 캐시할 데이터 집합을 설정 합니다.

- 레코드를 스크롤할 수 있도록 코드를 추가 합니다.

- 프로젝트를 테스트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- SQL Server Northwind 샘플 데이터베이스에 액세스 합니다. 개발 컴퓨터 또는 서버의 데이터베이스 수 있습니다.

- SQL Server 데이터베이스에서 읽고 권한입니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 이 단계에서는 Excel 통합 문서 프로젝트를 만들게 됩니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. 이름으로 Excel 통합 문서 프로젝트를 만듭니다 **내 마스터-세부**, Visual Basic 또는 C#을 사용 하 여 합니다. 했는지 **새 문서 만들기** 을 선택 합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

   Visual Studio 디자이너에서 새 Excel 통합 문서를 열고 사이트를 추가 합니다 **내 마스터-세부** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기
 **데이터 원본** 창을 사용하여 형식화된 데이터 집합을 프로젝트에 추가합니다.

### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. 경우는 **데이터 원본** 창이 표시 되지 않으면, 메뉴 모음에 의해 표시 **뷰** > **기타 Windows**  >   **데이터 원본**합니다.

2. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

3. 선택 **데이터베이스** 을 클릭 한 다음 **다음**합니다.

4. Northwind 샘플 SQL Server 데이터베이스에 데이터 연결을 선택 하거나 새 연결을 사용 하 여 추가 합니다 **새 연결** 단추입니다.

5. 을 선택 하거나 연결을 만든 후 클릭 **다음**합니다.

6. 선택 되어 있으면 연결을 저장 하는 옵션을 지우고 클릭 **다음**합니다.

7. 확장 된 **테이블** 에서 노드를 **데이터베이스 개체** 창입니다.

8. 선택 된 **주문을** 테이블 및 **Order Details** 테이블.

9. **마침**을 클릭합니다.

   마법사에서 두 테이블을 추가 합니다 **데이터 원본** 창입니다. 또한 형식화 된 데이터 집합에 표시 되는 프로젝트를 추가 **솔루션 탐색기**합니다.

## <a name="add-controls-to-the-worksheet"></a>워크시트에 컨트롤 추가
 이 단계에서는 첫 번째 워크시트에 명명된 된 범위, 목록 개체, 및 두 개의 단추를 추가 합니다. 먼저 명명된 된 범위와 목록 개체를 추가 합니다 **데이터 원본** 창은 자동으로 데이터 소스를 바인딩할 수 있도록 합니다. 다음으로에서 단추를 추가 합니다 **도구 상자**합니다.

### <a name="to-add-a-named-range-and-a-list-object"></a>명명된 된 범위와 목록 개체를 추가 하려면

1. 있는지 확인 합니다 **내 마스터 Detail.xlsx** Visual Studio 디자이너에 통합 문서가 열려 사용 하 여 **Sheet1** 표시 합니다.

2. 열기는 **데이터 원본** 창 확장 및 합니다 **주문** 노드.

3. 선택 합니다 **OrderID** 열에 표시 되는 드롭다운 화살표를 클릭 하 고 합니다.

4. 클릭 **NamedRange** 확인 하 고 다음 끌어서 드롭 다운 목록에는 **OrderID** 셀으로 열 **A2**합니다.

     A <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤인 `OrderIDNamedRange` 셀에 작성 됩니다 **A2**합니다. 동시에 <xref:System.Windows.Forms.BindingSource> 라는 `OrdersBindingSource`, 테이블 어댑터 및 <xref:System.Data.DataSet> 인스턴스 프로젝트에 추가 됩니다. 컨트롤이 바인딩되는 <xref:System.Windows.Forms.BindingSource>, 차례로에 바인딩된는 <xref:System.Data.DataSet> 인스턴스.

5. 지난 칼럼에서 사용 중인 아래로 스크롤하여 합니다 **주문** 테이블입니다. 목록의 맨 아래에는 **Order Details** 테이블의 자식 이므로 여기서는 **주문** 테이블입니다. 이 옵션을 선택 **Order Details** 와 동일한 수준에 중이 아닌 테이블을 **주문** 테이블을 선택한 다음 표시 되는 드롭다운 화살표를 클릭 합니다.

6. 클릭 **ListObject** 확인 하 고 다음 끌어서 드롭 다운 목록에는 **OrderDetails** 셀에는 테이블 **A6**.

7. A <xref:Microsoft.Office.Tools.Excel.ListObject> 라는 컨트롤 **Order_DetailsListObject** 셀에 작성 됩니다 **A6**를 바인딩할는 <xref:System.Windows.Forms.BindingSource>합니다.

### <a name="to-add-two-buttons"></a>두 개의 단추를 추가 하려면

1. **공용 컨트롤** 탭의 **도구 상자**, 추가 <xref:System.Windows.Forms.Button> 컨트롤을 셀 **A3** 워크시트의 합니다.

    이 단추 이름이 `Button1`합니다.

2. 다른 항목 추가 <xref:System.Windows.Forms.Button> 컨트롤을 셀 **B3** 워크시트입니다.

    이 단추 이름이 `Button2`합니다.

   다음으로 문서에서 캐시할 데이터 집합을 표시 합니다.

## <a name="cache-the-dataset"></a>데이터 집합 캐시
 공용 및 설정 데이터 집합을 만들어 문서에서 캐시할 데이터 집합을 표시 합니다 **CacheInDocument** 속성입니다.

### <a name="to-cache-the-dataset"></a>데이터 집합 캐시

1. 선택 **NorthwindDataSet** 구성 요소 트레이에 합니다.

2. 에 **속성** 창에서 변경 합니다 **한정자** 속성을 **공용**합니다.

    데이터 집합 캐싱을 활성화 하려면 public 이어야 합니다.

3. 변경 된 **CacheInDocument** 속성을 **True**합니다.

   다음 단계 단추에 텍스트를 추가 하 고 C#에서 이벤트 처리기를 연결 하는 코드를 추가 하는 것입니다.

## <a name="initialize-the-controls"></a>컨트롤 초기화
 단추 텍스트를 설정 하 고 하는 동안 이벤트 처리기를 추가 합니다 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 이벤트입니다.

### <a name="to-initialize-the-data-and-the-controls"></a>데이터 및 컨트롤을 초기화 하려면

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 **Sheet1.vb** 또는 **Sheet1.cs**를 클릭 하 고 **코드 보기** 바로 가기 메뉴.

2. 다음 코드를 추가 합니다 `Sheet1_Startup` 단추에 대 한 텍스트를 설정 하는 방법입니다.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. C#에 해당에 대 한 이벤트 처리기 단추 클릭 이벤트를 추가 합니다 `Sheet1_Startup` 메서드.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>레코드를 스크롤할 수 있도록 코드를 추가 합니다.
 코드를 추가 하 여 <xref:System.Windows.Forms.Control.Click> 레코드 간을 이동 하려면 각 단추의 이벤트 처리기입니다.

### <a name="to-scroll-through-the-records"></a>레코드를 스크롤하려면

1. 에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트를 `Button1`, 레코드를 뒤로 이동 하려면 다음 코드를 추가 하 고:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. 에 대 한 이벤트 처리기를 추가 합니다 <xref:System.Windows.Forms.Control.Click> 이벤트를 `Button2`, 레코드를 진행 하려면 다음 코드를 추가 하 고:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 데이터가 예상 대로 나타나는지 하 고 솔루션을 오프 라인으로 사용할 수 있는 통합 문서를 테스트할 수 있습니다.

### <a name="to-test-the-data-caching"></a>데이터 캐싱 테스트

1. **F5**키를 누릅니다.

2. 명명된 된 범위와 목록 개체 데이터 원본의 데이터로 채워지는 것을 확인 합니다.

3. 단추를 클릭 하 여 일부 레코드를 스크롤하십시오.

4. 통합 문서를 저장 하 고 통합 문서와 Visual Studio를 닫습니다.

5. 데이터베이스에 연결을 사용 하지 않도록 설정 합니다. 데이터베이스 서버에 있는 경우 컴퓨터에서 네트워크 케이블을 분리 하거나 데이터베이스가 개발 컴퓨터의 경우 SQL Server 서비스를 중지 합니다.

6. Excel을 연 다음 엽니다 **내 마스터 Detail.xlsx** 에서 합니다 *\bin* 디렉터리 ( *\My Master-Detail\bin* Visual basic에서 또는 *\My Master-Detail\bin\ 디버그* C#에서).

7. 일부 끊기면 워크시트 정상적으로 작동 하는지 확인 하려면 레코드를 스크롤하십시오.

8. 데이터베이스에 다시 연결 합니다. 네트워크에 연결할 컴퓨터를 다시 데이터베이스 서버에 있는 경우 또는 데이터베이스가 개발 컴퓨터의 경우 SQL Server 서비스를 시작 합니다.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 워크시트에서 마스터/세부 정보 데이터 관계를 만들고 데이터 집합을 캐시의 기본 사항을 보여 줍니다. 다음으로 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 솔루션을 배포합니다. 자세한 내용은 참조 하세요. [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>참고자료
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [데이터 캐시](../vsto/caching-data.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
