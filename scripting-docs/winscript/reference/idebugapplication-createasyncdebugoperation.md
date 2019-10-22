---
title: 'IDebugApplication:: CreateAsyncDebugOperation | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575567"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
지정 된 동기 디버그 작업에 대 한 비동기 액세스를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psdo`  
 진행 동기 디버그 작업 개체입니다.  
  
 `ppado`  
 제한이 비동기 디버그 작업 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드를 사용 하면 언어 엔진이 명시적으로 디버거 스레드와 동기화 하지 않고도 식을 비동기적으로 평가할 수 있습니다. 자세한 내용은 [IDebugSyncOperation interface](../../winscript/reference/idebugsyncoperation-interface.md) And [IDebugAsyncOperation interface](../../winscript/reference/idebugasyncoperation-interface.md)를 참조 하세요.  
  
## <a name="see-also"></a>참조  
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)    
 [IDebugSyncOperation 인터페이스](../../winscript/reference/idebugsyncoperation-interface.md)    
 [IDebugAsyncOperation 인터페이스](../../winscript/reference/idebugasyncoperation-interface.md)