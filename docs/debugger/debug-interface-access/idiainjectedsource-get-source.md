---
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604160cdaf8c1ff28b306106afe34e047768f3c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828431"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
소스 코드 바이트를 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>매개 변수
 `cbData`

[in] 데이터 버퍼의 크기를 나타내는 바이트의 수입니다.

 `pcbData`

[out] 반환 바이트를 나타내는 바이트 수를 반환 합니다. 하는 경우 `data` 됩니다 `NULL`, 다음 `pcbData` 은 총 데이터의 바이트를 사용할 수 있습니다.

 `data[]`

[out] 소스 바이트를 채울 수 있는 버퍼입니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우이 속성이 지원 되지 않습니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)