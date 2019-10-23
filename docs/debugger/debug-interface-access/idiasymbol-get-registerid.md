---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739459"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 이 `LocIsEnregistered`로 설정 된 경우 위치의 등록 지정자를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 위치의 등록 지정자를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
 기호가 레지스터를 기준으로 하는 경우, 즉 기호의 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 이 `LocIsRegRel`로 설정 된 경우에는 `get_registerId` 메서드를 사용 하 여 [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) 메서드에 대 한 호출을 수행 합니다. 여기서 기호는 배치할.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)