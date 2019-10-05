---
title: 'Idiasymbol:: Get_oemid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91d6097fd558ee3fd4e61485eb53cd25a0b7c6a2
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64796046"
---
# <a name="idiasymbolgetoemid"></a>IDiaSymbol::get_oemId
기호 원래 장비 제조업체 (OEM) ID 값을 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_oemId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] OEM을 식별 하는 고유 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.

> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호에 사용할 수 없다는 것을 의미 합니다.

## <a name="remarks"></a>설명
 이 속성은 사용 하 여 기호에만 적용 됩니다는 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 유형의 `SymTagCustomType`합니다.

## <a name="see-also"></a>참고 항목
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)