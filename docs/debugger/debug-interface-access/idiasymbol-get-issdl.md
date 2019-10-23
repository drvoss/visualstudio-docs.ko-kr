---
title: 'IDiaSymbol:: get_isSdl | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01503bca82046ace7f27cf4f80c163944009e89b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740077"
---
# <a name="idiasymbolget_issdl"></a>IDiaSymbol::get_isSdl
모듈이/SDL 옵션으로 컴파일되는지 여부를 지정 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_isSdl(
   BOOL *pRetVal);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 모듈이/SDL 옵션으로 컴파일되는지 여부를 지정 하는 `BOOL`에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)