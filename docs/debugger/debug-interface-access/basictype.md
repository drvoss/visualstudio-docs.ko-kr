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
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745486"
---
# <a name="basictype"></a>BasicType
기호의 기본 유형을 지정 합니다.

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
btNoType 기본 형식이 지정 되지 않았습니다.

btVoid Basic 형식은 `void`입니다.

btChar Basic 형식은 `char` (C/C++ 형식)입니다.

btWChar 기본 형식은 와이드 (유니코드) 문자 (`WCHAR`)입니다.

btInt 기본 형식 `signed int` (C/C++ 형식)입니다.

btUInt 기본 형식은 `unsigned int` (C/C++ 형식)입니다.

btFloat Basic 형식은 부동 소수점 숫자 (`FLOAT`)입니다.

btBCD Basic 형식은 이진으로 코딩 된 10 진수 (`BCD`)입니다.

btBool Basic 형식은 부울 (`BOOL`)입니다.

btLong Basic 형식은 `long int` (C/C++ 형식)입니다.

btULong Basic 형식은 `unsigned long int` (C/C++ 형식)입니다.

btCurrency Basic 형식은 currency입니다.

btDate Basic 형식은 날짜/시간 (`DATE`)입니다.

btVariant Basic 형식은 `VARIANT` (변수 형식 구조)입니다.

btComplex Basic 형식은 복소수입니다.

btBit Basic 형식은 bit입니다.

btBSTR Basic 형식은 기본 또는 이진 문자열 (`BSTR`)입니다.

btHresult 기본 유형은 `HRESULT`입니다.

## <a name="remarks"></a>주의
이 열거형의 값은 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) 메서드에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
