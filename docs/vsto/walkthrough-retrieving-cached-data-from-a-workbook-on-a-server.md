---
title: '연습: 서버에서 통합 문서에서 캐시 된 데이터를 검색 합니다.'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d0bcf3f299d1d2d10b3b043b772fca832a505278
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826130"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>연습: 서버에서 통합 문서에서 캐시 된 데이터를 검색 합니다.
  이 연습에서는 Microsoft Office Excel 통합 문서에 사용 하 여 Excel을 시작 하지 않고 캐시 된 데이터 집합에서 데이터를 검색 하는 방법에 설명 합니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 클래스입니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 데이터를 포함 하는 데이터 집합을 정의 합니다 *AdventureWorksLT* 데이터베이스입니다.

- Excel 통합 문서 프로젝트를 콘솔 응용 프로그램 프로젝트에 데이터 집합의 인스턴스를 만드는 중입니다.

- 만들기를 <xref:Microsoft.Office.Tools.Excel.ListObject> 통합 문서에서 데이터 집합에 바인딩된 쉽고 채우는 <xref:Microsoft.Office.Tools.Excel.ListObject> 통합 문서가 열릴 때 데이터를 사용 하 여 합니다.

- 통합 문서의 데이터 캐시에 데이터 집합을 추가 합니다.

- Excel을 시작 하지 않고 콘솔 응용 프로그램에서 데이터 집합에 캐시 된 데이터 집합에서 데이터를 읽습니다.

  이 연습에서는 개발 컴퓨터에서 코드를 실행 하는 가정 하지만이 연습에서 보여 주는 코드 Excel이 설치 되어 있지 않은 서버에서 사용할 수 있습니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

- Microsoft SQL Server 또는 AdventureWorksLT 샘플 데이터베이스가 연결 된 Microsoft SQL Server Express의 실행 중인 인스턴스에 액세스 합니다. AdventureWorksLT 데이터베이스를 다운로드할 수 있습니다 합니다 [CodePlex 웹 사이트](http://go.microsoft.com/fwlink/?linkid=87843)합니다. 데이터베이스 연결에 대한 자세한 내용은 다음 항목을 참조하세요.

  - SQL Server Management Studio 또는 SQL Server Management Studio Express를 사용 하 여 데이터베이스를 연결 하려면 참조 [방법: 데이터베이스 (SQL Server Management Studio) 연결](/sql/relational-databases/databases/attach-a-database)합니다.

  - 명령줄을 사용 하 여 데이터베이스를 연결, 참조 [방법: SQL Server Express에 데이터베이스 파일을 첨부할](/previous-versions/sql/)합니다.

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>데이터 집합을 정의 하는 클래스 라이브러리 프로젝트 만들기
 Excel 통합 문서 프로젝트를 콘솔 응용 프로그램에 동일한 데이터 집합을 사용 하려면 두 프로젝트 모두에 의해 참조 되는 별도 어셈블리에 데이터 집합을 정의 해야 합니다. 이 연습에서는 클래스 라이브러리 프로젝트에서 데이터 집합을 정의 합니다.

### <a name="create-the-class-library-project"></a>클래스 라이브러리 프로젝트 만들기

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. 템플릿 창에서 확장 **Visual C#** 하거나 **Visual Basic**를 클릭 하 고 **Windows**합니다.

4. 프로젝트 템플릿 목록에서 선택 **클래스 라이브러리**합니다.

5. 에 **이름을** 상자에 입력 **AdventureWorksDataSet**합니다.

6. 클릭 **찾아보기**로 이동 하 *%UserProfile%\My 문서* (Windows XP 및 이전) 또는 *%UserProfile%\Documents* (Windows Vista)에 대 한 폴더를 마우스 클릭 **폴더 선택**합니다.

7. 에 **새 프로젝트** 대화 상자에서 **솔루션용 디렉터리 만들기** 확인란을 선택 하지 않으면.

8. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 합니다 **AdventureWorksDataSet** 프로젝트를 **솔루션 탐색기** 열어서 합니다 *Class1.cs* 또는 *Class1.vb* 코드 파일.

9. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 *Class1.cs* 또는 *Class1.vb*를 클릭 하 고 **삭제**합니다. 이 연습에 대 한이 파일이 필요가 없습니다.

## <a name="define-a-dataset-in-the-class-library-project"></a>클래스 라이브러리 프로젝트에서 데이터 집합을 정의 합니다.
 SQL Server 2005에 대 한 AdventureWorksLT 데이터베이스에서 데이터를 포함 하는 형식화 된 데이터 집합을 정의 합니다. 이 연습의 뒷부분에서 Excel 통합 문서 프로젝트를 콘솔 응용 프로그램 프로젝트에서이 데이터 집합을 참조 합니다.

 데이터 집합은는 *형식화 된 데이터 집합* AdventureWorksLT 데이터베이스의 Product 테이블에서 데이터를 나타내는입니다. 형식화 된 데이터 집합에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)합니다.

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>클래스 라이브러리 프로젝트에서 형식화 된 데이터 집합을 정의 합니다.

