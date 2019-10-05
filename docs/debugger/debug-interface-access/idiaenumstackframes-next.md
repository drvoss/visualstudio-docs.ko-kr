---
title: 'Idiaenumstackframes:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833309"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
열거형 시퀀스에서 지정 된 개수의 스택 프레임 요소를 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 celt

[in] 검색할 열거자의 stackframe 요소의 수입니다.

 rgelt

[out] 배열을 채울 요청한 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) 개체입니다.

 pceltFetched

[out] 인출된 열거자의 수가 스택 프레임 요소를 반환합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 자세한 스택 프레임이 없는 경우. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)