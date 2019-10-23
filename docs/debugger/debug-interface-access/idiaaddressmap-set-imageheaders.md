---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft Docs'
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
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745007"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
상대 가상 주소 변환을 사용 하도록 이미지 헤더를 설정 합니다.

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

진행 헤더 데이터의 바이트 수입니다. @No__t_0 이어야 합니다. 여기서 `n`은 실행 파일의 섹션 헤더 수입니다.

 데이터[]

진행 이미지 헤더로 사용할 `IMAGE_SECTION_HEADER` 구조체의 배열입니다.

 originalHeaders

진행 이미지 머리글이 새 이미지에서 가져온 경우 `FALSE`로 설정 하 고, 업그레이드 전에 원래 이미지를 반영 하는 경우 `TRUE` 합니다. 일반적으로이는 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드에 대 한 호출과 함께만 `TRUE`로 설정 됩니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 @No__t_0 구조체는 Winnt.exe에서 선언 되 고 실행 파일의 이미지 섹션 헤더 형식을 나타냅니다.

 상대 가상 주소 계산은 `IMAGE_SECTION_HEADER` 값에 따라 달라 집니다. 일반적으로 DIA는 프로그램 데이터베이스 (.pdb) 파일에서이 파일을 검색 합니다. 이러한 값이 누락 된 경우 DIA는 상대 가상 주소를 계산할 수 없으며 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) 메서드는 `FALSE`를 반환 합니다. 그런 다음 클라이언트는 [IDiaAddressMap::P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) 메서드를 호출 하 여 이미지 자체에서 누락 된 이미지 헤더를 제공한 후 상대 가상 주소 계산을 사용 하도록 설정 해야 합니다.

## <a name="see-also"></a>참조
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)