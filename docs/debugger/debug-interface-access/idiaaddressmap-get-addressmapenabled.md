---
title: 'Idiaaddressmap:: Get_addressmapenabled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47d0b3ac64724881ab72cb9d9d873bc02f3bec9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938840"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
주소 지도 특정 세션에 대해 설정 되었는지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pRetVal  
 [out] 반환 `TRUE` 주소 매핑을 사용 하는 경우.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 경우에 따라 실행 후 프로세서 실행 파일을 업데이트합니다. DIA 기호 새 레이아웃의 번역 지원 하도록 메커니즘을 포함 합니다.  
  
 클라이언트 응용 프로그램 특정 세션을 가져옴으로써에 매핑된 주소를 설정할 수는 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) 에서 인터페이스를 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 인터페이스를 호출 합니다 [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드를 호출 하 여 여러 번 합니다 [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) 메서드. 합니다 `get_addressMapEnabled` 메서드 호출의 결과 반환 합니다 `put_addressMapEnabled` 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)