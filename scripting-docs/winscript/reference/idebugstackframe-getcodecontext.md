---
title: 'IDebugStackFrame:: GetCodeContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetCodeContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetCodeContext
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b640238b9c1212f477c6a26a9cc251678758f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574285"
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
스택 프레임과 연결 된 현재 코드 컨텍스트를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppcc`  
 제한이 스택 프레임과 연결 된 코드 컨텍스트입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 스택 프레임과 연결 된 현재 코드 컨텍스트를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugStackFrame 인터페이스](../../winscript/reference/idebugstackframe-interface.md)