---
title: '방법: 트랜잭션을 사용하여 데이터 저장'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bf5864d25e78b6050da5c13097503b2998dda44a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566318"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>방법: 트랜잭션을 사용하여 데이터 저장

사용 하 여 트랜잭션에서 데이터를 저장 합니다 <xref:System.Transactions> 네임 스페이스입니다. 사용 된 <xref:System.Transactions.TransactionScope> 개체를 자동으로 관리 되는 트랜잭션에 참여할 수 있습니다.

프로젝트에 대 한 참조를 사용 하 여 만들어지지 합니다 *System.Transactions* 어셈블리를 수동으로 트랜잭션을 사용 하는 프로젝트에 대 한 참조를 추가 해야 합니다.

인스턴스화하는 가장 쉬운 방법은 트랜잭션을 구현 하는 것을 <xref:System.Transactions.TransactionScope> 개체는 `using` 문입니다. (자세한 내용은 [문을 사용 하 여](/dotnet/visual-basic/language-reference/statements/using-statement), 및 [문을 사용 하 여](/dotnet/csharp/language-reference/keywords/using-statement).) 내에서 실행 되는 코드는 `using` 문을 트랜잭션에 참여 합니다.

트랜잭션을 커밋하려면 호출을 <xref:System.Transactions.TransactionScope.Complete%2A> 마지막 문으로 사용 하 여 메서드를 차단 합니다.

트랜잭션을 롤백하려면를 호출 하기 전에 예외를 throw 합니다 <xref:System.Transactions.TransactionScope.Complete%2A> 메서드.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System.Transactions.dll에 대 한 참조를 추가 하려면

1. **프로젝트** 메뉴에서 **참조 추가**를 선택합니다.

2. 에 **.NET** 탭 (**SQL Server** SQL Server 프로젝트에 대 한 탭)을 선택 **System.Transactions**를 선택한 후 **확인**합니다.

     에 대 한 참조가 *System.Transactions.dll* 프로젝트에 추가 됩니다.

## <a name="to-save-data-in-a-transaction"></a>트랜잭션에서 데이터를 저장 하려면

- 내에서 데이터를 저장 하는 코드를 추가 합니다. 트랜잭션을 포함 하는 문입니다. 다음 코드를 만들고 인스턴스화하는 방법을 보여 줍니다는 <xref:System.Transactions.TransactionScope> 개체를 사용 하 여 문:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>참고자료

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
- [연습: 트랜잭션에 데이터 저장](../data-tools/save-data-in-a-transaction.md)