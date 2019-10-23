---
title: IDiaSymbol::get_oemSymbolId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60d1486ba654ddba9fdd1dae6439cafbb1f81f29
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739587"
---
# <a name="idiasymbolget_oemsymbolid"></a>IDiaSymbol::get_oemSymbolId
OEM (원본 장비 제조업체) 기호 ID 값을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_oemSymbolId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 OEM의 내부적으로 할당 된 기호 ID를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
 식별자는 모든 기호를 고유 하 게 표시 하기 위해 DIA SDK에서 생성 하는 고유 값입니다.

 이 속성은 `SymTagCustomType` [SymTagEnum 열거](../../debugger/debug-interface-access/symtagenum.md) 형식의 기호에만 적용 됩니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)