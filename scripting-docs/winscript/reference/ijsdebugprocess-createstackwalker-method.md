---
title: 'IJsDebugProcess:: CreateStackWalker 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70f5d4885abba3d891526723d3ca1f174549c348
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573833"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker 메서드
Stack walker에 대 한 팩터리 메서드입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `threadId`  
 진행 스레드 ID입니다.  
  
 `ppStackWalker`  
 제한이 새 stack walker 개체입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 스레드에 JavaScript가 없는 경우 E_JsDEBUG_UNKNOWN_THREAD를 반환 합니다. 이 메서드는 대상 프로세스가 중지 되는 동안에만 호출할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugProcess 인터페이스](../../winscript/reference/ijsdebugprocess-interface.md)