---
title: 'IDiaEnumSourceFiles:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7aef3ea724bbb50f0342032a62e0044a1f0eb30
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744047"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
열거형 시퀀스에서 지정 된 수의 소스 파일을 건너뜁니다.

## <a name="syntax"></a>구문

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>매개 변수
 celt

진행 건너뛸 열거 시퀀스의 소스 파일 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 건너뛸 소스 파일이 더 이상 없는 경우 `S_FALSE`을 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)