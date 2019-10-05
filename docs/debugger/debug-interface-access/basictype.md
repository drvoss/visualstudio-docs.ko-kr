---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829734"
---
# <a name="basictype"></a>BasicType
기호 기본 형식을 지정합니다.

## <a name="syntax"></a>구문

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>요소
btNoType 기본 유형이 지정 되지 않았습니다.

기본 형식 btVoid는는 `void`합니다.

기본 형식 btChar은는 `char` (C /C++ 형식).

기본 형식 btWChar 와이드 (유니코드) 문자는 (`WCHAR`).

기본 형식 btInt가 `signed int` (C /C++ 형식).

기본 형식 btUInt가 `unsigned int` (C /C++ 형식).

btFloat 기본 형식 부동 소수점 숫자인 (`FLOAT`).

기본 형식 btBCD이 이진 코딩 된 10 진수 (`BCD`).

기본 형식 btBool은 부울 (`BOOL`).

기본 형식 btLong은는 `long int` (C /C++ 형식).

기본 형식 btULong은는 `unsigned long int` (C /C++ 형식).

기본 형식 btCurrency는 통화입니다.

기본 형식 btDate는 날짜/시간 (`DATE`).

btVariant 기본 형식을 변수 유형 구조가 (`VARIANT`).

기본 형식 btComplex 복합 숫자입니다.

기본 형식 btBit 약간입니다.

기본 형식 btBSTR는 기본 또는 이진 문자열 (`BSTR`).

기본 형식 btHresult는는 `HRESULT`합니다.

## <a name="remarks"></a>설명
이 열거형의 값에서 반환 되는 [idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: cvconst.h

## <a name="see-also"></a>참고 항목
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
