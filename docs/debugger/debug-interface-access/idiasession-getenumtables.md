---
title: 'IDiaSession:: getEnumTables | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41679304986f5de948119a2958524b8f269ceb42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741917"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
기호 저장소에 포함 된 모든 테이블에 대 한 열거자를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>매개 변수
`ppEnumTables`

제한이 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) 개체를 반환 합니다. 이 인터페이스를 사용 하 여 기호 저장소의 테이블을 열거 합니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제
이 예제에서는 `getEnumTables` 메서드를 사용 하 여 특정 열거자 개체를 가져오는 일반 함수를 제공 합니다. 열거자가 있는 경우 함수는 원하는 인터페이스로 캐스팅 될 수 있는 포인터를 반환 합니다. 그렇지 않으면 함수는 `NULL`를 반환 합니다.

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>참조
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
