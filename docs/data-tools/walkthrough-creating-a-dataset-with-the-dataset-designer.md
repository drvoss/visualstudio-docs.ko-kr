---
title: '연습: 데이터 집합 디자이너를 사용 하 여 데이터 집합 만들기'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f91c24885cc6817889671dd7a1a6e7e1686ce93f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565002"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>연습: 데이터 집합 디자이너를 사용 하 여 데이터 집합 만들기

이 연습에서 사용 하 여 데이터 집합을 만들 합니다 **데이터 집합 디자이너**합니다. 문서를 새 프로젝트를 만들고 새 추가 과정을 단계별로 안내 **데이터 집합** 항목 되도록 합니다. 마법사를 사용 하지 않고 데이터베이스의 테이블을 기준으로 테이블을 만드는 방법을 알아봅니다.

## <a name="prerequisites"></a>전제 조건

이 연습에서는 Northwind 샘플 데이터베이스 및 SQL Server Express LocalDB를 사용 합니다.

1. SQL Server Express LocalDB가 없는 경우 설치에서 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express), 또는 합니다 **Visual Studio 설치 관리자**합니다. Visual Studio 설치 관리자를 SQL Server Express LocalDB의 일부로 설치할 수 있습니다 합니다 **데이터 저장소 및 처리** 워크 로드 또는 개별 구성 요소입니다.

2. 다음이 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 엽니다는 **SQL Server 개체 탐색기** 창입니다. (SQL Server 개체 탐색기의 일부로 설치 되는 **데이터 저장소 및 처리** Visual Studio 설치 관리자에서 작업 합니다.) 확장 된 **SQL Server** 노드. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 선택 **새 쿼리**합니다.

       쿼리 편집기 창이 열립니다.

    2. 복사 합니다 [Northwind Transact SQL 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 클립보드에 있습니다. 이 T-SQL 스크립트부터에서 Northwind 데이터베이스를 만들고 데이터로 채웁니다.

    3. T-SQL 스크립트, 쿼리 편집기에 붙여넣고 선택한 합니다 **Execute** 단추입니다.

       짧은 시간 후 쿼리 실행을 완료 하 고 Northwind 데이터베이스 생성 됩니다.

## <a name="create-a-new-windows-forms-application-project"></a>새 Windows Forms 애플리케이션 프로젝트 만들기

1. Visual Studio에서에 **파일** 메뉴에서 **새로 만들기** > **프로젝트**합니다.

2. 확장 **Visual C#** 하거나 **Visual Basic** 왼쪽 창에서 선택한 **Windows Desktop**합니다.

3. 가운데 창에서 선택 합니다 **Windows Forms 앱** 형식 프로젝션 합니다.

4. 프로젝트 이름을 **DatasetDesignerWalkthrough**를 선택한 후 **확인**합니다.

     Visual Studio 프로젝트를 추가 합니다 **솔루션 탐색기** 디자이너에서 새 양식을 표시 합니다.

## <a name="add-a-new-dataset-to-the-application"></a>응용 프로그램에 새 데이터 집합 추가

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

2. 왼쪽 창에서 선택 **데이터**을 선택한 후 **데이터 집합** 가운데 창에서.

3. 데이터 집합의 이름을 **NorthwindDataset**를 선택한 후 **추가**합니다.

     라는 파일을 추가 하는 visual Studio **NorthwindDataset.xsd** 프로젝트에서 엽니다 합니다 **데이터 집합 디자이너**합니다.

## <a name="create-a-data-connection-in-server-explorer"></a>서버 탐색기에서 데이터 연결 만들기

1. **보기** 메뉴에서 **서버 탐색기**를 클릭합니다.

2. **서버 탐색기**를 클릭 합니다 **데이터베이스에 연결** 단추입니다.

3. Northwind 샘플 데이터베이스에 대 한 연결을 만듭니다.

## <a name="create-the-tables-in-the-dataset"></a>데이터 집합에 테이블을 만들려면

이 섹션에서는 테이블 데이터 집합을 추가 하는 방법에 설명 합니다.

### <a name="to-create-the-customers-table"></a>Customers 테이블을 만들려면

1. 데이터 연결에서 만든 확장 **서버 탐색기**를 차례로 확장 합니다 **테이블** 노드.

2. 끌어서 합니다 **고객** 에서 테이블 **서버 탐색기** 에 **데이터 집합 디자이너**합니다.

     A **고객이** 데이터 테이블 및 **CustomersTableAdapter** 데이터 집합에 추가 됩니다.

### <a name="to-create-the-orders-table"></a>Orders 테이블을 만들려면

- 끌어서 합니다 **주문을** 에서 테이블 **서버 탐색기** 에 **데이터 집합 디자이너**합니다.

     **주문을** 데이터 테이블 **OrdersTableAdapter**, 및 간에 데이터 관계를 **고객** 및 **주문** 테이블에 추가 됩니다는 데이터 집합입니다.

### <a name="to-create-the-orderdetails-table"></a>OrderDetails 테이블을 만들려면

- 끌어서 합니다 **Order Details** 에서 테이블 **서버 탐색기** 에 **데이터 집합 디자이너**합니다.

     **Order Details** 데이터 테이블 **OrderDetailsTableAdapter**, 간의 데이터 관계를 **주문** 하 고 **OrderDetails** 테이블 데이터 집합에 추가 됩니다.

## <a name="next-steps"></a>다음 단계

- 데이터 집합을 저장 합니다.

- 항목을 선택 합니다 **데이터 원본** 창 폼으로 끌어 합니다. 자세한 내용은 [Visual Studio에서 데이터 바인딩 Windows Forms 컨트롤](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)합니다.

- Tableadapter에 더 많은 쿼리를 추가 합니다.

- 유효성 검사 논리를 추가 합니다 <xref:System.Data.DataTable.ColumnChanging> 또는 <xref:System.Data.DataTable.RowChanging> 데이터 집합에 있는 데이터 테이블의 이벤트입니다. 자세한 내용은 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터 집합 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)