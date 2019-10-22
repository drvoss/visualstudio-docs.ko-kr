---
title: 'IActiveScript:: GetScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575700"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
지정 된 Win32 스레드와 연결 된 스레드의 스크립팅 엔진 정의 식별자를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwWin32ThreadID` ,  
 진행 현재 프로세스에서 실행 중인 Win32 스레드의 스레드 식별자입니다. [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) 함수를 사용 하 여 현재 실행 중인 스레드의 스레드 식별자를 검색 합니다.  
  
 `pstidThread` ,  
 제한이 지정 된 Win32 스레드와 연결 된 스크립트 스레드 식별자를 수신 하는 변수의 주소입니다. 이 식별자의 해석은 스크립팅 엔진으로 유지 되지만 Windows 스레드 식별자의 복사본 일 수도 있습니다. Win32 스레드가 종료 되 면이 식별자가 할당 해제 되 고 이후에 다른 스레드에 할당 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출을 수행할 수 없습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았기 때문에 실패 했습니다.|  
  
## <a name="remarks"></a>주의  
 검색 된 식별자는 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 메서드와 같은 스크립트 스레드 실행 제어 메서드에 대 한 후속 호출에서 사용할 수 있습니다.  
  
 이 메서드는 기본이 아닌 스레드에서 개체를 호스트 하거나 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 인터페이스를 호스트 하는 기본이 아닌 스레드에서 호출 될 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)