---
title: EX_DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EX_DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0094d49a7e528d312dc8206b02599651f192c6fb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575848"
---
# <a name="ex_dbgprop_info_flags"></a>EX_DBGPROP_INFO_FLAGS
`ExtendedDebugPropertyInfo` 필드를 지정 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## <a name="members"></a>멤버  
 EX_DBGPROP_INFO_ID  
 속성에 대 한 식별자를 초기화 합니다.  
  
 EX_DBGPROP_INFO_NTYPE  
 속성의 형식을 초기화 합니다.  
  
 EX_DBGPROP_INFO_NVALUE  
 속성의 값을 초기화 합니다.  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 `plb` 필드를 초기화 합니다.  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 `IDebugExtendedProperty` 인터페이스를 포함 하는 `pDebugExtProp` 필드를 초기화 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ExtendedDebugPropertyInfo 구조체](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty 인터페이스](../../winscript/reference/idebugextendedproperty-interface.md)