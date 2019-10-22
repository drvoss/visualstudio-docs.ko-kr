---
title: 'IDebugStackFrame:: GetThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetThread
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51cb000ef20877f4f3f6536cc9a01ae44c2810c8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576732"
---
# <a name="idebugstackframegetthread"></a>IDebugStackFrame::GetThread
이 스택 프레임과 연결 된 스레드를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppat`  
 제한이 이 스택 프레임과 연결 된 스레드입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 스택 프레임과 연결 된 스레드를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugStackFrame 인터페이스](../../winscript/reference/idebugstackframe-interface.md)