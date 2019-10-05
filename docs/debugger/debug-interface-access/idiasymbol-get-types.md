---
title: 'Idiasymbol:: Get_types | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19642e6875e81220cb20109ce45e8dca40777a63
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786566"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
이 기호에 대 한 컴파일러 별 형식의 배열을 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>매개 변수
 `cTypes`

[in] 데이터를 저장할 버퍼의 크기입니다.

 `pcTypes`

[out] 를 작성 하는 형식의 수를 반환 합니다. 또는 합니다 `types` 매개 변수는 `NULL`를 사용할 수 있는 유형의 총 다음.

 `types[]`

[out] 배열을 사용 하 여 채울 합니다 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 이 기호에 대 한 모든 형식을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.

> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호를 사용할 수 없는 것을 의미 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)