1. **솔루션 탐색기**를 클릭 합니다 **AdventureWorksDataSet** 프로젝트입니다.

2. 경우는 **데이터 원본** 창이 표시 되지 않으면, 메뉴 모음에 의해 표시 **뷰** > **기타 Windows**  >   **데이터 원본**합니다.

3. **새 데이터 소스 추가** 를 선택하여 **데이터 소스 구성 마법사**를 시작합니다.

4. **데이터베이스**를 클릭하고 **다음**을 클릭합니다.

5. AdventureWorksLT 데이터베이스에 대 한 기존 연결을 사용 하는 경우이 연결을 선택 하 고 클릭 **다음**합니다.

    그렇지 않은 경우 **새 연결**을 클릭하고 **연결 추가** 대화 상자를 사용하여 새 연결을 만듭니다. 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)합니다.

6. **애플리케이션 구성 파일에 연결 문자열 저장** 페이지에서 **다음**을 클릭합니다.

7. 에 **데이터베이스 개체 선택** 페이지에서 **테이블** 선택한 **Product (SalesLT)** 합니다.

8. **마침**을 클릭합니다.

    *AdventureWorksLTDataSet.xsd* 파일에 추가 되는 **AdventureWorksDataSet** 프로젝트. 이 파일은 다음 항목을 정의합니다.

   - `AdventureWorksLTDataSet`라는 형식화된 데이터 집합 이 데이터 집합은 AdventureWorksLT 데이터베이스의 Product 테이블의 내용을 나타냅니다.

   - 라는 TableAdapter `ProductTableAdapter`합니다. 이 TableAdapter의 읽기 및 쓰기 데이터를 사용할 수는 `AdventureWorksLTDataSet`합니다. 자세한 내용은 [TableAdapter 개요](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)합니다.

     이 연습 뒷부분에서는 이러한 두 개체를 모두 사용합니다.

9. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 **AdventureWorksDataSet** 누릅니다 **빌드**합니다.

     프로젝트가 오류 없이 빌드되는지 확인합니다.

## <a name="create-an-excel-workbook-project"></a>Excel 통합 문서 프로젝트 만들기
 데이터에 대 한 인터페이스에 대 한 Excel 통합 문서 프로젝트를 만듭니다. 이 연습의 뒷부분에서 만들려는 <xref:Microsoft.Office.Tools.Excel.ListObject> 데이터를 표시 하 고 통합 문서의 데이터 캐시에 데이터 집합의 인스턴스를 추가 합니다.

### <a name="create-the-excel-workbook-project"></a>Excel 통합 문서 프로젝트를 만들려면

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **AdventureWorksDataSet** 솔루션을 가리킵니다 **추가**를 클릭 하 고 **새 프로젝트**합니다.

