---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c63cf941bca1965fc4a2e3997f0c0b50ebc44035
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955304"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
지정 하는 데 `DebugPropertyInfo` 필드  
  
## <a name="syntax"></a>구문  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>멤버  
 DBGPROP_INFO_NAME  
 초기화는 `bstrName` 필드입니다.  
  
 DBGPROP_INFO_TYPE  
 초기화는 `bstrType` 필드입니다.  
  
 DBGPROP_INFO_VALUE  
 초기화는 `bstrValue` 필드입니다.  
  
 DBGPROP_INFO_FULLNAME  
 초기화는 `bstrFullName` 필드입니다.  
  
 DBGPROP_INFO_ATTRIBUTES  
 초기화는 `dwAttrib` 필드입니다.  
  
 DBGPROP_INFO_DEBUGPROP  
 초기화 된 `pDebugProp` 포함 된 필드는 `IDebugProperty` 인터페이스입니다.  
  
 DBGPROP_INFO_AUTOEXPAND  
 값 필드는이 형식의 개체에 대 한 사용 가능한 경우 자동 확장 값이 포함 됩니다 지정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [DebugPropertyInfo 구조체](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)