---
title: 'IDiaEnumTables:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688652fe3915e1974d5d0e1d04fb1ac075863d8c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743735"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
열거형 시퀀스에서 지정 된 수의 테이블을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 `celt`

진행 검색할 열거자의 테이블 수입니다.

 `rgelt`

제한이 원하는 테이블을 나타내는 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 개체로 채워질 배열입니다.

 `pceltFetched`

제한이 인출 된 열거자의 테이블 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 더 이상 테이블이 없으면 `S_FALSE`을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)