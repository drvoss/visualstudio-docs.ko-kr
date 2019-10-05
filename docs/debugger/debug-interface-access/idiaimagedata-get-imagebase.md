---
title: 'Idiaimagedata:: Get_imagebase | Microsoft Docs'
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
ms.openlocfilehash: de8c333391530cd86c6fc66a8e6c36ce8cfecd5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829066"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
여기서 이미지를 기반으로 하는 메모리 위치를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 이미지 제안 된 기본 값을 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이미지 기본 충돌로 인해 이미지 수 기준 주소를 지정할 자동으로 사용 되지 않는 메모리 위치에 로드 되는 경우. 이 메서드는 컴파일 시 모듈에 저장 된 기본 힌트 (제안 된 메모리 위치)를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)