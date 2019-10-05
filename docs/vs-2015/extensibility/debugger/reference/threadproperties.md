---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204815"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

스레드 속성을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>멤버  
 dwFields  
 플래그의 조합을 합니다 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) 이 구조의 필드는 유효한 설명 하는 열거형입니다.  
  
 dwThreadId  
 스레드 id입니다.  
  
 dwSuspendCount  
 스레드 수를 일시 중단 합니다.  
  
 dwThreadState  
 값을 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) 운영 스레드의 상태를 나타내는 열거형입니다.  
  
 bstrPriority  
 스레드 우선 순위;를 지정 하는 문자열 예를 들어, "위에 Normal", "Normal" 또는 "시간이 중요 한"입니다.  
  
 bstName  
 스레드 이름입니다.  
  
 bstrLocation  
 일반적으로 실행이 중단 현재 메서드의 이름으로 표시 된 스레드 위치 (일반적으로 최상위 스택 프레임)입니다.  
  
## <a name="remarks"></a>설명  
 이 구조에 대 한 호출에 의해 채워진 합니다 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 메서드. 따라서 반환 된 정보는 일반적으로 채우는 사용 합니다 **스레드** 창입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
