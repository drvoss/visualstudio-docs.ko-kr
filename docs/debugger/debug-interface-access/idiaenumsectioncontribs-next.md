---
title: 'IDiaEnumSectionContribs:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61d99b0c881abdb8974e94352911ae3234c440c1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744269"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
열거형 시퀀스에서 지정 된 수의 섹션 기여를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 celt

진행 검색할 열거자의 섹션 기여 수입니다.

 rgelt

제한이 원하는 섹션 기여를 나타내는 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 개체로 채워질 배열입니다.

 pceltFetched

제한이 인출 된 열거자의 섹션 기여 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 더 이상 섹션 기여를 하지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)