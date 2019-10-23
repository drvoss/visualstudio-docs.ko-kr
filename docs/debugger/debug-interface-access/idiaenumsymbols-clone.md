---
title: 'IDiaEnumSymbols:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07e3823a62ca6fdb81fa6916eec6a1de5598a748
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743980"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.

## <a name="syntax"></a>구문

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>매개 변수
 ppenum

제한이 열거자의 복제본을 포함 하는 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 개체를 반환 합니다. 기호가 중복 되지 않고 열거자만 있습니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)