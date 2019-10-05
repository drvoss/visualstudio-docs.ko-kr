---
title: 'Idiaenumframedata:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d747149e18f831b9f57249503a64c37141c4daa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833600"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
열거형 시퀀스에 포함 된 프레임 데이터 요소의 지정 된 수를 건너뜁니다.

## <a name="syntax"></a>구문

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>매개 변수
 celt

[in] 건너뛸 열거형 시퀀스에서 프레임 데이터 요소의 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 건너뛸 레코드가 더 이상 없으면입니다.

## <a name="see-also"></a>참고 항목
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)