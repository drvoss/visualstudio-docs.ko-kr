---
title: 'IDiaInjectedSource:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95c51910ee638338f588b1e81b844cf3f487a50e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743357"
---
# <a name="idiainjectedsourceget_length"></a>IDiaInjectedSource::get_length
코드의 바이트 수를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 코드의 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 이 메서드에서 반환 되는 값은 소스 코드의 길이 이며 [IDiaInjectedSource:: get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) 메서드에서 반환 되는 값과 같습니다.

## <a name="see-also"></a>참조
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)