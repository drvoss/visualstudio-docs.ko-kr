---
title: IDebugThread2::Resume | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152986"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

스레드의 실행을 다시 시작합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
