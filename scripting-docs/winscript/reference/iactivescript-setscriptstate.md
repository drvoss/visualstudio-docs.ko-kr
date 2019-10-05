---
title: 'Iactivescript:: Setscriptstate | Microsoft Docs'
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
ms.openlocfilehash: 16a13b545ddd482f8aa143d289d46447370e23ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935533"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
지정 된 상태로 스크립팅 엔진을 넣습니다. 호스트 개체 또는 기본이 아닌 설명선 발생 하지 않고 기본이 아닌 스레드에서이 메서드를 호출할 수는 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ss`  
 [in] 스크립팅 엔진의 지정 된 상태로 설정합니다. 에 정의 된 값 중 하나일 수 있습니다 합니다 [SCRIPTSTATE 열거형](../../winscript/reference/scriptstate-enumeration.md) 열거형입니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_FAIL`|스크립팅 엔진이 초기화 된 상태로 다시 전환을 지원 하지 않습니다. 호스트 해야이 스크립팅 엔진 삭제 및 만들기, 초기화 및 동일한 효과 달성 하기 위해 새 스크립팅 엔진을 로드 합니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화) 하므로 실패 합니다.|  
|`OLESCRIPT_S_PENDING`|메서드가 성공적으로 대기 하지만 상태가 아직 변경 되지 않습니다. 경우에 상태 변경을 사이트 들은 통해 합니다 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 메서드.|  
|`S_FALSE`|메서드 했지만 지정 된 상태로 이미 스크립트.|  
  
## <a name="remarks"></a>설명  
 스크립팅 엔진 상태에 대 한 자세한 내용은 스크립트 엔진 상태 섹션을 참조 하세요 [Windows 스크립트 엔진](../../winscript/windows-script-engines.md) 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)