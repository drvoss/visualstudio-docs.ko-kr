---
title: 'IDebugAsyncOperation:: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573303"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
작업을 취소 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|S_OK|메서드가 성공했으며|  
|E_NOTIMPL|작업을 취소할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 일반적으로 디버거 스레드 내에서 호출 되어 응답 하지 않는 작업을 취소 합니다. 이 메서드는 `IDebugSyncOperation` 개체에 대 한 `InProgressAbort` 메서드를 호출 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugAsyncOperation 인터페이스](../../winscript/reference/idebugasyncoperation-interface.md)    
 [IDebugAsyncOperation:: Start](../../winscript/reference/idebugasyncoperation-start.md)    
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)