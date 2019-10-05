---
title: 'Idiasession:: Findlinesbyaddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 730793d2b9f2e02d7e5665777f8df4d245b0ddf6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827687"
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
지정된 된 주소를 포함 하는 지정 된 compiland에서 줄을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findLinesByAddr (
    DWORD                 seg,
    DWORD                 offset,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>매개 변수
`seg`

[in] 특정 주소 섹션 구성 요소를 지정합니다.

`offset`

[in] 특정 주소의 오프셋된 구성 요소를 지정합니다.

`length`

[in] 이 쿼리를 처리 하기 위해 주소 범위의 바이트 수를 지정 합니다.

`ppResult`

[out] 반환 된 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 모든 줄의 목록을 포함 하는 개체 번호 규정 하는 지정된 된 주소 범위입니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제
이 예제에서는 함수의 주소 및 길이 사용 하는 함수에 포함 된 모든 줄 번호를 가져오는 함수를 보여 줍니다.

```C++
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,
                                          IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                seg;
    DWORD                offset;
    ULONGLONG            length;

    if (pFunc->get_addressSection ( &seg ) == S_OK &&
        pFunc->get_addressOffset ( &offset ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>참고 항목
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
