---
title: IDiaEnumFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData interface
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db06efe400106260556d8eab5fd644bbfc27f0c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833621"
---
# <a name="idiaenumframedata"></a>IDiaEnumFrameData
데이터 원본에 포함 된 다양 한 프레임 데이터 요소를 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaEnumFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaEnumFrameData`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaEnumFrameData::get__NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|검색 된 `IEnumVARIANT Interface` 이 열거자의 버전입니다.|
|[IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|프레임 데이터 요소의 수를 검색합니다.|
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|인덱스를 사용 하 여 프레임 데이터 요소를 검색 합니다.|
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|열거형 시퀀스에서 프레임 데이터 요소의 지정된 된 수를 검색 합니다.|
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|열거형 시퀀스에 포함 된 프레임 데이터 요소의 지정 된 수를 건너뜁니다.|
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|가상 RVA (상대 주소) 하 여 프레임을 반환합니다.|
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|가상 주소 (VA) 하 여 프레임을 반환합니다.|

## <a name="remarks"></a>설명

## <a name="notes-for-callers"></a>호출자에 대 한 정보
이 인터페이스를 가져올는 [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) 메서드. 세부 정보에 대 한 예제를 참조 하세요.

## <a name="example"></a>예제
이 예제에서는 가져오는 방법을 보여 줍니다 (를 `GetEnumFrameData` 함수) 사용 하 여 (합니다 `ShowFrameData` 함수)는 `IDiaEnumFrameData` 인터페이스. 참조 된 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 인터페이스의 예는 `PrintFrameData` 함수입니다.

```C++

      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)
{
    IDiaEnumFrameData* pUnknown    = NULL;
    REFIID             iid         = __uuidof(IDiaEnumFrameData);
    IDiaEnumTables*    pEnumTables = NULL;
    IDiaTable*         pTable      = NULL;
    ULONG              celt        = 0;

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

void ShowFrameData(IDiaSession *pSession)
{
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;

    if (pEnumFrameData != NULL)
    {
        IDiaFrameData* pFrameData;
        ULONG celt = 0;

        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&
              celt == 1)
        {
            PrintFrameData(pFrameData);
            pFrameData->Release();
        }
        pEnumFrameData->Release();
    }
}
```

## <a name="requirements"></a>요구 사항
**헤더:** Dia2.h

**라이브러리:** diaguids.lib

**DLL:** msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
