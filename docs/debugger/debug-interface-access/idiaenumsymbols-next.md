---
title: 'IDiaEnumSymbols:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2d754c144ad876890b89ea217bf0ac55ad60b24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743931"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
열거형 시퀀스에서 지정 된 수의 기호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 celt

진행 검색할 열거자의 기호 수입니다.

 rgelt

제한이 원하는 기호를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체로 채워질 배열입니다.

 pceltFetched

제한이 인출 된 열거자의 기호 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 더 이상 기호가 없으면 `S_FALSE`을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="example"></a>예제

```C++
IDiaEnumSymbols* pEnum
CComPtr< IDiaSymbol> pSym;
DWORD celt;
pEnum->Next( 1, &pSym, &celt );
```

## <a name="see-also"></a>참조
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)