2. 템플릿 창에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.

3. 확장된 **Office/SharePoint** 노드 아래에서 **Office 추가 기능** 노드를 선택합니다.

4. 프로젝트 템플릿 목록에서 **Excel 2010 통합 문서** 또는 **Excel 2013 통합 문서** 프로젝트를 선택합니다.

5. 에 **이름을** 상자에 입력 **AdventureWorksReport**합니다. 위치를 수정 하지 마십시오.

6. **확인**을 클릭합니다.

     **Visual Studio Tools for Office 프로젝트 마법사** 가 열립니다.

7. 했는지 **새 문서를 만듭니다** 을 선택 하 고 클릭 **확인**합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 열립니다는 **AdventureWorksReport** 디자이너에서 통합 문서 추가 **AdventureWorksReport** 프로젝트가 **솔루션 탐색기**합니다.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Excel 통합 문서 프로젝트에서 데이터 원본에 데이터 집합을 추가 합니다.
 Excel 통합 문서에서 데이터 집합을 표시할 수 있습니다, 전에 Excel 통합 문서 프로젝트에서 데이터 원본에 데이터 집합을 먼저 추가 해야 합니다.

1. **솔루션 탐색기**를 두 번 클릭 *Sheet1.cs* 또는 *Sheet1.vb* 아래를 **AdventureWorksReport** 프로젝트입니다.

     통합 문서 디자이너에서 열립니다.

2. **데이터** 메뉴에서 **새 데이터 소스 추가**를 클릭합니다.

     **데이터 원본 구성** 마법사가 열립니다.

3. 클릭 **개체**를 클릭 하 고 **다음**합니다.

4. 에 **바인딩할 개체 선택** 페이지를 클릭 **참조 추가**합니다.

5. 에 **프로젝트** 탭을 클릭 **AdventureWorksDataSet** 을 클릭 한 다음 **확인**합니다.

6. 아래는 **AdventureWorksDataSet** 의 네임 스페이스의 **AdventureWorksDataSet** 어셈블리 클릭 **AdventureWorksLTDataSet** 클릭 하 고 **마침** .

     합니다 **데이터 원본** 창이 열리고 및 **AdventureWorksLTDataSet** 데이터 원본 목록에 추가 됩니다.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>데이터 집합의 인스턴스에 바인딩되는 목록 개체 만들기
 통합 문서에서 데이터 집합을 표시 하려면 만들기를 <xref:Microsoft.Office.Tools.Excel.ListObject> 데이터 집합의 인스턴스에 바인딩된 합니다. 데이터 바인딩 컨트롤에 대 한 자세한 내용은 참조 하세요. [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)합니다.

1. 에 **데이터 원본** 창 확장 합니다 **AdventureWorksLTDataSet** 노드에서 **AdventureWorksDataSet**합니다.

2. 선택 된 **제품** 노드를 선택 하 고 표시 되는 드롭다운 화살표를 클릭 **ListObject** 드롭 다운 목록에서.

     드롭다운 화살표를 표시 되지 않는 경우 통합 문서 디자이너에서 열려 있는지 확인 합니다.

3. 끌기 합니다 **제품** A1 셀에는 테이블입니다.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> 제어 라는 `productListObject` A1 셀부터 워크시트에 만들어집니다. 동시에 `adventureWorksLTDataSet`라는 데이터 세트 개체와 <xref:System.Windows.Forms.BindingSource>라는 `productBindingSource`가 프로젝트에 추가됩니다. <xref:Microsoft.Office.Tools.Excel.ListObject> 가 <xref:System.Windows.Forms.BindingSource>에 바인딩된 다음 데이터 집합 개체에 바인딩됩니다.

