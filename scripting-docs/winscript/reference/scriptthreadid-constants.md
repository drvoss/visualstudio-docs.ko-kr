---
title: SCRIPTTHREADID 상수 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575660"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID 상수
스레드의 유형을 지정 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>상수  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|현재 실행 중인 스레드입니다.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|기본 스레드입니다. 즉, 스크립팅 엔진이 인스턴스화된 스레드입니다.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|모든 스레드.|  
  
## <a name="remarks"></a>주의  
 @No__t_0 형식은 `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` 및 `IActiveScript::InterruptScriptThread`에서 사용 되지만 상수는 `IActiveScript::GetScriptThreadState` 및 `IActiveScript::InterruptScriptThread` 에서만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)    
 [IActiveScript:: GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)    
 [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)    
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)