---
title: 'IDiaSymbol:: get_types | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d23ea3c4d885b3f7575c998999814d0808d03bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739065"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
이 기호에 대 한 컴파일러 관련 형식의 배열을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>매개 변수
 `cTypes`

진행 데이터를 보관할 버퍼의 크기입니다.

 `pcTypes`

제한이 쓴 형식의 수를 반환 하거나, `types` 매개 변수가 `NULL` 되 면 사용 가능한 총 형식 수를 반환 합니다.

 `types[]`

제한이 이 기호의 모든 형식을 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체와 함께 채워질 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)