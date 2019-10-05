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
ms.openlocfilehash: dfbb39d10d552141a68d40a7be3f1715a80f8f57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840205"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID 상수
스레드 유형을 지정 하는 데 사용 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>상수  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|현재 실행 중인 스레드입니다.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|기본 스레드입니다. 즉, 스레드는 스크립팅 엔진 인스턴스화 되었습니다.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|모든 스레드입니다.|  
  
## <a name="remarks"></a>설명  
 합니다 `SCRIPTTHREADID` 형식에서 사용 하는 `IActiveScript::GetCurrentScriptThreadID`를 `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, 및 `IActiveScript::InterruptScriptThread`, 상수만 사용할 수 있지만 `IActiveScript::GetScriptThreadState` 및 `IActiveScript::InterruptScriptThread`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)