---
title: 'IDiaSymbol:: get_liveRangeStartRelativeVirtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea82e9d1dee4b82e78ea3f6409acfdcfc30b2a27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739886"
---
# <a name="idiasymbolget_liverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
로컬 기호가 유효한 주소 범위의 시작을 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_liveRangeStartRelativeVirtualAddress ( 
   DWORD* address
);
```

#### <a name="parameters"></a>매개 변수
 `address`

제한이 주소 범위의 시작을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 반환 된 상대 가상 주소는 기호가 유효한 범위의 시작 부분입니다.

> [!NOTE]
> 반환 된 오류 코드는 기호에 라이브 범위 정보가 없음을 의미 합니다.

## <a name="remarks"></a>주의

## <a name="requirements"></a>요구 사항
 헤더: Dia2

 라이브러리: diaguids

 DLL: msdia100

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)