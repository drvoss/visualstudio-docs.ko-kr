---
title: 'IDiaSymbol:: get_bitPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_bitPosition method
ms.assetid: b0059407-8655-497b-81ca-025595989371
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 709bb7e57ee6260ffcd7d8b1421526d3dd41052a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740901"
---
# <a name="idiasymbolget_bitposition"></a>IDiaSymbol::get_bitPosition
위치의 비트 위치를 검색 합니다. [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 이 `LocIsBitField` 때 사용 됩니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_bitPosition ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 위치의 비트 위치를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v7.0|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)