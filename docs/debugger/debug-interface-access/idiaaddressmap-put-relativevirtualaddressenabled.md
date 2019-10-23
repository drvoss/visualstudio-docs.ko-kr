---
title: IDiaAddressMap::p ut_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d733a51bd599b85dcc6d1121b8d21e1a687a351
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745039"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
클라이언트에서 RVA (상대 가상 주소)의 계산과 사용을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

## <a name="syntax"></a>구문

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>매개 변수
 NewVal

진행 @No__t_0로 설정 `FALSE` 하거나 사용 하지 않도록 설정 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 DIA 인터페이스에서 설명 하는 디버그 개체의 주소와 실행 파일의 이미지 기반에 대 한 주소는 상대 가상 주소로 검색할 수 있습니다.

 Rva는 처음에 PDB 파일에서 세그먼트가 로드 될 때 사용할 수 있습니다. Rva 사용의 현재 상태를 가져오려면 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) 메서드를 호출 합니다.

 [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 메서드에 대 한 호출이 성공한 후에 rva를 사용 하도록 설정 하려면 `put_relativeVirtualAddress` 메서드를 호출 하 여 새 이미지 헤더를 설정 해야 합니다.

## <a name="see-also"></a>참조
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)