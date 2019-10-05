---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204806"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

스레드에 대 한 정보를 검색할 수를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>멤버  
 TPF_ID  
 초기화/사용 된 `dwThreadId` 필드를 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 구조입니다.  
  
 TPF_SUSPENDCOUNT  
 초기화/사용 합니다 `dwSuspendCount` 필드는 `THREADPROPERTIE`S 구조입니다.  
  
 TPF_STATE  
 초기화/사용 합니다 `dwThreadState` 필드는 `THREADPROPERTIE`S 구조입니다.  
  
 TPF_PRIORITY  
 초기화/사용 합니다 `bstrPriority` 필드는 `THREADPROPERTIE`S 구조입니다.  
  
 TPF_NAME  
 초기화/사용 합니다 `bstrName` 필드는 `THREADPROPERTIE`S 구조입니다.  
  
 TPF_LOCATION  
 초기화/사용 합니다 `bstrLocation` 필드는 `THREADPROPERTIE`S 구조입니다.  
  
 TPF_ALLFIELDS  
 모든 필드를 지정합니다.  
  
## <a name="remarks"></a>설명  
 이러한 값을 인수로 전달 됩니다는 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 의 필드를 나타내려면 메서드는 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 구조는 초기화할 합니다.  
  
 이러한 값에도 사용 됩니다 `dwFields` 의 멤버는 `THREADPROPERTIES` 에 유효 하 고 사용 되는 필드는 구조체.  
  
 이러한 플래그는 비트과 결합 될 수 `OR`입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
