---
title: 'IDiaEnumSymbols:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9252826470decd3cddfabdcc2a00e22037d5de5c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743902"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
열거형 시퀀스에서 지정 된 수의 기호를 건너뜁니다.

## <a name="syntax"></a>구문

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>매개 변수
 celt

진행 건너뛸 열거 시퀀스의 기호 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 건너뛸 기호가 더 이상 없는 경우 `S_FALSE`을 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)