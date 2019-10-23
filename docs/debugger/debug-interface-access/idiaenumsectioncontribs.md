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
ms.openlocfilehash: e332bacdeaeca00d4e43d80807ee5f95c51c7e93
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744242"
---
# <a name="idiaenumsectioncontribs"></a>IDiaEnumSectionContribs
데이터 원본에 포함 된 다양 한 섹션 기여를 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaEnumSectionContribs : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaEnumSectionContribs`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaEnumSectionContribs::get__NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|이 열거자의 [IEnumVARIANT 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 버전을 검색 합니다.|
|[IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|섹션 기여 수를 검색 합니다.|
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|인덱스를 사용 하 여 섹션 기여를 검색 합니다.|
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|열거형 시퀀스에서 지정 된 수의 섹션 기여를 검색 합니다.|
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|열거형 시퀀스에서 지정 된 개수의 섹션 기여를 건너뜁니다.|
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|

## <a name="remarks"></a>주의

## <a name="note-for-callers"></a>호출자 참고 사항
[IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) 메서드에서이 인터페이스를 가져옵니다. 자세한 내용은 예제를 참조 하세요.

## <a name="example"></a>예제
이 예제에서는 (`GetEnumSectionContribs` 함수)를 가져오고 `IDiaEnumSectionContribs` 인터페이스를 사용 하 여 `ShowSectionContribs` 함수를 사용 하는 방법을 보여 줍니다. 섹션 기여를 사용 하는 방법에 대 한 자세한 예제는 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 인터페이스를 참조 하세요.

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
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
