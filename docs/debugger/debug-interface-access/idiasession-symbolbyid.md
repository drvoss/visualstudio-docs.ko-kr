---
title: 'Idiasession:: Symbolbyid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b58fcf55741975a776e222b2845ae50774e7fc9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832916"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
해당 고유 식별자로 기호를 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>매개 변수
`id`

[in] 고유 식별자입니다.

`ppSymbol`

[out] 반환 된 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 기호를 나타내는 개체를 검색 합니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
지정된 된 식별자에는 모든 기호를 고유 하 게 DIA SDK에 의해 내부적으로 사용 되는 고유 값입니다.

이 방법을 사용할 수, 예를 들어, 다른 기호 유형을 나타내는 기호를 검색할 (예제 참조).

## <a name="example"></a>예제
이 예제에서는 검색을 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 나타내는 다른 기호의 형식입니다. 사용 하는 방법을 보여 주는이 예제는 `symbolById` 세션에서 메서드. 간단 호출 하는 것은 [idiasymbol:: Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) 형식 기호를 직접 검색 하는 방법입니다.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>참고 항목
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
