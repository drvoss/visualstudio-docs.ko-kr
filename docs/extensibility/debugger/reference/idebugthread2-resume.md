---
title: IDebugThread2::Resume | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f41f26c824a779133a335c0d3d5080373b791d06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920991"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
스레드의 실행을 다시 시작합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdwSuspendCount`  
 [out] 작업을 다시 시작 후 일시 중단 횟수를 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드 감소를 호출할 때마다 일시 중단 횟수가 실행이 실제로 다시 시작 될 때 0에 도달할 때까지 합니다. 이 일시 중단 횟수가 표시 됩니다는 **스레드** 디버그 창입니다.  
  
 이 메서드를 호출할 때마다 이전 호출 있어야 합니다 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) 메서드. 일시 중단 횟수가 결정 횟수는 `IDebugThread2::Suspend` 지금 메서드가 호출 되었습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)