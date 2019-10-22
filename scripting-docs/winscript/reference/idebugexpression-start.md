---
title: 'IDebugExpression:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576439"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
식의 계산을 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdecb`  
 진행 식 계산이 완료 된 경우를 나타내는 콜백입니다. 이 매개 변수를 `NULL` 하면 이벤트가 발생 하지 않으며 클라이언트는 `QueryIsComplete`를 사용 하 여 식 상태를 폴링해야 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 식의 계산을 시작 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugexpression:: Abort](../../winscript/reference/idebugexpression-abort.md)    
 [IDebugExpression 인터페이스](../../winscript/reference/idebugexpression-interface.md)