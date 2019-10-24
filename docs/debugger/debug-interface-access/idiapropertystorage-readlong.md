---
title: 'IDiaPropertyStorage:: ReadLONG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af9d65c571c5e0a281b968d922c9b5170bd1c561
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742898"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
속성 집합에서 `LONG` 값을 읽습니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>매개 변수
 `id`

진행 읽을 속성의 식별자입니다 (`PROPID`은 WTypes. h에서 `ULONG`로 정의 됨).

 `pValue`

제한이 속성 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 속성이 `LONG` 형식이 아니면 `E_INVALIDARG`을 반환 합니다.

## <a name="remarks"></a>주의
 @No__t_0는 Windows에서 32 비트의 부호 있는 정수로 정의 됩니다.

## <a name="see-also"></a>참조
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)