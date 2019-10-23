---
title: 'IDiaImageData:: get_virtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_virtualAddress method
ms.assetid: 67ecdc8c-d342-4d0b-b02a-c6b88e22fd02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 414e065cd9e772e74c573b51bf52f11bcb987b6d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743419"
---
# <a name="idiaimagedataget_virtualaddress"></a>IDiaImageData::get_virtualAddress
이미지의 가상 메모리에서 위치를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 이미지의 가상 주소를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)