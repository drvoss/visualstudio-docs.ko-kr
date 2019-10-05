---
title: 데이터 세트 쿼리
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bec1c878dce59ccb5444d74ba0255c9ceb705780
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402738"
---
# <a name="query-datasets"></a>데이터 세트 쿼리
데이터 집합의 특정 레코드를 검색 하려면 사용 합니다 `FindBy` 메서드는 DataTable에서 테이블의 행 컬렉션을 반복 하거나 사용 하 여 사용자 고유의 foreach 문을 작성할 [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)합니다.

## <a name="dataset-case-sensitivity"></a>데이터 집합의 대/소문자 구분
데이터 집합 내에서 테이블 및 열 이름은 기본적으로 대/소문자-즉, "Customers" 라는 데이터 집합의 테이블 수 수 라고도 "고객"을 선택 합니다. 이 SQL Server를 포함 하 여 여러 데이터베이스의 명명 규칙을 찾습니다. SQL Server의 기본 동작은 대/소문자를 통해서만 데이터 요소의 이름을 구별할 수 없으며 합니다.

> [!NOTE]
> 와 달리 데이터 집합을 XML 문서는 대/소문자 구분, 스키마에 정의 된 데이터 요소 이름은 대/소문자 구분 합니다. 예를 들어 스키마 프로토콜을 통해 "Customers" 및 "customers." 라는 다른 테이블 이라고 하는 테이블을 정의 하려면 이 데이터 집합 클래스를 생성 하는 대/소문자만 다른 요소가 포함 된 스키마를 사용 하는 경우 이름 충돌이 발생할 수 있습니다.

그러나 대/소문자 구분 데이터를 데이터 집합 내에서 해석 되는 방식을 비율을 수 있습니다. 예를 들어 데이터 집합 테이블의 데이터를 필터링 하면 검색 조건과 비교는 대/소문자 구분 여부에 따라 다른 결과 반환할 수 있습니다. 필터링, 검색 및 데이터 집합의 설정 하 여 정렬의 대/소문자를 구분 하는 것을 제어할 수 있습니다. <xref:System.Data.DataSet.CaseSensitive%2A> 속성입니다. 데이터 집합의 모든 테이블이 기본적으로이 속성의 값을 상속합니다. (테이블을 설정 하 여 각 개별 테이블에 대해이 속성을 재정의할 수 있습니다 <xref:System.Data.DataTable.CaseSensitive%2A> 속성입니다.)

## <a name="locate-a-specific-row-in-a-data-table"></a>데이터 테이블의 특정 행 찾기

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>기본 키 값을 사용 하 여 형식화 된 데이터 집합에서 행을 찾으려면

- 행을 찾으려면 호출 강력한 형식의 `FindBy` 테이블의 기본 키를 사용 하는 메서드입니다.

     다음 예제에서는 `CustomerID` 열이 기본 키를 `Customers` 테이블입니다. 즉, 생성 된 `FindBy` 메서드는 `FindByCustomerID`합니다. 이 예제에서는 특정 할당할 <xref:System.Data.DataRow> 생성을 사용 하 여 변수에 `FindBy` 메서드.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>기본 키 값을 사용 하 여 형식화 되지 않은 데이터 집합에서 행을 찾으려면

- 호출을 <xref:System.Data.DataRowCollection.Find%2A> 메서드는 <xref:System.Data.DataRowCollection> 컬렉션, 기본 키를 매개 변수로 전달 합니다.

     다음 예제에서는 라는 새 행을 선언 하는 방법을 보여 줍니다 `foundRow` 의 반환 값을 할당 합니다 <xref:System.Data.DataRowCollection.Find%2A> 메서드. 기본 키가 있으면 열 인덱스 1의 내용은 메시지 상자에 표시 됩니다.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>열 값을 기준으로 행 찾기

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>열에 값을 기반으로 하는 행을 찾으려면

- 데이터 테이블을 사용 하 여 만들어집니다 합니다 <xref:System.Data.DataTable.Select%2A> 배열을 반환 하는 메서드 <xref:System.Data.DataRow>에 전달 된 식에 따라 s는 <xref:System.Data.DataTable.Select%2A> 메서드. 유효한 식을 만드는 방법에 대 한 자세한 내용은 페이지의 "식 구문" 섹션에 대 한 참조를 <xref:System.Data.DataColumn.Expression%2A> 속성입니다.

     다음 예제에서는 사용 하는 방법을 보여 줍니다 합니다 <xref:System.Data.DataTable.Select%2A> 메서드는 <xref:System.Data.DataTable> 특정 행을 찾기 위한 합니다.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>액세스 관련 레코드
데이터 집합의 테이블 관련 되어 있는 경우는 <xref:System.Data.DataRelation> 개체 가능 관련된 레코드를 다른 테이블에서 사용할 수 있습니다. 예를 들어 데이터 집합 포함 하는 `Customers` 고 `Orders` 테이블 사용할 수 있습니다.

사용할 수는 <xref:System.Data.DataRelation> 호출 하 여 관련된 레코드를 찾을 개체입니다 합니다 <xref:System.Data.DataRow.GetChildRows%2A> 메서드의 <xref:System.Data.DataRow> 부모 테이블에서. 이 메서드는 관련 된 자식 레코드의 배열을 반환합니다. 하거나 호출할 수 있습니다 합니다 <xref:System.Data.DataRow.GetParentRow%2A> 메서드는 <xref:System.Data.DataRow> 자식 테이블의 합니다. 이 메서드는 단일 <xref:System.Data.DataRow> 부모 테이블에서.

이 페이지는 형식화 된 데이터 집합을 사용 하는 예제를 제공 합니다. 형식화 되지 않은 데이터 집합에서 관계를 탐색 하는 방법에 대 한 내용은 [Datarelation 탐색](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations)합니다.

> [!NOTE]
> Windows Forms 응용 프로그램에서 작업 하 고 데이터 바인딩 기능을 사용 하 여 데이터를 표시 하는 경우 디자이너에서 생성 된 양식 응용 프로그램에 대 한 충분 한 기능을 제공할 수 있습니다. 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)합니다. 특히 참조 [데이터 집합의 관계](relationships-in-datasets.md)합니다.

다음 코드 예제에서는 형식화 된 데이터 집합의 관계 위/아래로 이동 하는 방법을 보여 줍니다. 형식화 된 코드 예 사용 <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) 및 생성 된 FindBy*PrimaryKey* (`FindByCustomerID`) 메서드를 원하는 행을 찾아 관련된 레코드를 반환 합니다. 예제를 컴파일하고 있는 경우에 올바르게 실행:

- 명명 된 데이터 집합의 인스턴스에 `NorthwindDataSet` 사용 하 여를 `Customers` 테이블입니다.

- `Orders` 테이블입니다.

- 명명 된 관계 `FK_Orders_Customers`두 테이블 관련 됩니다.

또한 두 테이블 반환할 모든 레코드에 대 한 데이터를 사용 하 여 입력 해야 합니다.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>자식 선택한 부모 레코드의 레코드를 반환 하려면

- 호출 된 <xref:System.Data.DataRow.GetChildRows%2A> 특정 메서드의 `Customers` 데이터 행 및 행에서 배열을 반환 합니다 `Orders` 테이블:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>선택한 자식 레코드의 부모 레코드를 반환 합니다.

- 호출을 <xref:System.Data.DataRow.GetParentRow%2A> 특정 메서드의 `Orders` 에서 단일 행 돌아가 데이터 행을 `Customers` 테이블:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>참고자료

- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)