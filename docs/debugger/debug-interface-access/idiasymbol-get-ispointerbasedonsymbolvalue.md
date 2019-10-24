---
title: 'IDiaSymbol:: get_isPointerBasedOnSymbolValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a7e7546454ddb60babff757f86aab023ce5bb7d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740135"
---
# <a name="idiasymbolget_ispointerbasedonsymbolvalue"></a>IDiaSymbol::get_isPointerBasedOnSymbolValue
@No__t_0 포인터가 기호 값을 기반으로 하는지 여부를 지정 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_isPointerBasedOnSymbolValue(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 @No__t_1 포인터가 기호 값을 기반으로 하는지 여부를 지정 하는 `BOOL`에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)