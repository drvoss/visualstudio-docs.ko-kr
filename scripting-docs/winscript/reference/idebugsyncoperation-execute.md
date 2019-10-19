---
title: 'IDebugSyncOperation:: Execute | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25da02e6736cc2f8ac27c82f922bd515e791bef1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576690"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
작업을 동기적으로 수행 하 고를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppunkResult`  
 제한이 작업에서 반환 된 개체 매개 변수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_ABORT`|@No__t_0 메서드를 호출 하 여 작업이 중단 되었습니다.|  
  
## <a name="remarks"></a>주의  
 대상 스레드의 프로세스 디버그 관리자는 `Execute` 메서드를 동기적으로 호출 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugSyncOperation 인터페이스](../../winscript/reference/idebugsyncoperation-interface.md)