---
title: IDiaSession::findLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29f3f714cdcbe529dac98948f6568934a6f508af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832408"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
지정 된 가상 주소 (VA) 범위에 포함 된 줄에 대 한 줄 번호 정보를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>매개 변수
`va`

[in] VA.로 주소를 지정합니다.

`length`

[in] 이 쿼리를 처리 하기 위해 주소 범위의 바이트 수를 지정 합니다.

`ppResult`

[out] 반환 된 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 모든 줄의 목록을 포함 하는 개체 번호 규정 하는 지정된 된 주소 범위입니다.

## <a name="example"></a>예제
이 예제에서는 함수의 가상 주소 및 길이 사용 하는 함수에 포함 된 모든 줄 번호를 가져오는 함수를 보여 줍니다.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>참고 항목
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
