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
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745258"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
주소 맵의 항목을 설명 합니다.

## <a name="syntax"></a>구문

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>요소
이미지 A의 RVA (상대 가상 주소)를 `rva` 합니다.

이미지 B에서 매핑되는 `rva` 상대 가상 주소를 `rvaTo` 합니다.

## <a name="remarks"></a>주의
주소 맵은 한 이미지 레이아웃 (A)에서 다른 이미지 레이아웃 (B)으로의 변환을 제공 합니다. @No__t_1를 기준으로 정렬 된 `DiaAddressMapEntry` 구조의 배열로, 주소 맵을 정의 합니다.

@No__t_0 주소를 변환 하려면 이미지 A에서 주소 `addrB` 하 고 이미지 B에서 다음 단계를 수행 합니다.

1. @No__t_0 항목에 대 한 맵을 검색 하 고 `addrA` 보다 작거나 같은 가장 큰 `rva`를 검색 합니다.

2. `delta = addrA - e.rva`를 설정합니다.

3. `addrB = e.rvaTo + delta`를 설정합니다.

    @No__t_0 구조체의 배열은 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드에 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: dia2

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
