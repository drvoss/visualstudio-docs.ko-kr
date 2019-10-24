---
title: 'IDiaSectionContrib:: get_read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_read method
ms.assetid: 68bfb35c-eabd-412a-bc8f-3094703b98c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 206415f45c4f4f087b99064f772a679f15eb1506
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742568"
---
# <a name="idiasectioncontribget_read"></a>IDiaSectionContrib::get_read
섹션을 읽을 수 있는지 여부를 나타내는 플래그를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_read ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 섹션을 읽을 수 있는 경우 `TRUE`을 반환 합니다. 그렇지 않으면 `FALSE`을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)