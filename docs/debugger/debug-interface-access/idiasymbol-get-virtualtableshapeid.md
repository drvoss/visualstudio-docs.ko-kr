---
title: 'IDiaSymbol:: get_virtualTableShapeId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShapeId method
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3134d504625435706c36e1afc7c9df64611a7516
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738812"
---
# <a name="idiasymbolget_virtualtableshapeid"></a>IDiaSymbol::get_virtualTableShapeId
기호의 가상 테이블 셰이프 기호 식별자를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_virtualTableShapeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 기호의 가상 테이블 셰이프 기호 ID를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
 식별자는 모든 기호를 고유 하 게 표시 하기 위해 DIA SDK에서 생성 하는 고유 값입니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)