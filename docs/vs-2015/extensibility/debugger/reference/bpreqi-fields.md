---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8ad9e4b6d83ebc05c78a8b84c0c06e00d7563bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153222"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중단점 요청에 대 한 검색할 정보를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>멤버  
 BPREQI_BPLOCATION  
 초기화/사용 합니다 `bpLocation` (중단점 위치) 필드를 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 또는 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조입니다.  
  
 BPREQI_LANGUAGE  
 초기화/사용 된 `guidLanguage` 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_PROGRAM  
 초기화/사용 된 `pProgram` 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_PROGRAMNAME  
 초기화/사용 된 `bstrProgramName` 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_THREAD  
 초기화/사용 된 `pThread` 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_THREADNAME  
 초기화/사용 된 `bstrThreadName` 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_PASSCOUNT  
 초기화/사용 된 `bpPassCount` 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_CONDITION  
 초기화/사용 합니다 `bpCondition` (중단점 조건) 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_FLAGS  
 초기화/사용 된 `dwFlags` 필드를 `BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_ALLOLDFIELDS  
 초기화/사용에 대 한 모든 필드의의 `BP_REQUEST_INFO` 구조입니다.  
  
 BPREQI_VENDOR  
 초기화/사용 된 `guidVendor` 필드에 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_CONSTRAINT  
 초기화/사용 된 `bstrConstraint` 필드에 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_TRACEPOINT  
 초기화/사용 된 `bstrTracepoint` 필드에 `BP_REQUEST_INFO2` 구조입니다.  
  
 BPREQI_ALLFIELDS  
 에 대 한 모든 필드를 지정 합니다 `BP_REQUEST_INFO2` 구조입니다.  
  
## <a name="remarks"></a>설명  
 인수로 전달 합니다 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 및 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 의 필드를 지정 하는 방법의 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) 구조체가 초기화 되어야 합니다.  
  
 이러한 플래그는의 필드를 나타내는 데 또한 합니다 `BP_REQUEST_INFO` 및 `BP_REQUEST_INFO2` 구조는 유효 하 고 사용 되는 각 구조에 반환 되 면 합니다.  
  
 이러한 값을 비트 결합할 수 있습니다 `OR`합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
