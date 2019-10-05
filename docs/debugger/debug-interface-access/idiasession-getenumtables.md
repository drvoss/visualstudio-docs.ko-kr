---
title: 'Idiasession:: Getenumtables | Microsoft Docs'
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
ms.openlocfilehash: 759972fa02c7645ae457e0b715d835b2d717e26f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839175"
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

[out] 반환 된 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) 개체입니다. 이 인터페이스를 사용 하 여 기호 저장소의 테이블을 열거 합니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제
이 예제를 사용 하는 일반 함수를 제공 합니다 `getEnumTables` 특정 열거자 개체를 가져오려면 메서드. 함수는 원하는 인터페이스를 캐스팅할 수 있는 포인터를 반환 하면 열거자가 있으면 반환이 고, 그렇지 `NULL`합니다.

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

## <a name="see-also"></a>참고 항목
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
