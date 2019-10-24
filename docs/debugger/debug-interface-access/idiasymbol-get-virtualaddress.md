---
title: 'IDiaSymbol:: get_virtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualAddress method
ms.assetid: dc20c7c0-15a6-4b78-a5c9-2e0b94cac522
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee1c5e989c4e4d9937fad4ba23c261437b4009b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738903"
---
# <a name="idiasymbolget_virtualaddress"></a>IDiaSymbol::get_virtualAddress
위치의 VA (가상 주소)를 검색 합니다. [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 이 `LocIsStatic`로 설정 된 경우를 사용 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 위치의 가상 주소를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)