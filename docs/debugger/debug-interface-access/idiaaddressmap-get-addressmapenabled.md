---
title: 'IDiaAddressMap:: get_addressMapEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b518cf3728279ea8db267d01867fa66ceae35b21
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745188"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
특정 세션에 대 한 주소 맵이 설정 되었는지 여부를 나타냅니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 pRetVal

제한이 주소 매핑을 사용 하는 경우 `TRUE`를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 실행 가능 사후 프로세서는 때때로 실행 파일을 업데이트 합니다. DIA에는 기호를 새 레이아웃으로 변환할 수 있도록 지 원하는 메커니즘이 포함 되어 있습니다.

 클라이언트 응용 프로그램은 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 인터페이스에서 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) 인터페이스를 가져오고 다음에 대 한 호출 [을 통해 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드를 호출 하 여 특정 세션에 대 한 주소 맵을 설정할 수 있습니다. IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) 메서드입니다. `get_addressMapEnabled` 메서드는 `put_addressMapEnabled` 메서드를 호출한 결과를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)