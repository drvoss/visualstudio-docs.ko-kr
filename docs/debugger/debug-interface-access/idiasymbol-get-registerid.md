---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e2b1cbb6837ca139e735bef17bc0c2712d9cae7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786579"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
위치의 등록 지정자 검색 때 합니다 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 로 설정 되어 `LocIsEnregistered`입니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 위치의 등록 지정자를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.

> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호에 사용할 수 없다는 것을 의미 합니다.

## <a name="remarks"></a>설명
 즉, 기호가 레지스터를 기준으로 하는 경우 경우 기호 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 로 설정 된 `LocIsRegRel`를 사용 하 여를 `get_registerId` 메서드를 호출 하 여 여러 번를 [idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) 기호 위치한 레지스터에서 오프셋을 가져올 메서드.

## <a name="see-also"></a>참고 항목
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)