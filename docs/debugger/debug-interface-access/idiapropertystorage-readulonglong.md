---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f365578aba73ed94bdcd1d87801fc53030cfecdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828378"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
읽고 `ULONGLONG` 속성 집합의 값입니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>매개 변수
 `id`

[in] 읽을 속성의 식별자 (`PROPID` 으로 WTypes.h에 정의 된 `ULONG`).

 `pValue`

[out] 속성 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_INVALIDARG` 형식의 속성이 없는 경우 `ULONGLONG`합니다.

## <a name="remarks"></a>설명
 `ULONGLONG` Windows 64 비트 부호 없는 정수로 정의 됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)