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
ms.openlocfilehash: 086a2b7544a95a302219ddc62c15c5b31dd1d9b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955238"
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
지정 하는 데 `ExtendedDebugPropertyInfo` 필드입니다.  
  
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
 속성에 대 한 식별자를 초기화합니다.  
  
 EX_DBGPROP_INFO_NTYPE  
 초기화 속성의 형식입니다.  
  
 EX_DBGPROP_INFO_NVALUE  
 속성의 값을 초기화합니다.  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 초기화는 `plb` 필드입니다.  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 초기화 된 `pDebugExtProp` 포함 된 필드는 `IDebugExtendedProperty` 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [ExtendedDebugPropertyInfo 구조체](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty 인터페이스](../../winscript/reference/idebugextendedproperty-interface.md)