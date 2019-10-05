---
title: 트랜잭션을 사용 하 여 데이터 저장 | Microsoft Docs
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
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93c512bafd8b15682ed081c7778660ef52fd1f7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692497"
---
# <a name="save-data-by-using-a-transaction"></a>트랜잭션을 사용하여 데이터 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 하 여 트랜잭션에서 데이터를 저장 합니다 <xref:System.Transactions> 네임 스페이스입니다. 사용 된 <xref:System.Transactions.TransactionScope> 개체를 자동으로 관리 되는 트랜잭션에 참여할 수 있습니다.  
  
 트랜잭션을 사용 하는 프로젝트에 대 한 참조를 수동으로 추가 해야 하므로 프로젝트에서 System.Transactions 어셈블리에 대 한 참조를 사용 하 여 생성 되지 않습니다.  
  
> [!NOTE]
> <xref:System.Transactions> 네임 스페이스는 Windows 2000 이상에서 지원 됩니다.  
  
 인스턴스화하는 가장 쉬운 방법은 트랜잭션을 구현 하는 것을 <xref:System.Transactions.TransactionScope> 개체는 `using` 문입니다. (자세한 내용은 [Using 문](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), 및 [문을 사용 하 여](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) 내에서 실행 되는 코드는 `using` 문을 트랜잭션에 참여 합니다.  
  
 트랜잭션을 커밋하려면 호출을 <xref:System.Transactions.TransactionScope.Complete%2A> 마지막 문으로 사용 하 여 메서드를 차단 합니다.  
  
 트랜잭션을 롤백하려면를 호출 하기 전에 예외를 throw 합니다 <xref:System.Transactions.TransactionScope.Complete%2A> 메서드.  
  
 자세한 내용은 [트랜잭션에 데이터 저장](../data-tools/save-data-in-a-transaction.md)합니다.  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>System.Transactions dll에 대 한 참조를 추가 하려면  
  
1. **프로젝트** 메뉴에서 **참조 추가**를 선택합니다.  
  
2. 에 **.NET** 탭 (**SQL Server** SQL Server 프로젝트에 대 한 탭)을 선택 **System.Transactions**를 선택한 후 **확인**합니다.  
  
     System.Transactions.dll에 대 한 참조를 프로젝트에 추가 됩니다.  
  
### <a name="to-save-data-in-a-transaction"></a>트랜잭션에서 데이터를 저장 하려면  
  
- 내에서 데이터를 저장 하는 코드를 추가 합니다. 트랜잭션을 포함 하는 문입니다. 다음 코드를 만들고 인스턴스화하는 방법을 보여 줍니다는 <xref:System.Transactions.TransactionScope> 개체를 사용 하 여 문:  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>참고 항목  
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
