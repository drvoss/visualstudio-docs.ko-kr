---
title: 'IDebugExpression:: GetResultAsDebugProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575923"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
식 계산 결과를 디버그 속성으로 반환 하 고 작업의 반환 값을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phrResult`  
 제한이 작업의 반환 값입니다.  
  
 `ppdp`  
 제한이 식에 대 한 debug 속성입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_PENDING`|작업이 아직 보류 중입니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 식 계산 결과를 `IDebugProperty` 및 작업 `HRESULT` 반환 합니다.  
  
 이 메서드는 `S_OK`을 반환 하 고 `Abort` 작업을 중단 하는 경우 `phrResult` `E_ABORT` 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugexpression 인터페이스](../../winscript/reference/idebugexpression-interface.md)    
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)