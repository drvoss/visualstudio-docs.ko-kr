---
title: '방법: 단일 값을 반환 하는 SQL 문 만들기 및 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7d5d57637a25db62832ad535bbad60214a0aa4ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192155"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>방법: 단일 값을 반환하는 SQL 문 만들기 및 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

단일 값을 반환 하는 SQL 문을 실행 하려면 SQL 문을 실행 하도록 구성 된 TableAdapter 쿼리를 실행할 수 있습니다 (예를 들어 `CustomersTableAdapter.CustomerCount()`).  
  
 응용 프로그램에서 Tableadapter를 사용 하는 경우 호출 된 `ExecuteScalar` 메서드를 설정 하는 명령 개체를 해당 `CommandType` 속성을 <xref:System.Data.CommandType>. ("명령 개체"에 대 한 특정 명령에 참조를 [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) 응용 프로그램에서 사용 합니다. 예를 들어 응용 프로그램을 사용 중인 경우.NET Framework Data Provider for SQL Server 명령 개체 것 <xref:System.Data.SqlClient.SqlCommand>.)  
  
 다음 예에서는 명령 개체 또는 Tableadapter를 사용 하 여 데이터베이스에서 단일 값을 반환 하는 SQL 문을 실행 하는 방법을 보여 줍니다. Tableadapter 및 명령을 사용 하 여 쿼리에 대 한 자세한 내용은 참조 하세요. [Tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)합니다.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>TableAdapter를 사용 하 여 단일 값을 반환 하는 SQL 문 실행  
 사용 하 여 TableAdapter 쿼리를 만드는 방법을 보여 주는이 예제는 [Tableadapter 편집](../data-tools/editing-tableadapters.md), TableAdapter의 인스턴스를 선언 하 고 쿼리를 실행 하는 방법에 정보를 제공 합니다.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>TableAdapter를 사용 하 여 단일 값을 반환 하는 SQL 문을 만들려면  
  
1.  데이터 집합을 엽니다는 **데이터 집합 디자이너**합니다. 자세한 내용은 [방법: 데이터 집합 디자이너에서 데이터 집합 열기](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)합니다.  
  
2.  수 없는 하나, 경우에 TableAdapter를 만듭니다. Tableadapter를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [만들기 및 Tableadapter 구성](../data-tools/create-and-configure-tableadapters.md)합니다.  
  
3.  단일 값을 반환 하는 SQL 문을 사용 하 여 TableAdapter에 쿼리를 이미 있는 경우 다음 TableAdapter의 인스턴스를 선언 하 고 쿼리를 실행 합니다.""에 다음 절차를 건너뛸 그렇지 않으면 4 단일 값을 반환 하는 새 쿼리를 만드는 단계를 사용 하 여 계속 합니다.  
  
4.  원하는 TableAdapter를 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴를 사용 하 여 쿼리를 추가 합니다.  
  
     합니다 **TableAdapter 쿼리 구성 마법사** 열립니다.  
  
5.  기본값을 그대로 둡니다 **사용 하 여 SQL 문을**를 클릭 하 고 **다음**합니다.  
  
6.  선택 된 **단일 값을 반환 하는 SELECT** 옵션을 선택한 다음 클릭 **다음**합니다.  
  
7.  SQL 문을 입력 하거나 사용 합니다 **쿼리 작성기** 하 여 만들고, 누른 **다음**.  
  
8.  쿼리에 대 한 이름을 제공 합니다.  
  
9. 마법사를 완료 합니다. 쿼리는 TableAdapter에 추가 됩니다.  
  
10. 프로젝트를 빌드합니다.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>TableAdapter의 인스턴스를 선언 하 고 쿼리를 실행 하려면  
  
