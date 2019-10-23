---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738642"
---
# <a name="locationtype"></a>LocationType
기호에 포함 된 위치 정보의 종류를 나타냅니다.

## <a name="syntax"></a>구문

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>요소
`LocIsNull` 위치 정보를 사용할 수 없습니다.

`LocIsStatic` 위치가 static입니다.

`LocIsTLS` 위치가 스레드 로컬 저장소에 있습니다.

`LocIsRegRel` 위치가 등록 상대 경로입니다.

`LocIsThisRel` 위치는 `this` 상대 경로입니다.

`LocIsEnregistered` 위치가 레지스터에 있습니다.

`LocIsBitField` 위치가 비트 필드에 있습니다.

`LocIsSlot` 위치는 MSIL (Microsoft 중간 언어) 슬롯입니다.

`LocIsIlRel` 위치는 MSIL에 상대적입니다.

`LocInMetaData` 위치가 메타 데이터에 있습니다.

`LocIsConstant` 위치는 상수 값입니다.

이 열거형의 위치 형식 수를 `LocTypeMax` 합니다.

## <a name="remarks"></a>주의
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 인터페이스에 사용할 수 있는 속성은 이미지 파일 내의 기호 위치에 따라 달라 집니다. 자세한 내용은 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)를 참조 하세요.

이 열거형의 값은 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) 메서드를 호출 하 여 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)
