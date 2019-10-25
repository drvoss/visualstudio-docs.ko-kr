---
title: 'IDiaSymbol:: get_typeIds | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4db7c1d7e3ed19268d94b28a7f0500788f7d21f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739066"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
이 기호에 대 한 컴파일러 관련 형식 식별자 값의 배열을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>매개 변수
 `cTypeIds`

진행 데이터를 보관할 버퍼의 크기입니다.

 `pcTypeIds`

제한이 작성 된 `typeIds`의 수를 반환 하거나 `typeIds` `NULL` 경우 사용할 수 있는 형식 식별자의 총 수를 반환 합니다.

 `typeIds[]`

제한이 형식 식별자로 채워질 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)