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
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977814"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker 인터페이스
지정 된 스레드의 스택 워커를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext 메서드](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|다음 프레임을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 스택 워커 대상 중지 되 고 사용할 수 없습니다. 대상 프로세스가 다시 계속 된 후에 만들 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)