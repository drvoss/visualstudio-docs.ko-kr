---
title: 'IDebugAsyncOperation:: GetResult | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573290"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
동기 디버그 작업의 반환 값 및 반환 개체 매개 변수를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phrResult`  
 제한이 작업이 완료 되 면 `phrResult`은 `IDebugSyncOperation::Execute`의 반환 값입니다.  
  
 `ppunkResult`  
 제한이 작업이 완료 되 면 작업에서 반환 된 개체 매개 변수 `ppunkResult`입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_PENDING`|작업이 완료 되지 않았습니다.|  
  
## <a name="remarks"></a>주의  
 작업이 완료 되 면이 메서드는 `IDebugSyncOperation::Execute`에서 `HRESULT` 및 개체 매개 변수를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugAsyncOperation 인터페이스](../../winscript/reference/idebugasyncoperation-interface.md)    
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)