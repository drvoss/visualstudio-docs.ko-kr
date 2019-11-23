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
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572586"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
`DebugPropertyInfo` 필드를 지정 하는 데 사용 됩니다.  
  
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
 `bstrName` 필드를 초기화 합니다.  
  
 DBGPROP_INFO_TYPE  
 `bstrType` 필드를 초기화 합니다.  
  
 DBGPROP_INFO_VALUE  
 `bstrValue` 필드를 초기화 합니다.  
  
 DBGPROP_INFO_FULLNAME  
 `bstrFullName` 필드를 초기화 합니다.  
  
 DBGPROP_INFO_ATTRIBUTES  
 `dwAttrib` 필드를 초기화 합니다.  
  
 DBGPROP_INFO_DEBUGPROP  
 `IDebugProperty` 인터페이스를 포함 하는 `pDebugProp` 필드를 초기화 합니다.  
  
 DBGPROP_INFO_AUTOEXPAND  
 값 필드에이 형식의 개체에 대 한 자동 확장 값 (사용 가능한 경우)을 포함 하도록 지정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [DebugPropertyInfo 구조체](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)