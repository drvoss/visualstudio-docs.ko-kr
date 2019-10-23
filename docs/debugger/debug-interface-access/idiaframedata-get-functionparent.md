---
title: 'IDiaFrameData:: get_functionParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 809de8589302ddc35a14e2ea0663248a163176e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743616"
---
# <a name="idiaframedataget_functionparent"></a>IDiaFrameData::get_functionParent
바깥쪽 함수의 프레임 데이터 인터페이스를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_functionParent ( 
   IDiaFrameData** pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 바깥쪽 함수에 대 한 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)