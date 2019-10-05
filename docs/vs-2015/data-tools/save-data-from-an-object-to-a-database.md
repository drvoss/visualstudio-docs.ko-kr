---
title: 데이터베이스 개체에서 데이터를 저장 | Microsoft Docs
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
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c079d3f85dbab87e30edb059c76202dd727f715c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425057"
---
# <a name="save-data-from-an-object-to-a-database"></a>개체에서 데이터베이스로 데이터 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter의 DBDirect 메서드 중 하나에 개체에서 값을 전달 하 여 데이터베이스 개체에서 데이터를 저장할 수 있습니다 (예를 들어 `TableAdapter.Insert`).
  
 개체의 컬렉션에서 데이터를 저장 하려면 개체 (예를 들어, 다음에 대 한 루프의 경우)의 컬렉션을 반복 하 고 TableAdapter의 DBDirect 메서드 중 하나를 사용 하 여 데이터베이스에 각 개체에 대 한 값을 보냅니다.  
  
 기본적으로 데이터베이스에 대해 직접 실행할 수 있는 TableAdapter의 DBDirect 메서드 생성 됩니다. 이러한 메서드는 직접 호출할 수 있습니다 하 고 필요 하지 않습니다 <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable> 내용을 데이터베이스에 업데이트를 전송 하기 위해 조정 하는 개체입니다.  
  
> [!NOTE]
> TableAdapter를 구성 하는 경우 주 쿼리의 DBDirect 메서드를 만들 수에 대 한 충분 한 정보를 제공 해야 합니다. 예를 들어 TableAdapter를 정의 하는 기본 키 열이 없는 테이블에서 데이터를 쿼리 하 구성 된 경우 DBDirect 메서드 생성 하지 않습니다.  
  
|TableAdapter DBDirect 메서드|설명|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|데이터베이스에 새 레코드를 추가 하 고 개별 열 값을 메서드 매개 변수로 전달할 수 있습니다.|  
|`TableAdapter.Update`|기존 데이터베이스에서 레코드를 업데이트 합니다. `Update` 메서드는 원래 및 새 열 값을 메서드 매개 변수로 사용 합니다. 원래 값을 원래 레코드를 찾는 데 사용 되 고 새 값은 해당 레코드를 업데이트 하는 데 사용 됩니다.<br /><br /> 합니다 `TableAdapter.Update` 메서드는 또한 수행 하 여 데이터 집합의 변경 내용을 데이터베이스로 다시 조정 하는 데 사용 됩니다는 <xref:System.Data.DataSet>를 <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, 또는 배열을 <xref:System.Data.DataRow>메서드 매개 변수로 합니다.|  
|`TableAdapter.Delete`|메서드 매개 변수로 전달 되는 원래 열 값에 따라 데이터베이스에서 기존 레코드를 삭제 합니다.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>데이터베이스 개체에서 새 레코드를 저장 하려면  
  
- 값을 전달 하 여 레코드를 만들어야 합니다 `TableAdapter.Insert` 메서드.  
  
     다음 예제에서 새 고객 레코드를 만듭니다는 `Customers` 의 값을 전달 하 여 테이블의 `currentCustomer` 개체를 `TableAdapter.Insert` 메서드.  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>데이터베이스 개체에서 기존 레코드를 업데이트 하려면  
  
- 호출 하 여 레코드를 수정 합니다 `TableAdapter.Update` 메서드, 레코드를 업데이트 하려면 새 값을 전달 하 고 레코드를 찾고 원래 값을 전달 합니다.  
  
    > [!NOTE]
    > 개체를 전달할 수 있도록 원래 값을 유지 해야 하는 경우는 `Update` 메서드. 사용 하 여 속성을 사용 하 여이 예제는 `orig` 원래 값을 저장 하는 접두사입니다.  
  
     기존 레코드를 업데이트 하는 다음 예제는 `Customers` 테이블에서 새 및 원래 값을 전달 하 여는 `Customer` 개체는 `TableAdapter.Update` 메서드.  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>데이터베이스에서 기존 레코드를 삭제 하려면  
  
- 호출 하 여 레코드를 삭제 하는 `TableAdapter.Delete` 메서드와 레코드를 찾고 원래 값을 전달 합니다.  
  
    > [!NOTE]
    > 개체를 전달할 수 있도록 원래 값을 유지 해야 하는 경우는 `Delete` 메서드. 사용 하 여 속성을 사용 하 여이 예제는 `orig` 원래 값을 저장 하는 접두사입니다.  
  
     레코드를 삭제 하는 다음 예제는 `Customers` 테이블의 원래 값을 전달 하 여는 `Customer` 개체를 `TableAdapter.Delete` 메서드.  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>.NET Framework 보안  
 선택한 삽입을 수행할 수 있는 권한이 있어야 합니다. 업데이트 또는 데이터베이스의 테이블에서 삭제 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
