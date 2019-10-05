---
title: IDiaPropertyStorage::ReadBSTR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0bff81499fe8ea66ce5d4f50616adfec44d3002
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839630"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
읽고 `BSTR` 속성 집합의 값입니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>매개 변수
 `id`

[in] 읽을 속성의 식별자 (`PROPID` 으로 WTypes.h에 정의 된 `ULONG`).

 `pValue`

[out] 속성 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_INVALIDARG` 형식의 속성이 없는 경우 `BSTR`합니다.

## <a name="remarks"></a>설명
 `BSTR` 0으로 끝나는 와이드 문자열로 Windows에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)