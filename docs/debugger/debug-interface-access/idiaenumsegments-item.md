---
title: 'IDiaEnumSegments:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101821e3c00d3aeac9b131ee5a11ab9a01e090a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744177"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
인덱스를 사용 하 여 세그먼트를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>매개 변수
 인덱스입니다.

진행 검색할 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 개체의 인덱스입니다. 인덱스의 범위는 0 ~ `count`-1입니다. 여기서 `count`는 [IDiaEnumSegments:: get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) 메서드에서 반환 됩니다.

 세그먼트

제한이 원하는 세그먼트를 나타내는 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)