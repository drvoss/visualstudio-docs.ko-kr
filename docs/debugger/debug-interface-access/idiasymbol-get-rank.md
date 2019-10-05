---
title: IDiaSymbol::get_rank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c38962ab5915a4235201e76e1828f84a56af1333
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64830789"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
FORTRAN 다차원 배열의 차수 (차원 수)를 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] FORTRAN 다차원 배열의 차원 수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.

> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호를 사용할 수 없는 것을 의미 합니다.

## <a name="remarks"></a>설명
 순위 배열으로 선언 된 위치는 배열의 차원 수를 나타냅니다 `myarray[1,2,3]`합니다. 이 예제는 차수 3 및 3 차원에 있습니다. 순위에 적용 되지 않습니다 C++ 각 차원에 대 한 배열의 배열 개념을 사용 하는 (즉, `myarray[1][2][3]`).

## <a name="see-also"></a>참고 항목
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)