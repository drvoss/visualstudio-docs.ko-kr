---
title: IDiaSymbol::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60f9b9fd91535cc16b96da530db8ab43c4eaabf2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739104"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
이 기호의 형식을 나타내는 기호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>매개 변수
`pRetVal`

제한이 이 기호의 형식을 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
기호에 포함 된 형식을 확인 하려면이 메서드를 호출 하 고 결과 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 검사 해야 합니다. 기호에 형식을 사용할 수 없습니다. 예를 들어 구조체의 이름에는 형식이 없지만 자식 기호 ( [IDiaSymbol:: findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) 메서드를 사용 하 여 해당 자식을 검사 함)가 있을 수 있습니다.

## <a name="example"></a>예제

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
