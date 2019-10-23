---
title: 'IDiaImageData:: get_imageBase | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743446"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
이미지를 기반으로 하는 메모리 위치를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 제안 된 이미지 기준 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 이미지 기본 충돌로 인해 이미지는 로드 될 때 사용 하지 않는 메모리 위치로 자동으로 주소가 다시 지정할 수 있습니다. 이 메서드는 컴파일 시간에 모듈에 저장 된 기본 힌트 (제안 된 메모리 위치)를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)