## <a name="add-the-dataset-to-the-data-cache"></a>데이터 캐시에 데이터 집합을 추가 합니다.
 통합 문서에서 데이터 집합에 액세스 하려면 Excel 통합 문서 프로젝트 외부에서 코드를 사용 하려면 데이터 캐시에 데이터 집합을 추가 해야 합니다. 데이터 캐시에 대 한 자세한 내용은 참조 하세요. [문서 수준 사용자 지정에서 캐시 된 데이터](../vsto/cached-data-in-document-level-customizations.md) 하 고 [데이터를 캐시](../vsto/caching-data.md)합니다.

1. 디자이너에서 클릭 **adventureWorksLTDataSet**합니다.

2. 에 **속성** 창에서 설정 합니다 **한정자** 속성을 **공용**.

3. 설정 된 **CacheInDocument** 속성을 **True**합니다.

## <a name="initialize-the-dataset-in-the-workbook"></a>통합 문서에서 데이터 집합을 초기화
 콘솔 응용 프로그램을 사용 하 여 캐시 된 데이터 집합에서 데이터를 검색할 수 있습니다, 전에 캐시 된 데이터 집합을 먼저 채워야 합니다.

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 *Sheet1.cs* 또는 *Sheet1.vb* 파일을 클릭 **코드 보기**합니다.

2. `Sheet1_Startup` 이벤트 처리기를 다음 코드로 바꿉니다. 인스턴스를 사용 하 여이 코드는 `ProductTableAdapter` 에 정의 된 클래스를 **AdventureWorksDataSet** 프로젝트를 현재 비어 있는 경우 데이터를 사용 하 여 캐시 된 데이터 집합을 입력 합니다.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>검사점
 빌드하고 컴파일 및 오류 없이 실행 되는지 확인 하려면 Excel 통합 문서 프로젝트를 실행 합니다. 또한이 작업 캐시 된 데이터 집합을 채우는 하 고 통합 문서에서 데이터를 저장 합니다.

### <a name="build-and-run-the-project"></a>프로젝트 빌드 및 실행

1. **솔루션 탐색기**, 마우스 오른쪽 단추로 클릭 합니다 **AdventureWorksReport** 프로젝트 **디버그**를 클릭 하 고 **새 인스턴스 시작**.

     프로젝트를 빌드하고 Excel에서 통합 문서가 열립니다. 다음 사항을 확인합니다.

    - <xref:Microsoft.Office.Tools.Excel.ListObject> 데이터로 채웁니다.

    - 값을 **ListPrice** 의 첫 번째 행에 대 한 열을 <xref:Microsoft.Office.Tools.Excel.ListObject> 1431.5는 합니다. 이 연습의 뒷부분에서 사용할지는 콘솔 응용 프로그램에서 값을 수정 합니다 **ListPrice** 열입니다.

2. 통합 문서를 저장 합니다. 파일 이름이 나 통합 문서의 위치를 수정 하지 마십시오.

3. Excel을 닫습니다.

## <a name="create-a-console-application-project"></a>콘솔 응용 프로그램 프로젝트 만들기
 통합 문서에서 캐시 된 데이터 집합의 데이터를 수정 하는 데 콘솔 응용 프로그램 프로젝트를 만듭니다.

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **AdventureWorksDataSet** 솔루션을 가리킵니다 **추가**를 클릭 하 고 **새 프로젝트**합니다.

2. 에 **프로젝트 형식** 창 확장 **Visual C#** 또는 **Visual Basic**를 클릭 하 고 **Windows**합니다.

3. 에 **템플릿을** 창 **콘솔 응용 프로그램**합니다.

4. 에 **이름을** 상자에 입력 **DataReader**합니다. 위치를 수정 하지 마십시오.

5. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 합니다 **DataReader** 프로젝트를 **솔루션 탐색기** 열어서 합니다 *Program.cs* 또는 *Module1.vb* 코드 파일.

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>콘솔 응용 프로그램을 사용 하 여 캐시 된 데이터 집합에서 데이터를 검색
 사용 합니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 콘솔 응용 프로그램을 로컬에 데이터를 읽을 수 있는 클래스 `AdventureWorksLTDataSet` 개체입니다. 응용 프로그램을 로컬 데이터 집합 캐시 된 데이터 집합에서 데이터를 사용 하 여 초기화 된 있는지를 확인 하려면 로컬 데이터 집합의 행 수를 표시 합니다.

