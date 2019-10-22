---
title: 'IDebugAsyncOperation:: QueryIsComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51bbfa6a19a247f378a0408e250651c94219fcb5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573257"
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
디버그 작업이 완료 되었는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|작업이 완료 되었습니다.|  
|`S_FALSE`|작업이 완료 되지 않았습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 디버그 작업이 완료 되었는지 여부를 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugAsyncOperation 인터페이스](../../winscript/reference/idebugasyncoperation-interface.md)