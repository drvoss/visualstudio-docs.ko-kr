---
title: IDiaEnumLineNumbers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers interface
ms.assetid: cdf07b4f-19e4-4dcd-8af8-c2dbca586a7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49257aa3b9b51a1e8b62c867ced030b853deae9c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833511"
---
# <a name="idiaenumlinenumbers"></a>IDiaEnumLineNumbers
데이터 원본에 포함 된 다양 한 줄 번호를 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaEnumLineNumbers : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaEnumLineNumbers`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaEnumLineNumbers::get__NewEnum](../../debugger/debug-interface-access/idiaenumlinenumbers-get-newenum.md)|검색 된 [IEnumVARIANT 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 이 열거자의 버전입니다.|
|[IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)|줄 번호의 수를 검색 합니다.|
|[IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)|인덱스를 사용 하 여 줄 번호를 검색합니다.|
|[IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)|열거형 시퀀스에서 줄 번호의 지정된 된 수를 검색 합니다.|
|[IDiaEnumLineNumbers::Skip](../../debugger/debug-interface-access/idiaenumlinenumbers-skip.md)|열거형 시퀀스에서 줄 번호의 지정된 된 수를 건너뜁니다.|
|[IDiaEnumLineNumbers::Reset](../../debugger/debug-interface-access/idiaenumlinenumbers-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[IDiaEnumLineNumbers::Clone](../../debugger/debug-interface-access/idiaenumlinenumbers-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|

## <a name="remarks"></a>설명

## <a name="notes-for-callers"></a>호출자에 대 한 정보
이 인터페이스의 다음 메서드 중 하나를 호출 하 여 가져온 합니다 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 인터페이스:

- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)

- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)

- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)

- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)

- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)

## <a name="example"></a>예제
가져오는 방법을 보여 주는이 예제는 `IDiaEnumLineNumbers` 세션에서 인터페이스입니다. 이 경우에 예제에서는 함수에 대 한 줄 번호 열거형을 가져옵니다 (나타내는 `pSymbol`). 줄 번호를 사용 하 여 자세한 예제를 참조 하세요. 합니다 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 인터페이스입니다.

```C++
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )
{
    ULONGLONG length = 0;
    DWORD isect = 0;
    DWORD offset = 0;
    pSymbol->get_addressSection( &isect );
    pSymbol->get_addressOffset( &offset );
    pSymbol->get_length( &length );
    if ( isect != 0 && length > 0 )
    {
        CComPtr< IDiaEnumLineNumbers > pLines;
        if ( SUCCEEDED( pSession->findLinesByAddr(
                                      isect,
                                      offset,
                                      static_cast<DWORD>( length ),
                                      &pLines )
                      )
           )
        {
            // Do something with the enumeration
        }
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
