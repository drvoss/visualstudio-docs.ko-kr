---
title: IDebugAsyncOperation::GetResult | Microsoft Docs
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
ms.openlocfilehash: 49cf761c85fce3f8fc2f6705d114ab042e0c2ecd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822047"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
반환 값 및 동기식 디버그 작업에서 반환 된 개체 매개 변수를 제공합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phrResult`  
 [out] 작업이 완료 되 면 `phrResult` 의 반환 값인 `IDebugSyncOperation::Execute`합니다.  
  
 `ppunkResult`  
 [out] 작업이 완료 되 면 `ppunkResult` 작업에서 반환 된 개체 매개 변수입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_PENDING`|작업이 완료 되지 않았습니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드는 반환 된 작업이 완료 되는 경우는 `HRESULT` 개체에서 매개 변수 및 `IDebugSyncOperation::Execute`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugAsyncOperation 인터페이스](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)