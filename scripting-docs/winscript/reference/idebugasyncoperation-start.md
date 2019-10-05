---
title: IDebugAsyncOperation::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821930"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
비동기 작업을 시작 하면 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `padocb`  
 이 작업에서 상태 이벤트를 수신 하는 콜백 인터페이스입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_UNEXPECTED`|작업이 이미 보류 중입니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드를 사용 하면 `IDebugSyncOperation::Execute` 에서 가져온 스레드에서 비동기적으로 호출할 `IDebugSyncOperation::GetTargetThread`합니다. 이 메서드를 디버거 스레드; 내 에서만 호출 해야 그렇지 않은 경우 작업이 완료 될 때까지 반환 하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation 인터페이스](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)