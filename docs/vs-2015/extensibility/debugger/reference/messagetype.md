---
title: MESSAGETYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d75b09377797135e03269bf9f0629a6ff0f81b83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739561"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

메시지 유형 및 이유를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>멤버  
 MT_OUTPUTSTRING  
 출력 창에 메시지를 보낼 수 해야 나타냅니다. 이 상호 배타적인에서 `MT_MESSAGEBOX`합니다.  
  
 MT_MESSAGEBOX  
 메시지를 메시지 상자에 표시 됨을 나타냅니다. 이 상호 배타적인에서 `MT_OUTPUTSTRING`합니다.  
  
 MT_TYPE_MASK  
 대상에 메시지를 격리 하는 마스크 값입니다.  
  
 MT_REASON_EXCEPTION  
 예외 결과로 메시지 상자를 표시 되는 것을 나타냅니다. 이 상호 배타적인에서 `MT_REASON_TRACEPOINT`합니다.  
  
 MT_REASON_TRACEPOINT  
 추적점에 도달 하는 결과로 메시지 상자를 표시 되는 것을 나타냅니다. 이 상호 배타적으로 `MT_REASON_EXCEPTION`입니다.  
  
 MT_REASON_MASK  
 표시 되는 메시지에 대 한 이유를 격리 하는 마스크 값입니다.  
  
## <a name="remarks"></a>설명  
 이러한 값이 반환 된 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) 하 고 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) 메서드.  
  
 비트를 사용 하 여 출력 대상 값 중 하나를 사용 하 여 결합할 수 이유 값 중 하나로 `OR`합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

