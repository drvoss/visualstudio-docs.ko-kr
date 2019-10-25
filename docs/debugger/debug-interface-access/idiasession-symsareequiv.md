---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741872"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
두 기호가 동일한 지 확인 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>매개 변수
 `symbolA`

진행 비교에 사용 되는 첫 번째 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다.

 `symbolB`

진행 비교에 사용 되는 두 번째 `IDiaSymbol` 개체입니다.

## <a name="return-value"></a>반환 값
 기호가 같으면 `S_OK`을 반환 하 고, 그렇지 않으면 `S_FALSE`을 반환 하 고 기호는 동일 하지 않습니다. 그렇지 않은 경우 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)