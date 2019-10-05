---
title: 데이터베이스에 새 레코드 삽입
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 64fc4735fd95c611dd1c2d905be6fa5b45c84664
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715024"
---
# <a name="insert-new-records-into-a-database"></a>데이터베이스에 새 레코드 삽입

데이터베이스에 새 레코드를 삽입을 사용할 수 있습니다 합니다 `TableAdapter.Update` 메서드 또는 TableAdapter의 DBDirect 메서드 중 하나 (특히는 `TableAdapter.Insert` 메서드). 자세한 내용은 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)합니다.

응용 프로그램에서 Tableadapter를 사용 하지 않는 경우 명령 개체를 사용할 수 있습니다 (예를 들어 <xref:System.Data.SqlClient.SqlCommand>) 데이터베이스에서 새 레코드를 삽입 합니다.

사용 하 여 응용 프로그램에서는 데이터 집합 데이터를 저장 하는 경우는 `TableAdapter.Update` 메서드. `Update` 메서드는 데이터베이스에 모든 변경 내용 (업데이트, 삽입 및 삭제)를 보냅니다.

응용 프로그램 개체를 사용 하 여 데이터를 저장 하거나 데이터베이스에 새 레코드를 만드는 보다 세부적으로 제어 하려는 경우 사용 하는 경우는 `TableAdapter.Insert` 메서드.

TableAdapter에 없는 경우는 `Insert` 메서드를 의미 하거나 TableAdapter 저장된 프로시저를 사용 하도록 구성 되어 있는지 또는 해당 `GenerateDBDirectMethods` 속성이 `false`합니다. TableAdapter의 설정 해 보십시오 `GenerateDBDirectMethods` 속성을 `true` 내에서 **데이터 집합 디자이너**, 다음 데이터 집합을 저장 합니다. 이렇게 하면 TableAdapter 다시 생성 됩니다. TableAdapter 아직 없는 경우는 `Insert` 메서드는 표를 제공 하지 않게 개별 행을 구분 하기 위해 충분 한 스키마 정보 (예를 들어 있을 수 있습니다 테이블에 기본 키 설정 없음).

## <a name="insert-new-records-by-using-tableadapters"></a>Tableadapter를 사용 하 여 새 레코드를 삽입 합니다.

Tableadapter에는 응용 프로그램의 요구 사항에 따라 데이터베이스에 새 레코드를 삽입 하는 다른 방법을 제공 합니다.

응용 프로그램에서는 데이터 집합 데이터를 저장 하는 경우 있습니다 단순히 새 레코드를 추가 하면 원하는 <xref:System.Data.DataTable> 데이터 집합 및 호출에는 `TableAdapter.Update` 메서드. `TableAdapter.Update` 메서드 내용을 보냅니다는 <xref:System.Data.DataTable> (수정 및 삭제 된 레코드를 포함 하 여) 데이터베이스에 있습니다.

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter.Update 메서드를 사용 하 여 데이터베이스에 새 레코드를 삽입 하려면

1. 원하는에 새 레코드를 추가 <xref:System.Data.DataTable> 새 <xref:System.Data.DataRow> 에 추가 하 여 <xref:System.Data.DataTable.Rows%2A> 컬렉션입니다.

2. 새 행에 추가 된 후의 <xref:System.Data.DataTable>를 호출 합니다 `TableAdapter.Update` 메서드. 전체에서 전달 하 여 업데이트 하는 데이터의 양을 제어할 수 있습니다 <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, 배열을 <xref:System.Data.DataRow>s, 단일 <xref:System.Data.DataRow>합니다.

   다음 코드는 새 레코드를 추가 하는 방법을 보여 줍니다는 <xref:System.Data.DataTable> 호출을 `TableAdapter.Update` 데이터베이스에 새 행을 저장 하는 방법입니다. (이 예제에서는 `Region` Northwind 데이터베이스의 테이블입니다.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter.Insert 메서드를 사용 하 여 데이터베이스에 새 레코드를 삽입 하려면

개체를 사용 하 여 데이터를 저장 하는 응용 프로그램을 사용할 수 있습니다는 `TableAdapter.Insert` 데이터베이스에 직접 새 행을 만드는 방법. `Insert` 메서드 매개 변수로 각 열에 대 한 개별 값을 받아들입니다. 데이터베이스에 전달 되는 매개 변수 값을 사용 하 여 새 레코드를 삽입 메서드를 호출 합니다.

- TableAdapter의 호출 `Insert` 메서드를 매개 변수로 각 열에 대 한 값을 전달 합니다.

다음 절차를 사용 하 여 하는 방법을 보여 줍니다는 `TableAdapter.Insert` 행을 삽입 하는 방법입니다. 데이터를 삽입 하는이 예제는 `Region` Northwind 데이터베이스의 테이블입니다.

> [!NOTE]
> 인스턴스에 사용할 수 없는 경우 사용 하려는 TableAdapter를 인스턴스화하십시오.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>명령 개체를 사용 하 여 새 레코드를 삽입 합니다.

명령 개체를 사용 하 여 데이터베이스에 직접 새 레코드를 삽입할 수 있습니다.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>명령 개체를 사용 하 여 데이터베이스에 새 레코드를 삽입 하려면

- 새 명령 개체를 만들고 설정한 해당 `Connection`, `CommandType`, 및 `CommandText` 속성입니다.

다음 예에서는 명령 개체를 사용 하 여 데이터베이스에 레코드 삽입을 보여 줍니다. 데이터를 삽입 합니다 `Region` Northwind 데이터베이스의 테이블입니다.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>.NET 보안

연결 하려는 데이터베이스 뿐만 아니라 원하는 테이블에 삽입을 수행할 수 있는 권한이 있는 사용 권한이 있어야 합니다.

## <a name="see-also"></a>참고자료

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)