### <a name="retrieve-data-from-the-cached-dataset"></a>캐시 된 데이터 집합에서 데이터를 검색 합니다.

1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **DataReader** 프로젝트 및 클릭 **참조 추가**합니다.

2. 에 **.NET** 탭을 선택 **Microsoft.VisualStudio.Tools.Applications.ServerDocument**합니다.

3. **확인**을 클릭합니다.

4. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **DataReader** 프로젝트 및 클릭 **참조 추가**합니다.

5. 에 **프로젝트** 탭을 선택 **AdventureWorksDataSet**를 클릭 하 고 **확인**합니다.

6. 엽니다는 *Program.cs* 하거나 *Module1.vb* 코드 편집기에서 파일.

7. 다음을 추가 합니다 **를 사용 하 여** (에 대 한 C#) 또는 **Imports** (Visual Basic의 경우)에 대 한 문을 코드 파일의 맨 위에 있습니다.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. `Main` 메서드에 다음 코드를 추가합니다. 이 코드는 다음 개체를 선언합니다.

   - 인스턴스를 `AdventureWorksLTDataSet` 에 정의 된 형식에는 **AdventureWorksDataSet** 프로젝트.

   - 빌드 폴더에서 AdventureWorksReport 통합 문서에 대 한 경로 **AdventureWorksReport** 프로젝트입니다.

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 통합 문서의 데이터 캐시에 액세스 하는 데 사용할 개체입니다.

     > [!NOTE]
     > 다음 코드를 사용 하 여 통합 문서가 저장 하는 것으로 가정 합니다 *.xlsx* 확장 합니다. 프로젝트에서 통합 문서에 다른 확장 하는 경우 필요에 따라 경로 수정 합니다.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. 다음 코드를 추가 합니다 `Main` 메서드, 이전 단계에서 추가한 코드입니다. 이 코드는 다음 작업을 수행합니다.

   - 사용 하 여는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 의 속성을 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 통합 문서에서 캐시 된 데이터 집합에 액세스 하는 클래스입니다.

   - 로컬 데이터 집합에 캐시 된 데이터 집합에서 데이터를 읽습니다.

   - 데이터가 있는지 확인 하는 로컬 데이터 집합의 행 수가 표시 합니다.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. 에 **빌드** 메뉴에서 클릭 **DataReader 빌드**합니다.

## <a name="test-the-project"></a>프로젝트 테스트
 콘솔 응용 프로그램을 실행 하면 로컬 데이터 집합의 행 수가 표시 됩니다.

### <a name="test-the-workbook"></a>통합 문서를 테스트 합니다.

1. **솔루션 탐색기**, 마우스 오른쪽 단추로 클릭 합니다 **DataReader** 프로젝트를 가리키도록 **디버그**, 클릭 하 고 **새 인스턴스 시작**합니다.

     응용 프로그램 로컬 데이터 집합에 295 개 행이 있는지를 보고 하는지 확인 합니다.

2. 키를 눌러 **Enter** 응용 프로그램을 닫습니다.

## <a name="next-steps"></a>다음 단계
 다음이 항목에서 캐시 된 데이터로 작업 하는 방법에 대 한 자세한 수 있습니다.

- Excel을 시작 하지 않고 캐시 된 데이터 집합에서 데이터를 변경 합니다. 자세한 내용은 [연습: 서버에서 통합 문서에서 캐시 된 데이터 변경](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)합니다.

## <a name="see-also"></a>참고 항목

- [연습: 서버에서 통합 문서에 데이터 삽입](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [연습: 서버에서 통합 문서에서 캐시 된 데이터를 변경 합니다.](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
