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
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575674"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE 열거형
스크립팅 엔진의 상태를 지정 합니다. 이 열거형은 [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) 및 [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 메서드에서 사용 됩니다.  
  
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
|SCRIPTSTATE_UNINITIALIZED|스크립트가 만들어졌지만 `IPersist*` 인터페이스 및 [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 를 사용 하 여 아직 초기화 되지 않았습니다.|  
|SCRIPTSTATE_INITIALIZED|스크립트가 초기화 되었지만 실행 되 고 있지 않습니다. 다른 개체에 연결 하거나 이벤트를 싱크 하거나 코드를 실행 하 고 있지 않습니다. [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) 메서드를 호출 하 여 실행을 위해 코드를 쿼리할 수 있습니다.|  
|SCRIPTSTATE_STARTED|스크립트는 코드를 실행할 수 있지만 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 메서드에 의해 추가 된 개체의 이벤트는 아직 싱크 되지 않습니다.|  
|SCRIPTSTATE_CONNECTED|스크립트를 로드 하 고 싱크 이벤트에 연결 합니다.|  
|SCRIPTSTATE_DISCONNECTED|스크립트가 로드 되 고 런타임 실행 상태가 있지만 싱크 이벤트와 일시적으로 연결이 끊겼습니다.|  
|SCRIPTSTATE_CLOSED|스크립트가 닫혔습니다. 스크립트 엔진이 더 이상 작동하지 않고 대부분의 메서드에 대해 오류를 반환합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 상수, 열거형 및 오류 코드](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)