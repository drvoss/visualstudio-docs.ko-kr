---
title: 'IDiaSymbol:: get_baseType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a3d1bb8b2f3095fd35488c47f823e7b3603995b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740913"
---
# <a name="idiasymbolget_basetype"></a>IDiaSymbol::get_baseType
이 기호의 기본 형식을 검색<em>합니다.</em>

## <a name="syntax"></a>구문

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
`pRetVal`

제한이 기호의 기본 형식을 지정 하는 [Basictype 열거형](../../debugger/debug-interface-access/basictype.md) 열거형의 값을 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
기호의 기본 형식은 먼저 기호의 형식을 가져온 다음 기본 형식에 대해 반환 된 형식을 조회 하 여 확인할 수 있습니다. 일부 기호에는 기본 형식 (예: 구조체 이름)이 없을 수 있습니다.

## <a name="example"></a>예제

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v7.0|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType 열거형](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
