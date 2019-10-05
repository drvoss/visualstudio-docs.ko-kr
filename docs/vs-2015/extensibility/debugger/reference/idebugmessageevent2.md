---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e7bb6b014ef8aa662abd42ab2989d47f703880a4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685980"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 메시지를 보내는 사용자에서 응답을 요구 하는 Visual studio 디버그 엔진 (DE)에 의해 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE 사용자 응답을 해야 하는 Visual Studio에 메시지를 보내려면이 인터페이스를 구현 합니다. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 액세스는 `IDebugEvent2` 인터페이스입니다.  
  
 Visual Studio의 호출을 통신 해야 하는이 인터페이스의 구현을 [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) 는 DE 하 합니다. 예를 들어 스레드를 처리 하는 독일의 메시지를 게시 하는 메시지를 사용 하 여이 작업을 수행할 수 있습니다 또는이 인터페이스를 구현 하는 개체 수는 독일에 대 한 참조를 저장 및 콜백할는 DE에 전달 된 응답을 사용 하 여 `IDebugMessageEvent2::SetResponse`입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 DE을 만들어 응답 해야 하는 사용자에 게 메시지를 표시 하려면이 이벤트 개체를 보냅니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버그 중인 프로그램에 연결 될 때 SDM에서 제공 하는 콜백 함수.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugMessageEvent2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|표시할 메시지를 가져옵니다.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|메시지 상자에서 모든 경우에 응답을 설정 합니다.|  
  
## <a name="remarks"></a>설명  
 DE 특정 메시지에 대 한 사용자의 특정 응답이 필요한 경우이 인터페이스를 사용 합니다. 예를 들어 경우는 DE "액세스 거부" 메시지를 원격으로 프로그램에 연결 하려고 시도한 후에 DE이 메시지를 보냅니다 특정 Visual studio에 `IDebugMessageEvent2` 메시지 상자 스타일을 사용 하 여 이벤트 `MB_RETRYCANCEL`합니다. 이 다시 시도 하거나 연결 작업을 취소할 수 있습니다.  
  
 DE Win32 함수의 규칙에 따라 처리할이 메시지는 하는 방법을 지정 `MessageBox` (참조 [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) 세부 정보에 대 한).  
  
 사용 합니다 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 사용자 로부터 응답을 필요로 하지 않는 Visual Studio에 메시지를 보내는 인터페이스입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
