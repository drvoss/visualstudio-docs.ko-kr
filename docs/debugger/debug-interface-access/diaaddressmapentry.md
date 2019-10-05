---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 311762f4eafc8dad63da5854870f2836ee68b3ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554898"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
주소 맵에서 항목을 설명 합니다.

## <a name="syntax"></a>구문

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>요소
`rva` 1. 이미지의 상대 가상 주소 (RVA)

`rvaTo` 상대 가상 주소 `rva` 이미지 2.에 매핑된

## <a name="remarks"></a>설명
주소 지도 (A)에서 다른 (B) 하나 이미지 레이아웃에서 번역을 제공합니다. 배열을 `DiaAddressMapEntry` 기준으로 정렬 하는 구조 `rva` 주소 지도 정의 합니다.

주소를 변환할 `addrA`, 주소는 그림과에서 `addrB`, B 이미지에서 다음 단계를 수행:

1. 검색 항목에 대 한 맵을 `e`, 가장 큰 값을 사용 하 여 `rva` 보다 작거나 같음 `addrA`합니다.

2. `delta = addrA - e.rva`를 설정합니다.

3. `addrB = e.rvaTo + delta`를 설정합니다.

    배열을 `DiaAddressMapEntry` 구조에 전달 되는 [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: dia2.h

## <a name="see-also"></a>참고 항목
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
