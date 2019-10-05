---
title: SCRIPTSTATE 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe6a05c5e73d26a8daa9e46c317422d85d1c40be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840163"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE 열거형
스크립팅 엔진의 상태를 지정 합니다. 이 열거형은에서 사용 합니다 [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 를 [iactivescript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) , 및 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 메서드.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>열거형 값  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|스크립트에 방금 생성 되었지만 초기화 되지 않은 아직 사용 하 여는 `IPersist*` 인터페이스 및 [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 합니다.|  
|SCRIPTSTATE_INITIALIZED|스크립트가 초기화 된 하지만 (다른 개체에 연결 하거나 이벤트를 싱크하기)를 실행 또는 코드를 실행 됩니다. 호출 하 여 실행 한 코드를 쿼리할 수는 [iactivescriptparse:: Parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) 메서드.|  
|SCRIPTSTATE_STARTED|스크립트 코드를 실행할 수 있습니다 하 여 추가 된 개체의 이벤트를 아직 싱크 하지는 않지만 합니다 [iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) 메서드.|  
|SCRIPTSTATE_CONNECTED|스크립트는 로드 되 고 이벤트를 싱크하기 위해 연결 합니다.|  
|SCRIPTSTATE_DISCONNECTED|스크립트는 런타임 실행 상태가 하며 이벤트를 싱크하기에서 임시로 연결이 끊겨 로드 됩니다.|  
|SCRIPTSTATE_CLOSED|스크립트가 종료 되었습니다. 스크립트 엔진이 더 이상 작동하지 않고 대부분의 메서드에 대해 오류를 반환합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 상수, 열거형 및 오류 코드](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)