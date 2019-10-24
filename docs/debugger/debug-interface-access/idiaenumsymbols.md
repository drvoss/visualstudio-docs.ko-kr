---
title: IDiaEnumSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0864522c079ff1f694072fec3147d006cd2ce43d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743891"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
데이터 원본에 포함 된 다양 한 기호를 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaEnumSymbols : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaEnumSymbols`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|이 열거자의 `IEnumVARIANT Interface` 버전을 검색 합니다.|
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|기호 수를 검색 합니다.|
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|인덱스를 사용 하 여 기호를 검색 합니다.|
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|열거형 시퀀스에서 지정 된 수의 기호를 검색 합니다.|
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|열거형 시퀀스에서 지정 된 수의 기호를 건너뜁니다.|
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|

## <a name="remarks"></a>주의
이 인터페이스는 `SymTagUDT` (사용자 정의 형식) 또는 `SymTagBaseClass` 같은 특정 형식의 기호를 기준으로 그룹화 된 기호를 제공 합니다. 주소로 그룹화 된 기호로 작업 하려면 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) 인터페이스를 사용 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
다음 메서드를 호출 하 여이 인터페이스를 가져옵니다.

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)

## <a name="example"></a>예제
이 예제에서는 `IDiaEnumSymbols` 인터페이스를 가져온 다음이 열거형을 사용 하 여 Udt (사용자 정의 형식)를 나열 하는 방법을 보여 줍니다.

> [!NOTE]
> `CDiaBSTR`은 `BSTR`를 래핑하고 인스턴스화가 범위를 벗어날 때 문자열 해제를 자동으로 처리 하는 클래스입니다.

```C++
void ShowUDTs(IDiaSymbol *pGlobals)
{
    CComPtr<IDiaEnumSymbols> pEnum;
    CComPtr<IDiaSymbol> pSymbol;
    HRESULT hr;

    hr = pGlobals->findChildren(SymTagUDT,
                                NULL,
                                nsfCaseInsensitive | nsfUndecoratedName,
                                &pEnum);
    if (hr == S_OK)
    {
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR name;
            if ( pSymbol->get_name( &name ) != S_OK )
                Fatal( "get_name" );
            printf( "Found UDT: %ws\n", name );
            pSymbol = 0;
        }
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
