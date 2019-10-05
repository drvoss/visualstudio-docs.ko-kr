---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cc189283d6e9910b0b01d3d3e1ca28165bf500
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839695"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
읽고 `BOOL` 속성 집합의 값입니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>매개 변수
 `id`

[in] 읽을 속성의 식별자 (`PROPID` 으로 WTypes.h에 정의 된 `ULONG`).

 `pValue`

[out] 속성 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_INVALIDARG` 형식의 속성이 없는 경우 `BOOL`합니다.

## <a name="remarks"></a>설명
 일관 된 결과 대 한 해석 된 `BOOL` 값 0이 아닌 값은 `TRUE` 0 이며 `FALSE`합니다.

## <a name="see-also"></a>참고 항목
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)