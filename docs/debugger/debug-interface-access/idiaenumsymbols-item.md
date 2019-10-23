---
title: 'IDiaEnumSymbols:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12766fe52f7f515b7ca411b17d58117e4e56cc9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743942"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
인덱스를 사용 하 여 기호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>매개 변수
 인덱스입니다.

진행 검색할 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체의 인덱스입니다. 인덱스의 범위는 0 ~ `count`-1입니다. 여기서 `count`는 [IDiaEnumSymbols:: get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) 메서드에서 반환 됩니다.

 기호

제한이 원하는 기호를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)