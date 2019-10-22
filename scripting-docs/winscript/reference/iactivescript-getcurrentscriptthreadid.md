---
title: 'IActiveScript:: GetCurrentScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575776"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
현재 실행 중인 스레드에 대 한 스크립팅 엔진 정의 식별자를 검색 합니다. 식별자는 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 메서드와 같은 스레드 실행 제어 메서드를 이후에 호출 하는 데 사용할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstidThread`  
 제한이 현재 스레드와 연결 된 스크립트 스레드 식별자를 받는 변수의 주소입니다. 이 식별자의 해석은 스크립팅 엔진으로 유지 되지만 Windows 스레드 식별자의 복사본 일 수도 있습니다. Win32 스레드가 종료 되 면이 식별자는 할당 되지 않으며 이후에 다른 스레드에 할당 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 잘못 된 포인터가 지정 된 경우 `E_POINTER`을 반환 합니다.  
  
## <a name="remarks"></a>주의  
 이 메서드는 기본이 아닌 스레드에서 개체를 호스트 하거나 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스를 호스트 하는 경우를 제외 하 고는 기본이 아닌 스레드에서 호출 될 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)