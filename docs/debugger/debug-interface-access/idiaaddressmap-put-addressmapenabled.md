---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745060"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
주소 맵을 사용 하 여 기호 주소를 변환 해야 하는지 여부를 지정 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>매개 변수
 NewVal

진행 @No__t_0로 설정 하 여 기호를 변환 하거나 `FALSE` 사용 하지 않도록 설정 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 실행 가능 사후 프로세서는 때때로 실행 파일을 업데이트 합니다. DIA에는 기호를 새 레이아웃으로 변환할 수 있도록 지 원하는 메커니즘이 포함 되어 있습니다.

 PDB 파일이 로드 될 때 파일에 저장 된 주소 맵을 사용할 수 있습니다. 그러나 클라이언트 응용 프로그램에서 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드를 호출 하 여 자체 주소 맵을 제공 해야 하는 경우도 있습니다. @No__t_0 메서드가 성공적으로 수행 되 면 클라이언트 응용 프로그램은 `TRUE`의 `NewVal` 매개 변수를 사용 하 여 `put_addressMapEnabled` 메서드를 호출 하 여 해당 주소 맵을 사용할 수 있도록 해야 합니다.

 사용할 수 있는 주소 맵의 현재 상태는 [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) 메서드를 호출 하 여 검색할 수 있습니다.

## <a name="see-also"></a>참조
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)