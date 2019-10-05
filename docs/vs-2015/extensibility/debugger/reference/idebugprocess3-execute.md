---
title: IDebugProcess3::Execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8b6647db9e3a013be0ffd3a0a12f92e9cb6cc738
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405815"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

계속 중지 된 상태에서이 프로세스를 실행 합니다. 이전 실행 상태 (예: 단계)를 지우고 다시 실행 프로세스를 시작 합니다.  
  
> [!NOTE]
> 이 메서드를 대신 사용 해야 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 스레드의 실행을 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 다른 프로세스의 스레드 중지 된 상태에서 실행을 시작할 때이 메서드는이 프로세스에서 호출 됩니다. 이 또한 메서드는 사용자가 선택 합니다 **시작** 명령을 합니다 **디버그** IDE의 메뉴. 이 메서드의 구현을 호출 처럼 간단할 수 있습니다 합니다 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 프로세스에서 현재 스레드에서 메서드.  
  
> [!WARNING]
> Stopping 이벤트 또는 직접 (동기) 이벤트를 전송 하지 마십시오 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 이 호출을 처리 하는 동안 그렇지 않은 경우 디버거가 중단 될 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [다시 시작](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
