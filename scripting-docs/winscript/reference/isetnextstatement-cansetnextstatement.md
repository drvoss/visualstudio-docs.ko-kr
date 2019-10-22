---
title: 'ISetNextStatement:: CanSetNextStatement | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56cf0b2e4afd7a86a087b37be4b23758a5b59720
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571848"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
이 메서드는 실행 될 코드의 다음 문을 결정 하는 실행 지점을 지정 된 위치로 설정할 수 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStackFrame`  
 진행 스택 프레임 개체에 대 한 포인터입니다.  
  
 `pCodeContext`  
 진행 코드 컨텍스트 개체에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|다음 문을 지정 된 코드 컨텍스트로 업데이트할 수 있습니다.|  
|`S_FALSE`|다음 문을 지정 된 코드 컨텍스트로 업데이트할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [ISetNextStatement 인터페이스](../../winscript/reference/isetnextstatement-interface.md)