---
title: 'IDiaSymbol:: get_dataBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79c14427e967736b0dbe1ddb235f9e90b3ecc10f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740720"
---
# <a name="idiasymbolget_databytes"></a>IDiaSymbol::get_dataBytes
OEM 기호의 데이터 바이트를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_dataBytes ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>매개 변수
 `cbData`

진행 데이터를 보관할 버퍼의 크기입니다.

 `pcbData`

제한이 쓴 바이트 수를 반환 하거나 `data` 매개 변수가 `NULL` 경우 사용 가능한 바이트 수를 반환 합니다.

 `data[]`
- [out,] 데이터 바이트를 사용 하 여 채워진 버퍼입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v7.0|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)