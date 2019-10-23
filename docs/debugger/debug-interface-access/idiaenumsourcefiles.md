---
title: IDiaEnumSourceFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 091d2f5996d53341e57c5c1b2125609642a156eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744022"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
데이터 원본에 포함 된 다양 한 소스 파일을 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaEnumSourceFiles : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaEnumSourceFiles`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|이 열거자의 `IEnumVARIANT Interface` 버전을 검색 합니다.|
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|소스 파일 수를 검색 합니다.|
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|인덱스를 사용 하 여 소스 파일을 검색 합니다.|
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|열거형 시퀀스에서 지정 된 수의 소스 파일을 검색 합니다.|
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|열거형 시퀀스에서 지정 된 수의 소스 파일을 건너뜁니다.|
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|

## <a name="remarks"></a>주의

## <a name="notes-for-callers"></a>호출자 참고 사항
[IDiaTable](../../debugger/debug-interface-access/idiatable.md) 개체에 대 한 `QueryInterface` 메서드를 호출 하 여이 인터페이스를 가져옵니다. 자세한 내용은 예제를 참조 하세요.

## <a name="example"></a>예제
이 예에서는 DIA session 개체의 테이블 목록에서 `IDiaEnumSourceFiles` 인터페이스를 가져오는 방법을 보여 줍니다. 소스 파일 정보에 액세스 하는 방법에 대 한 예제는 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 인터페이스를 참조 하세요.

```C++

IDiaEnumSourceFiles* GetEnumSourceFiles(IDiaSession *pSession)
{
    IDiaEnumSourceFiles * pUnknown    = NULL;
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);
    IDiaEnumTables*       pEnumTables = NULL;
    IDiaTable*            pTable      = NULL;
    ULONG                 celt        = 0;

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
```

## <a name="requirements"></a>요구 사항
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
