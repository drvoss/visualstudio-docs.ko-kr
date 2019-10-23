---
title: 'IDiaEnumSegments:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efedd0e24c96259f1c9e9b6fc7522ee250bd4b25
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744163"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
열거형 시퀀스에서 지정 된 개수의 세그먼트를 건너뜁니다.

## <a name="syntax"></a>구문

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>매개 변수
 celt

진행 건너뛸 열거 시퀀스의 세그먼트 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 건너뛸 세그먼트가 더 이상 없는 경우 `S_FALSE`을 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)