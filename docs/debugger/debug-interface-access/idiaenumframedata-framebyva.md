---
title: 'IDiaEnumFrameData:: frameByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9889a4f4add318209728bb09ac5c469c1fa836fe
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744643"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
VA (가상 주소)를 기준으로 프레임을 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>매개 변수
 virtualAddress

진행 관심 프레임의 VA입니다.

 프레임

제한이 제공 된 주소를 포함 하는 프레임을 나타내는 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 지정 된 주소와 일치 하는 프레임 데이터가 없으면 `S_FALSE`을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)