1.  실행 하려는 쿼리를 포함 하는 TableAdapter의 인스턴스를 선언 합니다.  
  
    -   원하는 TableAdapter를 끌어 디자인 타임 도구를 사용 하 여 인스턴스를 만들려고 합니다 **도구 상자**합니다. (프로젝트의 구성 요소에 표시 된 **도구 상자** 프로젝트 이름과 일치 하는 머리글 아래.) TableAdapter에 나타나지 않으면 합니다 **도구 상자**, 프로젝트를 빌드하려면 해야 할 수 있습니다.  
  
         또는  
  
    -   코드에서 인스턴스를 만들려면 다음 코드의 이름으로 대체 하 <xref:System.Data.DataSet> 및 TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  해당 연결 된 데이터 집합 클래스 내에서 Tableadapter 실제로 있는 것은 아닙니다. 각 데이터 집합에는 자체 네임 스페이스에 Tableadapter의 해당 컬렉션을 있습니다. 예를 들어 라는 데이터 집합이 있다고 `SalesDataSet`, 있습니다 다음을 `SalesDataSetTableAdapters` 해당 Tableadapter를 포함 하는 네임 스페이스입니다.  
  
2.  코드에서 다른 메서드를 호출 하는 것 처럼 쿼리를 호출 합니다. 쿼리는 TableAdapter의 메서드입니다. 다음 코드를 쿼리 및 TableAdapter의 이름을 바꿉니다. 쿼리에 필요한 모든 매개 변수를 전달 및 반환 값을 사용 하 여 작업을 수행 해야 (예를 들어 할당할 변수). 쿼리 매개 변수가 필요한 경우 확실 하지 않은 경우 다음 필요한 매개 변수 쿼리 필요한 서명에 대 한 IntelliSense를 확인 합니다. 쿼리 매개 변수를 사용 하는지 여부에 따라 코드를 다음 예제 중 하 나와 비슷하게 보입니다.  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  가능성이 변수로 쿼리에 의해 반환 된 값을 할당 해야 합니다. 단일 값을 반환 하는 TableAdapter 쿼리는 쿼리를 기반으로 데이터 형식을 반환 (아닌 사이트별로 `ExecuteScalar` 개체를 반환 하는 메서드). 예를 들어 데이터 형식이 정수가 단일 열을 선택 하는 TableAdapter 쿼리 경우 쿼리의 반환 값은 정수입니다. 열의 null 값을 허용 하는 경우 반환 값은 nullable 형식 중 하나 (예를 들어 `Nullable(Of Integer)`). Nullable 형식에 대 한 자세한 내용은 참조 하세요. <xref:System.Nullable>합니다. TableAdapter의 인스턴스를 선언 하 고 쿼리를 실행 하는 코드 전체 다음과 비슷하게 표시 됩니다 (이 예에서는 가정 반환 값은 정수; 쿼리에서 반환 되는 데이터 형식에 따라 코드 조정):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>명령 개체를 사용 하 여 단일 값을 반환 하는 SQL 문 실행  
 다음 예제에서는 명령을 만들고 단일 값을 반환 하는 SQL 문을 실행 하는 방법을 보여 줍니다. 설정 및 명령의 매개 변수 값을 가져오기에 대 한 내용은 참조 하세요 [방법: 집합 및 명령 개체에 대 한 매개 변수 가져오기](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)합니다.  
  
 이 예제에서는 <xref:System.Data.SqlClient.SqlCommand> 하며 개체:  
  
-   에 대 한 참조를 <xref:System>, <xref:System.Data>, 및 <xref:System.Xml> 네임 스페이스입니다.  
  
-   명명 된 데이터 연결을 `SqlConnection1`입니다.  
  
-   라는 테이블 `Customers` 원본의 데이터에 `SqlConnection1` 에 연결 합니다. (이 고, 그렇지 해야 유효한 SQL 문을 데이터 원본에 대 한).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>DataCommand를 사용 하 여 단일 값을 반환 하는 SQL 문을 실행 하려면  
  
-   코드를 실행 하려는 메서드에 다음 코드를 추가 합니다. 호출 하 여 단일 값을 반환 합니다 `ExecuteScalar` 명령의 메서드 (예를 들어 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). 데이터가 반환 되는 <xref:System.Object>합니다.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>.NET Framework 보안  
 응용 프로그램 데이터베이스에 액세스 하 고 SQL 문을 실행할 수 있는 권한이 필요 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [방법: TableAdapter 쿼리 만들기](../data-tools/how-to-create-tableadapter-queries.md)   
 [방법: TableAdapter 쿼리 편집](../data-tools/how-to-edit-tableadapter-queries.md)   
 [방법: 데이터 집합을 데이터로 채우기](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [방법: 명령 개체에 대 한 매개 변수를 가져와 설정](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)