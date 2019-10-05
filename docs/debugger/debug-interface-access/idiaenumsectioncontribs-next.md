---
title: 'Idiaenumsectioncontribs:: Next | Microsoft Docs'
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
ms.openlocfilehash: 8e8fd088ff6be619de56f27f91b198aed18e428c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829786"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
열거형 시퀀스에서 섹션 작성 글의 지정된 된 수를 검색 합니다.

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

[in] 검색할 열거자의 섹션 작성 글의 수입니다.

 rgelt

[out] 배열을 채울 합니다 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 원하는 섹션 기여를 나타내는 개체입니다.

 pceltFetched

[out] 인출 열거자의 섹션 작성 글의 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우 더 많은 섹션 작성 글을 없습니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)