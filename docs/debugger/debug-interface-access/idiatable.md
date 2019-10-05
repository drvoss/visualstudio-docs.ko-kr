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
ms.openlocfilehash: 604c68ef82f66358238f94b43f000fae24a076f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834154"
---
# <a name="idiatable"></a>IDiaTable
DIA 데이터 원본 테이블을 열거합니다.

## <a name="syntax"></a>구문

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaTable`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|검색 된 [IEnumVARIANT 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 이 열거자의 버전입니다.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|테이블의 이름을 검색합니다.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|테이블에서 항목을 검색합니다.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|특정 항목 인덱스에 대 한 참조를 검색합니다.|

## <a name="remarks"></a>설명
이 인터페이스를 구현 하는 `IEnumUnknown` Microsoft.VisualStudio.OLE.Interop 네임 스페이스에서 열거형 메서드. `IEnumUnknown` 열거형 인터페이스 보다 목차를 반복 하기 위한 훨씬 더 효율적입니다 합니다 [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md) 하 고 [idiatable:: Item](../../debugger/debug-interface-access/idiatable-item.md) 메서드.

해석은 합니다 `IUnknown` 인터페이스 중 하나에서 반환 된를 `IDiaTable::Item` 메서드 또는 `Next` (Microsoft.VisualStudio.OLE.Interop 네임 스페이스)에서 메서드는 테이블의 유형에 따라 달라 집니다. 예를 들어 경우는 `IDiaTable` 인터페이스 삽입된 원본 목록을 나타냅니다는 `IUnknown` 인터페이스를 쿼리해야 합니다 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 인터페이스.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
호출 하 여이 인터페이스를 가져올는 [idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) 하거나 [idiaenumtables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) 메서드.

다음 인터페이스는 사용 하 여 구현 합니다 `IDiaTable` 인터페이스 (즉, 쿼리할 수 있습니다는 `IDiaTable` 다음 인터페이스 중 하나에 대 한 인터페이스):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>예제
첫 번째 함수 `ShowTableNames`, 세션에 있는 모든 테이블의 이름을 표시 합니다. 두 번째 함수를 `GetTable`, 모든 지정된 된 인터페이스를 구현 하는 테이블에 대 한 테이블을 검색 합니다. 세 번째 함수 `UseTable`를 사용 하는 방법을 보여 줍니다는 `GetTable` 함수입니다.

> [!NOTE]
> `CDiaBSTR` 래핑하는 클래스를 `BSTR` 인스턴스화 범위를 벗어나면 문자열이 해제를 자동으로 처리 하 고 있습니다.

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
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
