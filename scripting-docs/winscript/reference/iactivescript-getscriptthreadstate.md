---
title: 'IActiveScript:: GetScriptThreadState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578003"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
스크립트 스레드의 현재 상태를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `stidThread`  
 진행 상태를 원하는 스레드의 식별자 이거나 다음 특수 스레드 식별자 중 하나입니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|기본 스레드입니다. 즉, 스크립팅 엔진이 인스턴스화된 스레드입니다.|  
|SCRIPTTHREADID_CURRENT|현재 실행 중인 스레드입니다.|  
  
 `pstsState`  
 제한이 표시 된 스레드의 상태를 받는 변수의 주소입니다. 상태는 [SCRIPTTHREADSTATE 열거형](../../winscript/reference/scriptthreadstate-enumeration.md) 열거형에 정의 된 명명 된 상수 값 중 하나로 표시 됩니다. 이 매개 변수가 현재 스레드를 식별 하지 않는 경우 상태는 언제 든 지 변경 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 기본이 아닌 스레드에서 개체를 호스트 하거나 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스를 호스트 하는 경우를 제외 하 고는 기본이 아닌 스레드에서 호출 될 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)