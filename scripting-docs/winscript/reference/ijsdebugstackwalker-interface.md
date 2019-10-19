---
title: IJsDebugStackWalker 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574012"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker 인터페이스
지정 된 스레드에 대 한 스택 walker 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|name|설명|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext 메서드](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|다음 프레임을 가져옵니다.|  
  
## <a name="remarks"></a>주의  
 Stack 워커은 대상이 중지 된 동안에만 만들 수 있으며 대상 프로세스가 다시 계속 되 면 유효 하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)