---
title: 'IDiaSession:: symbolById | Microsoft Docs'
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
ms.openlocfilehash: b0ffcb6c438150bff82f17a66c3347c300b17d72
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741877"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
고유한 식별자로 기호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>매개 변수
`id`

진행 고유 식별자입니다.

`ppSymbol`

제한이 검색 된 기호를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
지정 된 식별자는 모든 기호를 고유 하 게 만들기 위해 DIA SDK에서 내부적으로 사용 하는 고유 값입니다.

예를 들어이 메서드를 사용 하 여 다른 기호의 형식을 나타내는 기호를 검색할 수 있습니다 (예제 참조).

## <a name="example"></a>예제
이 예제에서는 다른 기호의 형식을 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 을 검색 합니다. 이 예제에서는 세션에서 `symbolById` 메서드를 사용 하는 방법을 보여 줍니다. 더 간단한 방법은 [IDiaSymbol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) 메서드를 호출 하 여 형식 기호를 직접 검색 하는 것입니다.

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

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
