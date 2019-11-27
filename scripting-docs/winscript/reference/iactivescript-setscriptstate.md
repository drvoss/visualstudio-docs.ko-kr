---
title: 'IActiveScript:: SetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577999"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
지정 된 상태에 스크립팅 엔진을 배치 합니다. 이 메서드는 기본이 아닌 스레드에서 개체를 호스트 하거나 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스를 호스트 하는 경우를 제외 하 고는 기본이 아닌 스레드에서 호출 될 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ss`  
 진행 스크립팅 엔진을 지정 된 상태로 설정 합니다. [Scriptstate 열거형](../../winscript/reference/scriptstate-enumeration.md) 열거형에 정의 된 값 중 하나일 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_FAIL`|스크립팅 엔진은 초기화 된 상태로 다시 전환 하는 것을 지원 하지 않습니다. 호스트에서이 스크립팅 엔진을 삭제 하 고 새 스크립팅 엔진을 만들고 초기화 하 고 로드 하 여 동일한 결과를 얻습니다.|  
|`E_UNEXPECTED`|호출을 수행할 수 없습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았기 때문에 실패 했습니다.|  
|`OLESCRIPT_S_PENDING`|메서드가 성공적으로 큐에 대기 되었지만 상태가 아직 변경 되지 않았습니다. 상태가 변경 되 면 사이트는 [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 메서드를 통해 다시 호출 됩니다.|  
|`S_FALSE`|메서드가 성공 했지만 스크립트가 이미 지정 된 상태에 있습니다.|  
  
## <a name="remarks"></a>주의  
 스크립팅 엔진 상태에 대 한 자세한 내용은 [Windows 스크립트](../../winscript/windows-script-engines.md) 엔진의 스크립트 엔진 상태 섹션을 참조 하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)