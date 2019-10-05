---
title: Tableadapter를 사용 하 여 데이터 집합 채우기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fb06c1d97c854aae05d993c086069e10e35518f5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704978"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapters를 사용하여 데이터 세트 채우기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter 구성 요소를 기반으로 쿼리 또는 저장된 프로시저 수를 지정 하는 하나 이상의 데이터베이스에서 데이터를 사용 하 여 데이터 집합을 채웁니다. Tableadapter를 수행할 수도 있습니다 추가, 업데이트 및 데이터 집합에 수행한 변경 내용을 유지 하려면 데이터베이스를 삭제 합니다. 또한 특정 테이블에 관련 되지 않은 전역 명령을 실행할 수 있습니다.  
  
> [!NOTE]
> Tableadapter는 Visual Studio 디자이너에서 생성 됩니다. 데이터 집합을 프로그래밍 방식으로 만들려는 경우에.NET Framework 클래스는 DataAdapter를 사용 합니다.  
  
 TableAdapter 작업에 대 한 자세한 내용은 다음이 항목 중 하나에 직접 건너뛸 수 있습니다.  
  
|항목|설명|  
|-----------|-----------------|  
|[TableAdapter 만들기 및 구성](../data-tools/create-and-configure-tableadapters.md)|Tableadapter 만들기 및 구성 하는 디자이너를 사용 하는 방법|  
|[매개 변수가 있는 TableAdapter 쿼리 만들기](../data-tools/create-parameterized-tableadapter-queries.md)|사용자가 인수 TableAdapter 프로시저 또는 쿼리를 제공할 수 있게 하는 방법|  
|[TableAdapter를 사용하여 데이터베이스에 직접 액세스](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Tableadapter의 Dbdirect 메서드를 사용 하는 방법|  
|[데이터 세트를 채우는 동안 제약 조건 해제](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|데이터를 업데이트할 때 foreign key 제약 조건을 사용 하는 방법|  
|[TableAdapter의 기능 확장 방법](../data-tools/fill-datasets-by-using-tableadapters.md)|Tableadapter를 사용자 지정 코드를 추가 하는 방법|  
|[XML 데이터를 데이터 세트에 읽어오기](../data-tools/read-xml-data-into-a-dataset.md)|XML을 사용 하는 방법|  
  
## <a name="tableadapters-overview"></a>TableAdapters 개요  
 Tableadapter는 데이터베이스, 쿼리 실행된 또는 저장된 프로시저를 연결 하 고 반환된 된 데이터를 사용 하 여 해당 DataTable을 채울는 디자이너에서 생성 된 구성 요소입니다. Tableadapter 다시 데이터베이스에 응용 프로그램에서 업데이트 된 데이터를 보낼 수도 있습니다. TableAdapter와 연결 된 테이블의 스키마를 따르는 데이터를 반환 하기만 TableAdapter에 원하는 만큼 많은 쿼리를 실행할 수 있습니다. 다음 다이어그램에서는 Tableadapter 데이터베이스와 메모리 내에서 기타 개체와 상호 작용 하는 방법을 보여 줍니다.  
  
 ![클라이언트 응용 프로그램에서 데이터 흐름](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 사용 하 여 Tableadapter 설계 되어는 **데이터 집합 디자이너**, TableAdapter 클래스의 중첩 클래스로 생성 되지 않습니다 <xref:System.Data.DataSet>합니다. 각 데이터 집합에 관련 된 별도 네임 스페이스에 있습니다. 예를 들어 라는 데이터 집합이 있다고 `NorthwindDataSet`, 연관 된 Tableadapter <xref:System.Data.DataTable>의 합니다 `NorthwindDataSet` 에 `NorthwindDataSetTableAdapters` 네임 스페이스입니다. 특정 TableAdapter에 프로그래밍 방식으로 액세스 하려면 TableAdapter의 새 인스턴스를 선언 해야 합니다. 예를 들어:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>DataTable 스키마와 연결된  
 TableAdapter를 만든, 초기 쿼리를 사용 하거나 TableAdapter의 스키마를 정의 하는 저장된 프로시저의 연결 된 경우 <xref:System.Data.DataTable>합니다. 이 초기 쿼리를 실행 하거나 TableAdapter의 호출 하 여 저장 프로시저 `Fill` 메서드 (연결 된 TableAdapter 채우는 <xref:System.Data.DataTable>). 연결된 된 데이터 테이블의 스키마에는 TableAdapter의 주 쿼리에 변경 내용이 반영 됩니다. 예를 들어, 연결된 된 데이터 테이블에서 열을 제거도 기본 쿼리에서 열을 제거 합니다. TableAdapter에 대 한 추가 쿼리가 기본 쿼리에 포함 하지 않은 열을 반환 하는 SQL 문을 사용 하 여, 디자이너 주 쿼리 및 추가 쿼리 간의 열 변경 내용을 동기화 하려고 합니다. 자세한 내용은 [방법: Tableadapter 편집](https://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)합니다.  
  
## <a name="tableadapter-update-commands"></a>TableAdapter 업데이트 명령  
 TableAdapter의 업데이트 기능은 TableAdapter 마법사에서 기본 쿼리에 사용할 수 있는 얼 만큼의 정보에 따라 다릅니다. 예를 들어, 여러 테이블 (조인)의 값, 스칼라 값, 뷰 또는 집계 함수의 결과 인출 하도록 구성 된 Tableadapter 처음에 기본 데이터베이스로 업데이트를 보낼 수 있는 기능을 사용 하 여 만들어지지 않습니다. 그러나 INSERT, UPDATE 및 DELETE 명령에서 수동으로 구성할 수 있습니다 합니다 **속성** 창입니다.  
  
## <a name="tableadapter-queries"></a>TableAdapter 쿼리  
 ![여러 개의 쿼리가 있는 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Tableadapter가 연결 된 데이터 테이블을 채우는 여러 쿼리를 포함할 수 있습니다. 해당 연결 된 데이터 테이블과 같은 스키마를 따르는 데이터를 반환 하는 각 쿼리도 응용 프로그램에 필요한 대로 TableAdapter에 대 한 많은 쿼리를 정의할 수 있습니다. 이 기능은 서로 다른 조건에 따라 다른 결과 로드 하려면 TableAdapter를 사용 하도록 설정 합니다.  
  
 예를 들어 고객 이름의 테이블을 포함 하는 응용 프로그램에 동일한 상태에 있는 모든 고객을 사용 하 여 테이블을 채우는 테이블을 채우는 특정 문자로 시작 하는 모든 고객 이름 및 다른 쿼리를 만들 수 있습니다. 맞게를 `Customers` 테이블 지정된 된 상태에서 고객을 만들 수 있습니다를 `FillByState` 상태 값에 대 한 매개 변수를 다음과 같이 사용 하는 쿼리: `SELECT * FROM Customers WHERE State = @State`합니다. 호출 하 여 쿼리를 실행 합니다 `FillByState` 메서드 및 매개 변수 값 전달 같이: `CustomerTableAdapter.FillByState("WA")`합니다.  
  
 TableAdapter의 데이터 테이블과 동일한 스키마의 데이터를 반환 하는 쿼리를 추가 하는 것 외에도 스칼라 (단일) 값을 반환 하는 쿼리를 추가할 수 있습니다. 고객의 수를 반환 하는 쿼리 예를 들어, (`SELECT Count(*) From Customers`)에 대 한 유효를 `CustomersTableAdapter,` 있지만 반환 되는 데이터 테이블의 스키마를 준수 하지 않습니다.  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill 속성  
 기본적으로 TableAdapter의 데이터 테이블 채우는 쿼리를 실행할 때 기존 데이터의 선택을 취소 하 고 쿼리 결과 테이블에 로드 됩니다. TableAdapter의 설정 `ClearBeforeFill` 속성을 `false` 를 추가 하 여 데이터 테이블의 기존 데이터에는 쿼리에서 반환 되는 데이터를 병합 하려는 경우. 데이터를 지우려면 여부에 관계 없이 보내야 명시적으로 업데이트를 다시 데이터베이스에 유지 하려는 경우. 따라서 테이블을 채우는 다른 쿼리를 실행 하기 전에 데이터를 테이블에 변경 내용을 저장 해야 합니다. 자세한 내용은 [TableAdapter를 사용 하 여 데이터를 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)합니다.  
  
## <a name="tableadapter-inheritance"></a>TableAdapter 상속  
 Tableadapter 구성 캡슐화 하 여 표준 데이터 어댑터의 기능을 확장 <xref:System.Data.Common.DataAdapter> 클래스? qualifyHint = False autoUpgrade = True입니다. 기본적으로 TableAdapter에서 상속 된 <xref:System.ComponentModel.Component> 클래스 및 캐스팅할 수 없는 <xref:System.Data.Common.DataAdapter> 클래스입니다. TableAdapter를 캐스팅 합니다 <xref:System.Data.Common.DataAdapter> 클래스에 결과 <xref:System.InvalidCastException> 오류? qualifyHint False autoUpgrade = = True입니다. TableAdapter의 기본 클래스를 변경 하려면에서 파생 된 클래스를 입력할 수 있습니다 <xref:System.ComponentModel.Component> 에 **기본 클래스** 에서 TableAdapter의 속성을 **데이터 집합 디자이너**합니다.  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter 메서드 및 속성  
 TableAdapter 클래스를 부분을 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]입니다. 즉, 설명서에서를 찾을 수 없습니다. 있습니다 또는 **개체 브라우저**합니다. 앞에서 언급 한 마법사 중 하나를 사용 하면 디자인 타임에 생성 됩니다. 만들 때 TableAdapter에 할당 된 이름은 사용 하는 테이블의 이름을 기반으로 합니다. 예를 들어, 명명 된 데이터베이스의 테이블을 기반으로 TableAdapter를 만들 때 `Orders`, TableAdapter 이름은 `OrdersTableAdapter`합니다. TableAdapter의 클래스 이름을 사용 하 여 변경할 수 있습니다 합니다 **이름을** 속성에는 **데이터 집합 디자이너**합니다.  
  
 다음은 일반적으로 사용 되는 메서드 및 Tableadapter의 속성입니다.  
  
|멤버|설명|  
|------------|-----------------|  
|`TableAdapter.Fill`|TableAdapter의 SELECT 명령의 결과 사용 하 여 TableAdapter의 연결 된 데이터 테이블을 채웁니다.|  
|`TableAdapter.Update`|변경 내용을 다시 데이터베이스에 보내고 업데이트에 의해 영향을 받는 행 수를 나타내는 정수를 반환 합니다. 자세한 내용은 [TableAdapter를 사용 하 여 데이터를 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)합니다.|  
|`TableAdapter.GetData`|반환 된 새 <xref:System.Data.DataTable> 는 데이터로 채워집니다.|  
|`TableAdapter.Insert`|데이터 테이블에 새 행을 만듭니다. 자세한 내용은 [데이터베이스에 새 레코드 삽입](../data-tools/insert-new-records-into-a-database.md)합니다.|  
|`TableAdapter.ClearBeforeFill`|데이터 테이블 중 하나를 호출 하기 전에 비어 있는지 여부를 결정 합니다 `Fill` 메서드.|  
  
## <a name="tableadapter-update-method"></a>TableAdapter 업데이트 메서드  
 Tableadapter에 대 한 읽기 및 쓰기 데이터베이스에서 데이터 명령을 사용 합니다. TableAdapter의 첫 `Fill` (main) 쿼리는 연결 된 데이터 테이블의 스키마를 만들기 위한 기초로 사용 뿐만 `InsertCommand`를 `UpdateCommand`, 및 `DeleteCommand` 연관 된 명령을 `TableAdapter.Update` 메서드. TableAdapter의 호출 `Update` 사용 하 여 추가 된 추가 쿼리 중 하나가 아닙니다 메서드 실행 문은 TableAdapter를 원래 때 생성 된 구성의 **TableAdapter 쿼리 구성 마법사**.  
  
 TableAdapter를 사용 하면 효과적으로 일반적으로 수행 하는 명령 사용 하 여 동일한 작업을 수행 합니다. 예를 들어, 호출 하는 경우 어댑터의 `Fill` 메서드는 어댑터에서 실행 됩니다 데이터 명령을 해당 `SelectCommand` 속성 데이터 판독기를 사용 하 고 (예를 들어 <xref:System.Data.SqlClient.SqlDataReader>) 결과 집합을 데이터 테이블에 로드 합니다. 마찬가지로, 호출 하는 경우 어댑터의 `Update` 메서드를 적절 한 명령을 실행 (에 `UpdateCommand`를 `InsertCommand`, 및 `DeleteCommand` 속성) 각각에 대 한 데이터 테이블의 레코드를 변경 합니다.  
  
> [!NOTE]
> 기본 쿼리에서 충분 한 정보가 있는 경우는 `InsertCommand`, `UpdateCommand`, 및 `DeleteCommand` 명령을 TableAdapter를 생성할 때 기본적으로 생성 됩니다. TableAdapter의 주 쿼리에서 단일 테이블 SELECT 문을 보다 경우 디자이너를 생성할 수 없습니다 `InsertCommand`하십시오 `UpdateCommand`, 및 `DeleteCommand`합니다. 이러한 명령은 생성 되지 않은 경우 오류가 발생할 수 있습니다를 실행 하는 경우는 `TableAdapter.Update` 메서드.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 외에 `InsertCommand`, `UpdateCommand`, 및 `DeleteCommand`, Tableadapter는 데이터베이스에 대해 직접 실행할 수 있는 메서드를 사용 하 여 만들어집니다. 이러한 메서드 (`TableAdapter.Insert`, `TableAdapter.Update`, 및 `TableAdapter.Delete`) 데이터베이스의 데이터를 조작 하는 직접 호출할 수 있습니다. 즉, 호출 하는 대신 코드에서 이러한 개별 메서드를 호출할 수 있습니다 `TableAdapter.Update` 삽입, 업데이트 및 보류 중인 삭제를 처리 하는 연결 된 데이터 테이블에 대 한 합니다.  
  
 이러한 직접 메서드를 만드는 않으려면 TableAdapter의 설정 **GenerateDbDirectMethods** 속성을 `false` (에 **속성** 창). TableAdapter에 추가 되는 추가 쿼리는 독립 실행형-이러한 메서드를 생성 하지는 않습니다.  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter nullable 형식 지원  
 Tableadapter에 nullable 형식 지원 `Nullable(Of T)` 고 `T?`입니다. Visual Basic의 nullable 형식에 대한 자세한 내용은 [Nullable 값 형식](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)을 참조하세요. C#의 nullable 형식에 대 한 자세한 내용은 참조 하세요. [Nullable 형식 사용](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)합니다.  
  
## <a name="security"></a>보안  
 데이터 명령을 사용 하는 경우는 `CommandType` 속성이 설정 <xref:System.Data.CommandType>, 신중 하 게 데이터베이스에 전달 하기 전에 클라이언트에서 전송 되는 정보를 확인 합니다. 악의적인 사용자가 인증되지 않은 액세스 권한을 얻거나 데이터베이스를 손상시키기 위해 수정되었거나 추가된 SQL 문을 전송(주입)할 수도 있습니다. 데이터베이스에 사용자 입력을 전송 하기 전에 항상 정보가 유효한 지 확인 합니다. 매개 변수가 있는 쿼리 또는 저장된 프로시저를 가능 하면 항상 사용 하는 것이 좋습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
