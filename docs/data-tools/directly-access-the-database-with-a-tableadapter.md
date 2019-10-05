---
title: TableAdapter를 사용하여 데이터베이스에 직접 액세스
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 26bcab8d589c1fedcbbc4eb1f8b06bb1c04cac53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567024"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>TableAdapter를 사용하여 데이터베이스에 직접 액세스

외에 `InsertCommand`, `UpdateCommand`, 및 `DeleteCommand`, Tableadapter는 데이터베이스에 대해 직접 실행할 수 있는 메서드를 사용 하 여 만들어집니다. 이러한 메서드를 호출할 수 있습니다 (`TableAdapter.Insert`, `TableAdapter.Update`, 및 `TableAdapter.Delete`) 데이터베이스에서 직접 데이터를 조작 합니다.

이러한 직접 메서드를 만드는 않으려면 TableAdapter의 설정 `GenerateDbDirectMethods` 속성을 `false` 에 **속성** 창입니다. 이 생성 하지 않는 독립 실행형 쿼리는 TableAdapter의 기본 쿼리 외에도 TableAdapter에 쿼리를 추가 하는 경우 `DbDirect` 메서드.

## <a name="send-commands-directly-to-a-database"></a>명령을 데이터베이스로 직접 보내는

TableAdapter 호출 `DbDirect` 수행 하려는 작업을 수행 하는 메서드입니다.

### <a name="to-insert-new-records-directly-into-a-database"></a>데이터베이스에 직접 새 레코드를 삽입 하려면

- TableAdapter의 호출 `Insert` 메서드를 매개 변수로 각 열에 대 한 값을 전달 합니다. 다음 절차에서는 `Region` 예를 들어 Northwind 데이터베이스의 테이블입니다.

    > [!NOTE]
    > 인스턴스에 사용할 수 없는 경우 사용 하려는 TableAdapter를 인스턴스화하십시오.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>데이터베이스에서 직접 레코드를 업데이트 하려면

- TableAdapter의 호출 `Update` 메서드를 매개 변수로 각 열에 대 한 새 및 원래 값을 전달 합니다.

    > [!NOTE]
    > 인스턴스에 사용할 수 없는 경우 사용 하려는 TableAdapter를 인스턴스화하십시오.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>데이터베이스에서 직접 레코드를 삭제 하려면

- TableAdapter의 호출 `Delete` 의 매개 변수로 각 열에 대 한 값을 전달 하는 메서드를 `Delete` 메서드. 다음 절차에서는 `Region` 예를 들어 Northwind 데이터베이스의 테이블입니다.

    > [!NOTE]
    > 인스턴스에 사용할 수 없는 경우 사용 하려는 TableAdapter를 인스턴스화하십시오.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>참고자료

- [TableAdapter를 사용하여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)