---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84255e364630245564a0cbab5d38c6dff38df0a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978474"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
문자열 작업의 반환 값을 식 평가의 결과 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phrResult`  
 [out] 작업의 반환 값입니다.  
  
 `pbstrResult`  
 [out] 식 계산의 결과입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_PENDING`|작업이 여전히 보류 중입니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드가 작업의 문자열을 식 평가의 결과 반환 합니다. `HRESULT`합니다.  
  
 이 메서드는 반환 `S_OK` 하 고 `phrResult` 반환 `E_ABORT` 경우 `Abort` 작업을 중단 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugExpression 인터페이스](../../winscript/reference/idebugexpression-interface.md)