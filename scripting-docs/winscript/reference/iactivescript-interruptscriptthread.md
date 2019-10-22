---
title: 'IActiveScript:: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577262"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
실행 중인 스크립트 스레드 (이벤트 싱크, 즉시 실행 또는 매크로 호출)의 실행을 중단 합니다. 이 메서드를 사용 하 여 중단 된 스크립트 (예: 무한 루프)를 종료할 수 있습니다. 기본이 아닌 스레드에서 개체를 호스트 하거나 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 메서드를 호스트 하는 기본이 아닌 스레드에서 호출 될 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `stidThread`  
 진행 중단할 스레드의 식별자 이거나 다음 특수 스레드 식별자 값 중 하나입니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|모든 스레드. 현재 진행 중인 모든 스크립트 메서드에 인터럽트가 적용 됩니다. 호출자가 스크립트의 연결을 끊기 위해 요청 하지 않는 한, 다음 스크립팅된 이벤트는 SCRIPTSTATE_DISCONNECTED 또는 SCRIPTSTATE_INITIALIZED 플래그를 사용 하 여 [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 메서드를 호출 하 여 스크립트 코드를 다시 실행 합니다. 설정.|  
|SCRIPTTHREADID_BASE|기본 스레드입니다. 즉, 스크립팅 엔진이 인스턴스화된 스레드입니다.|  
|SCRIPTTHREADID_CURRENT|현재 실행 중인 스레드입니다.|  
  
 `pexcepinfo`  
 진행 중단 된 스크립트에 보고 해야 하는 오류 정보를 포함 하는 `EXCEPINFO` 구조의 주소입니다.  
  
 `dwFlags`  
 진행 중단에 연결 된 옵션 플래그입니다. 다음 값 중 하나일 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|지원 되는 경우 현재 스크립트 실행 지점에 스크립팅 엔진의 디버거를 입력 합니다.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|스크립팅 엔진의 언어로 지원 되는 경우 스크립트가 예외를 처리 하도록 합니다. 그렇지 않으면 스크립트 메서드가 중단 되 고 오류 코드가 호출자에 게 반환 됩니다. 즉, 이벤트 원본 또는 매크로 호출자입니다.|  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)