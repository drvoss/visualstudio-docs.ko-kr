---
title: 'IDiaPropertyStorage:: ReadBOOL | Microsoft Docs'
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
ms.openlocfilehash: d776e37bab189e61d0264f4cbda24f89cb4501ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742933"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
속성 집합에서 `BOOL` 값을 읽습니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>매개 변수
 `id`

진행 읽을 속성의 식별자입니다 (`PROPID`은 WTypes. h에서 `ULONG`로 정의 됨).

 `pValue`

제한이 속성 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 속성이 `BOOL` 형식이 아니면 `E_INVALIDARG`을 반환 합니다.

## <a name="remarks"></a>주의
 일관 된 결과를 위해 `BOOL` 값을 해석 하 여 0이 아닌 값이 `TRUE` 되 고 0이 `FALSE` 됩니다.

## <a name="see-also"></a>참조
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)