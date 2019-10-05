---
title: IDiaEnumSectionContribs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs interface
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ede7789fcdba63595cecd6426c8f3ca1a4048e07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833261"
---
# <a name="idiaenumsectioncontribs"></a>IDiaEnumSectionContribs
데이터 원본에 포함 된 다양 한 섹션 기여도 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaEnumSectionContribs : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaEnumSectionContribs`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaEnumSectionContribs::get__NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|검색 된 [IEnumVARIANT 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 이 열거자의 버전입니다.|
|[IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|섹션 작성 글의 수를 검색 합니다.|
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|인덱스를 사용 하 여 섹션 기여를 검색합니다.|
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|열거형 시퀀스에서 섹션 작성 글의 지정된 된 수를 검색 합니다.|
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|열거형 시퀀스에서 섹션 작성 글의 지정된 된 수를 건너뜁니다.|
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|

## <a name="remarks"></a>설명

## <a name="note-for-callers"></a>호출자 참고
이 인터페이스를 가져올는 [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) 메서드. 세부 정보에 대 한 예제를 참조 하세요.

## <a name="example"></a>예제
이 예제에서는 가져오는 방법을 보여 줍니다 (를 `GetEnumSectionContribs` 함수) 사용 하 여 (합니다 `ShowSectionContribs` 함수)는 `IDiaEnumSectionContribs` 인터페이스. 섹션 기여를 사용 하 여 자세한 예제를 참조 하세요. 합니다 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 인터페이스입니다.

```C++

IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)
{
    IDiaEnumSectionContribs* pUnknown    = NULL;
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);
    IDiaEnumTables*          pEnumTables = NULL;
    IDiaTable*               pTable      = NULL;
    ULONG                    celt        = 0;

    if (pSession->getEnumTables(&pEnumTables) != S_OK)
    {
        wprintf(L"ERROR - GetTable() getEnumTables\n");
        return NULL;
    }
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)
    {
        // There is only one table that matches the given iid
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);
        pTable->Release();
        if (hr == S_OK)
        {
            break;
        }
    }
    pEnumTables->Release();
    return pUnknown;
}

void ShowSectionContribs(IDiaSession *pSession)
{
    IDiaEnumSectionContribs* pEnumSectionContribs;

    pEnumSectionContribs = GetEnumSectionContribs(pSession);
    if (pSectionContrib != NULL)
    {
        IDiaSectionContrib* pSectionContrib;
        ULONG celt = 0;

        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&
              celt == 1)
        {
            PrintSectionContrib(pSectionContrib, pSession);
            pSectionContrib->Release();
        }
        pSectionContrib->Release();
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
