---
title: BP_RESOLUTION_CODE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dbd9e3d683336d2009e8ff9f02665f7610f988f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915193"
---
# <a name="bpresolutioncode"></a>BP_RESOLUTION_CODE
코드 중단점의 위치를 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _BP_RESOLUTION_CODE {   
   IDebugCodeContext2* pCodeContext;  
} BP_RESOLUTION_CODE;  
```  
  
```csharp  
public struct BP_RESOLUTION_CODE {   
   public IDebugCodeContext2 pCodeContext;  
};  
```  
  
## <a name="members"></a>멤버  
 `pCodeContext`  
 합니다 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 코드에서 중단점의 위치를 식별 하는 개체입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체의 멤버인 합니다 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 설정에의 멤버는 구조를 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 반환한 구조는 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)