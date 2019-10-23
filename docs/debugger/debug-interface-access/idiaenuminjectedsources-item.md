---
title: 'IDiaEnumInjectedSources:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91be2f4f437cfeed30b0741d10bf719ba0ed2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744510"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
인덱스를 사용 하 여 삽입 된 소스를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>매개 변수
 인덱스입니다.

진행 검색할 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 개체의 인덱스입니다. 인덱스는 0 ~ 1 `count` 범위입니다. 여기서 `count`는 [IDiaEnumInjectedSources:: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) 메서드에서 반환 됩니다.

 injectedSource

제한이 삽입 된 소스를 나타내는 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)