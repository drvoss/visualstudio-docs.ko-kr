---
title: 'IDiaSectionContrib:: get_code16bit | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94fcc9ae93a515890025bb74a810733f213c869a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742742"
---
# <a name="idiasectioncontribget_code16bit"></a>IDiaSectionContrib::get_code16bit
섹션에 16 비트 코드가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_code16bit(
   BOOL *pRetVal
};
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 섹션의 코드가 16 비트 이면 `TRUE`을 반환 합니다. 그렇지 않으면 `FALSE`을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 이 메서드는 코드가 16 비트 인지만 나타냅니다. 코드가 16 비트가 아니면 32 비트 또는 64 비트 코드와 같은 다른 것이 될 수 있습니다.

## <a name="see-also"></a>참조
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)