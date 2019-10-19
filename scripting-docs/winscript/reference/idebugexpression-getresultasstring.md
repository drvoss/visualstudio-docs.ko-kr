---
title: 'IDebugExpression:: GetResultAsString | Microsoft Docs'
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
ms.openlocfilehash: 56b8f637744227763f55b7c024745d7ae4448b40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573520"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
식 계산 결과를 문자열로 반환 하 고 작업의 반환 값을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phrResult`  
 제한이 작업의 반환 값입니다.  
  
 `pbstrResult`  
 제한이 식 계산의 결과입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_PENDING`|작업이 아직 보류 중입니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 식 계산 결과를 문자열로 반환 하 고 작업의 `HRESULT`을 반환 합니다.  
  
 이 메서드는 `S_OK`을 반환 하 고 `Abort` 작업을 중단 하는 경우 `phrResult` `E_ABORT` 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugExpression 인터페이스](../../winscript/reference/idebugexpression-interface.md)