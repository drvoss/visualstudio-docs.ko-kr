---
title: 'IDiaEnumSegments:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34062b654cbaccec053c5ac50bfb041d37a0f4e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744198"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
열거형 시퀀스에서 지정 된 수의 세그먼트를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 celt

진행 검색할 열거자의 세그먼트 수입니다.

 rgelt

제한이 세그먼트를 나타내는 원하는 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 개체로 채워질 배열입니다.

 pceltFetched

제한이 인출 된 열거자의 세그먼트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 세그먼트가 더 이상 없는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)