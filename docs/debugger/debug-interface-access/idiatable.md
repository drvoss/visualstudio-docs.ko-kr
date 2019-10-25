---
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7a573eb92d7c51079b0a7e97067abd155ae4fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738706"
---
# <a name="idiatable"></a>IDiaTable
DIA 데이터 원본 테이블을 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaTable`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|이 열거자의 [IEnumVARIANT 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 버전을 검색 합니다.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|테이블의 이름을 검색 합니다.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|테이블의 항목 수를 검색 합니다.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|특정 엔트리 인덱스에 대 한 참조를 검색 합니다.|

## <a name="remarks"></a>주의
이 인터페이스는 VisualStudio 네임 스페이스의 `IEnumUnknown` 열거형 메서드를 구현 합니다. @No__t_0 열거형 인터페이스는 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) 및 [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) 메서드를 제외 하 고 테이블 콘텐츠를 반복 하는 데 훨씬 더 효율적입니다.

@No__t_1 메서드 또는 `Next` 메서드 (VisualStudio 네임 스페이스)에서 반환 된 `IUnknown` 인터페이스의 해석은 테이블의 형식에 따라 달라 집니다. 예를 들어 `IDiaTable` 인터페이스가 삽입 된 소스 목록을 나타내는 경우에는 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 인터페이스에 대해 `IUnknown` 인터페이스를 쿼리해야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
[IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) 또는 [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) 메서드를 호출 하 여이 인터페이스를 가져옵니다.

다음 인터페이스는 `IDiaTable` 인터페이스를 사용 하 여 구현 됩니다. 즉, 다음 인터페이스 중 하나에 대해 `IDiaTable` 인터페이스를 쿼리할 수 있습니다.

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>예제
첫 번째 함수인 `ShowTableNames`는 세션에 있는 모든 테이블의 이름을 표시 합니다. 두 번째 함수인 `GetTable`는 모든 테이블에서 지정 된 인터페이스를 구현 하는 테이블을 검색 합니다. 세 번째 함수인 `UseTable`는 `GetTable` 함수를 사용 하는 방법을 보여 줍니다.

> [!NOTE]
> `CDiaBSTR`은 `BSTR`를 래핑하고 인스턴스화가 범위를 벗어날 때 문자열 해제를 자동으로 처리 하는 클래스입니다.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
