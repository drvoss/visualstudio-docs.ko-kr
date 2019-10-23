---
title: 'IDiaInjectedSource:: get_crc | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e20cdf82af3b36c589879c81c492a3f58b67f90
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743384"
---
# <a name="idiainjectedsourceget_crc"></a>IDiaInjectedSource::get_crc
소스 코드의 바이트에서 계산 된 CRC (순환 중복 검사)를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 소스 코드의 바이트에서 계산 된 CRC를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)