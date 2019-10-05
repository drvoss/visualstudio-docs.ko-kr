---
title: IDebugProcess3::Continue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e7167a5425566936c196960d5014fcf5d7c8709
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405827"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

계속 중지 된 상태에서이 프로세스를 실행 합니다. 이전 실행 상태 (예: 단계)은 유지, 프로세스를 다시 실행을 시작 합니다.  
  
> [!NOTE]
> 이 메서드를 대신 사용 해야 [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
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
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 계속 실행 되어야 하는 스레드를 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 디버깅 중인 프로세스 또는 중지 이벤트를 생성 하는 프로세스에 관계 없이이 프로세스에서 호출 됩니다. 구현 (예: 단계)를 실행 상태로 유지 하 고 이전 실행을 완료 하기 전에 중지 되지 것 처럼 계속 실행 해야 합니다. 즉, 경우에 스레드가이 프로세스 건너뛰기 작업을 수행 중 이었던 작업 및 일부 다른 프로세스가 중지, 중지 되었습니다 차례로 `Continue` 가 호출 되 면 지정 된 스레드는 원래 건너뛰기 작업을 완료 해야 합니다.  
  
 **경고** stopping 이벤트 또는 직접 (동기) 이벤트를 전송 하지 마십시오 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 이 호출을 처리 하는 동안 그렇지 않은 경우 디버거가 중단 될 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
