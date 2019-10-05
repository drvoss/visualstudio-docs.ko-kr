---
title: 'Idiainjectedsource:: Get_length | Microsoft Docs'
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
ms.openlocfilehash: 8333c7e57c3cd3f240f8a72dd865e458b23bc299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828636"
---
# <a name="idiainjectedsourcegetlength"></a>IDiaInjectedSource::get_length
코드의 바이트 수를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 코드의 바이트 수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우이 속성이 지원 되지 않습니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 된 값의 소스 코드의 길이 이며에서 반환 되는 값과 동일 합니다 [idiainjectedsource:: Get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) 메서드.

## <a name="see-also"></a>참고 항목
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)