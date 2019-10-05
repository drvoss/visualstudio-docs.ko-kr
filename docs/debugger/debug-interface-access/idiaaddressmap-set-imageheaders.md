---
title: 'Idiaaddressmap:: Set_imageheaders | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10835f422f8d2d116234eadd91da0d27c424f314
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554224"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
집합에는 상대 가상 주소 변환을 사용 하도록 설정 하는 헤더 이미지입니다.

## <a name="syntax"></a>구문

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>매개 변수
 cbData

[in] 헤더 데이터의 바이트 수입니다. 여야 `n*sizeof(IMAGE_SECTION_HEADER)` 여기서 `n` 실행 파일의 섹션 헤더입니다.

 데이터[]

[in] 배열을 `IMAGE_SECTION_HEADER` 이미지 헤더로 사용할 구조입니다.

 originalHeaders

[in] 로 `FALSE` 새 이미지에서 이미지 헤더 경우 `TRUE` 를 업그레이드 하기 전에 원본 이미지를 반영 합니다. 일반적으로이 설정 됩니다 `TRUE` 조합에 대 한 호출 에서만 합니다 [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 `IMAGE_SECTION_HEADER` 구조 Winnt.h에서 선언 및 실행 파일의 이미지 섹션 헤더 형식을 나타냅니다.

 상대 가상 주소 계산에 종속 된 `IMAGE_SECTION_HEADER` 값입니다. 일반적으로 DIA 프로그램 데이터베이스 (.pdb) 파일에서이 검색합니다. 이 값은 누락 된 DIA 수 없는 경우 상대 가상 주소를 계산 하 고 [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) 메서드가 반환 되는 `FALSE`합니다. 클라이언트 호출 해야 합니다 [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) 이미지 자체에서 누락 된 이미지 헤더를 입력 한 후 상대 가상 주소 계산을 사용 하도록 설정 하는 방법입니다.

## <a name="see-also"></a>참고 항목
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)