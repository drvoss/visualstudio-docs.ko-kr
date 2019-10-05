---
title: 'Idiaaddressmap:: Put_addressmapenabled | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198678"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호 주소 변환할 매핑된 주소를 사용할지 여부를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 NewVal  
 [in] 로 `TRUE` 기호, 번역을 사용 하도록 설정 하려면 또는 `FALSE` 사용 하지 않도록 설정 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 경우에 따라 실행 후 프로세서 실행 파일을 업데이트합니다. DIA 기호 새 레이아웃의 번역 지원 하도록 메커니즘을 포함 합니다.  
  
 PDB 파일이 로드 될 때 파일에 저장 된 매핑된 주소 사용 됩니다. 그러나 클라이언트 응용 프로그램을 호출 하 여 매핑된 자체 주소를 제공 해야 할 수 있습니다 합니다 [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드. 경우는 `set_addressMap` 메서드를 성공적으로, 클라이언트 응용 프로그램을 호출 해야 합니다는 `put_addressMapEnabled` 메서드를 `NewVal` 의 매개 변수 `TRUE` 매핑된 해당 주소를 사용 하도록 설정 하려면.  
  
 매핑된 주소를 사용 하도록 설정의 현재 상태에 대 한 호출을 사용 하 여 검색할 수는 [idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) 메서드.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
