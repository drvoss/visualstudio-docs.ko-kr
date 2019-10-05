---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
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
ms.openlocfilehash: a0066894830c111a8e0ad18f7acdc09d6114162e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935611"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
스크립트 스레드의 현재 상태를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `stidThread`  
 [in] 원하는 상태는 스레드의 식별자 또는 다음 특수 스레드 식별자 중 하나:  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|기본 스레드입니다. 즉, 스레드는 스크립팅 엔진 인스턴스화 되었습니다.|  
|SCRIPTTHREADID_CURRENT|현재 실행 중인 스레드입니다.|  
  
 `pstsState`  
 [out] 지정 된 스레드의 상태를 받는 변수의 주소입니다. 상태에 정의 된 명명 된 상수 값 중 하나에 의해 표시 됩니다는 [SCRIPTTHREADSTATE 열거형](../../winscript/reference/scriptthreadstate-enumeration.md) 열거형입니다. 이 매개 변수는 현재 스레드를 식별 하지 않으면 상태는 언제 든 지 변경 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화).|  
  
## <a name="remarks"></a>설명  
 호스트 개체 또는 기본이 아닌 설명선 발생 하지 않고 기본이 아닌 스레드에서이 메서드를 호출할 수는 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)