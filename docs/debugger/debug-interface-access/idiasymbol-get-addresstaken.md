---
title: IDiaSymbol::get_addressTaken | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f452aa01f29d25ad1674c6bc2f5494a745733793
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741066"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
다른 기호가이 기호의 주소를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 다른 기호가이 주소를 참조 하는 경우 `TRUE`를 반환 합니다. 그렇지 않으면 `FALSE`을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

## <a name="example"></a>예제
 다음 예제에서는 `B` 참조 `A` 합니다. 따라서 기호 `A`의 `get_addressTaken` 메서드는 `TRUE`를 반환 합니다.

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v7.0|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)