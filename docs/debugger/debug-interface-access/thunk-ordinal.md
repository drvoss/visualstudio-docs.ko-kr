---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738505"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
썽크 유형을 지정 합니다.

## <a name="syntax"></a>구문

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>요소
THUNK_ORDINAL_NOTYPE 표준 썽크입니다.

THUNK_ORDINAL_ADJUSTOR ADJUSTOR 썽크 `this`를 합니다.

THUNK_ORDINAL_VCALL 가상 호출 썽크입니다.

THUNK_ORDINAL_PCODE P-코드 썽크

THUNK_ORDINAL_LOAD 지연 로드 썽크입니다.

THUNK_ORDINAL_TRAMP_INCREMENTAL 증분 trampoline 썽크 (한 메모리 공간에서 다른 메모리 공간으로 호출을 바운스 하는 데 사용 됨).

THUNK_ORDINAL_TRAMP_BRANCHISLAND 분기 지점입니다.

## <a name="remarks"></a>주의
이 열거형의 값은 [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) 메서드에 대 한 호출에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
