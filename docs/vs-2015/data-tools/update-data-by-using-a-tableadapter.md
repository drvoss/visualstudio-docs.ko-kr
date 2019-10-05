---
title: TableAdapter를 사용 하 여 데이터를 업데이트 합니다. | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30d1fd3ee211d6b30f435104a2e2f9b42ed100c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692339"
---
# <a name="update-data-by-using-a-tableadapter"></a>TableAdapter를 사용하여 데이터 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 집합의 데이터를 수정 하 고 유효성을 검사 된 후 databaseby 호출을 다시 업데이트 된 데이터를 보낼 수 있습니다는 `Update` TableAdapter의 메서드. `Update` 메서드는 단일 데이터 테이블을 업데이트 하 고 올바른 명령을 (INSERT, UPDATE 또는 DELETE)에 따라 실행을 <xref:System.Data.DataRow.RowState%2A> 테이블의 각 데이터 행입니다. 데이터 집합에 관련 테이블, Visual Studio는 업데이트를 수행 하는 데 사용할 수 있는 TableAdapterManager 클래스를 생성 합니다. TableAdapterManager 클래스는 데이터베이스에 정의 된 외래 키 제약 조건에 따라 올바른 순서로 업데이트를 확인 합니다. 데이터 바인딩된 컨트롤을 사용 하면 데이터 바인딩 아키텍처 tableAdapterManager 호출 되는 TableAdapterManager 클래스의 멤버 변수를 만듭니다. 자세한 내용은 [계층적 업데이트 개요](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)합니다.  
  
> [!NOTE]
> 데이터 집합의 콘텐츠를 사용 하 여 데이터 소스를 업데이트 하려고 할 때 오류를 가져올 수 있습니다. 오류를 방지 하려면 thatyou 어댑터를 호출 하는 코드를 배치 권장 `Update` 내에서 메서드를 `try` / `catch` 블록입니다.  
  
 데이터 소스를 업데이트 하기 위한 정확한 절차는 비즈니스 요구 사항에 따라 달라질 수 있지만 다음 단계가 포함 됩니다.  
  
1. 어댑터의 호출 `Update` 의 메서드를 `try` / `catch` 블록입니다.  
  
2. 예외가 포착 되는 경우 오류를 발생 시키는 데이터 행을 찾습니다. 자세한 내용은 [방법: 오류가 있는 행 찾기](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c)합니다.  
  
3. 데이터의 문제 (가능한 경우 프로그래밍 방식으로 또는 수정에 대 한 사용자에 게 잘못 된 행을 제공 하 여) 행을 한 다음 다시 업데이트 (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="savedata-to-a-database"></a>Savedata 데이터베이스로  
 호출 된 `Update` TableAdapter의 메서드. 데이터베이스에 쓸 값이 포함 된 데이터 테이블의 이름을 전달 하세요.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>TableAdapter를 사용 하 여 데이터베이스를 업데이트 하려면  
  
- TableAdapter의 묶습니다`Update` 의 메서드를 `try` / `catch` 블록입니다. 다음 예제에서는의 내용을 업데이트 하는 방법을 보여 줍니다 합니다 `Customers` 테이블의 `NorthwindDataSet` 내에서 `try` / `catch` 블록입니다.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>참고 항목  
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
