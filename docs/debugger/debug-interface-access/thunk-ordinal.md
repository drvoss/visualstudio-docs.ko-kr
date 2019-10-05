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
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854442"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
썽크 형식을 지정합니다.

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
표준 THUNK_ORDINAL_NOTYPE 썽크 합니다.

THUNK_ORDINAL_ADJUSTOR는 `this` 조정기 썽크 합니다.

THUNK_ORDINAL_VCALL 가상 호출 썽크 합니다.

THUNK_ORDINAL_PCODE p-code 썽크 합니다.

THUNK_ORDINAL_LOAD 지연 로드 썽크 합니다.

THUNK_ORDINAL_TRAMP_INCREMENTAL 증분 trampoline 썽크 (trampoline 썽크를 다른 메모리 공간에서 호출 반송에 사용 됨).

THUNK_ORDINAL_TRAMP_BRANCHISLAND 분기 지점 trampoline 썽크 합니다.

## <a name="remarks"></a>설명
이 열거형의 값에 대 한 호출에서 반환 되는 [idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: cvconst.h

## <a name="see-also"></a>참고 항목
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
