---
title: 'Idiasymbol:: Get_typeids | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7b32ab5b1965ea7a641cfac470addd2aae0ede0
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64791770"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
이 기호에 대 한 컴파일러 별 형식 식별자 값의 배열을 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>매개 변수
 `cTypeIds`

[in] 데이터를 저장할 버퍼의 크기입니다.

 `pcTypeIds`

[out] 개수를 반환 `typeIds` 기록 또는 `typeIds` 는 `NULL`, 다음 총 형식 식별자를 사용할 수 있습니다.

 `typeIds[]`

[out] 배열 형식 식별자로 채워질입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.

> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호를 사용할 수 없는 것을 의미 합니다.

## <a name="see-also"></a>관련 항목
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)