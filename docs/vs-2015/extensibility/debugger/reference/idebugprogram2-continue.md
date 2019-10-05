---
title: IDebugProgram2::Continue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f28379d202a59ca2bdf9bfc7eb1185dee343accf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426290"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중지 된 상태에서이 프로그램 실행을 계속 합니다. 이전 실행 상태 (예: 단계)은 유지, 프로그램이 다시 실행을 시작 하 고 있습니다.  
  
> [!NOTE]
> 이 메서드는 사용 되지 않습니다. 사용 된 [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드 대신 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 스레드를 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 디버깅 중인 프로그램 수 또는 중지 이벤트를 생성 하는 프로그램에 관계 없이이 프로그램에서 호출 됩니다. 구현 (예: 단계)를 실행 상태로 유지 하 고 이전 실행을 완료 하기 전에 중지 되지 것 처럼 계속 실행 해야 합니다. 즉,이 프로그램에서 스레드 건너뛰기 작업을 수행 중 이었던 작업 및 다른 프로그램 중지 하 고이 메서드를 호출한 다음 중지 되었습니다, 프로그램이 원래 건너뛰기 작업을 완료 해야 합니다.  
  
> [!WARNING]
> Stopping 이벤트 또는 직접 (동기) 이벤트를 전송 하지 마십시오 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 이 호출을 처리 하는 동안 그렇지 않은 경우 디버거가 중단 될 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
