---
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c514f43f39f0b002da0f01b1804120b98530990b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182944"
---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중단점을 구현 하는 데 필요한 정보를 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```csharp  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## <a name="members"></a>멤버  
 `dwFields`  
 플래그의 조합 된 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 채워진 필드를 지정 하는 열거형입니다.  
  
 `guidLanguage`  
 언어 GUID입니다.  
  
 `bpLocation`  
 합니다 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 중단점 위치 유형을 지정 하는 구조입니다.  
  
 `pProgram`  
 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 중단점이 발생 하는 응용 프로그램을 나타내는 개체입니다.  
  
 `bstrProgramName`  
 중단점이 발생 하는 응용 프로그램의 이름입니다.  
  
 `pThread`  
 합니다 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 중단점이 발생 하는 스레드를 나타내는 개체입니다.  
  
 `bstrThreadName`  
 중단점이 발생 하는 스레드의 이름입니다.  
  
 `bpCondition`  
 합니다 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 중단점은 발생 하는 조건을 설명 하는 구조입니다.  
  
 `bpPassCount`  
 합니다 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 중단점의 패스 개수 정보가 포함 된 구조체입니다.  
  
 `dwFlags`  
 플래그의 조합을 합니다 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 요청 된 중단점에 대 한 플래그를 지정 하는 열거형입니다.  
  
## <a name="remarks"></a>설명  
 이 구조에서 반환 되는 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 메서드.  
  
 중단점 제약 조건 또는 추적점을이 참조는 디버그 엔진 공급 업체 GUID를 가져올 해야 할 경우는 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
