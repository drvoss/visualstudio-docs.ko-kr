---
title: 'IDiaEnumDebugStreams:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25fb1cb952c41d412df72ff7c0f0ad90e56ee6c0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744696"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
열거형 시퀀스에서 지정 된 수의 디버그 스트림을 건너뜁니다.

## <a name="syntax"></a>구문

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>매개 변수
 `celt`

진행 건너뛸 열거형 시퀀스의 디버그 스트림 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 건너뛸 레코드가 더 이상 없는 경우 `S_FALSE`을 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)