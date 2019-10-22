---
title: 'IActiveScript:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575786"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
스크립팅 엔진이 현재 로드 된 모든 스크립트를 중단 하 고, 상태를 잃고, 다른 개체에 대 한 인터페이스 포인터를 해제 하 여 closed 상태를 시작 하도록 합니다. 이미 진행 중인 이벤트 싱크, 즉시 실행 되는 스크립트 텍스트 및 매크로 호출은 상태가 변경 되기 전에 완료 됩니다 ( [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 를 사용 하 여 실행 중인 스크립트 스레드 취소). 순환 참조 문제를 방지 하기 위해 인터페이스를 해제 하기 전에 만들기 호스트에서이 메서드를 호출 해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|값|의미|  
|-----------|-------------|  
|`S_OK`|성공할.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진은 이미 closed 상태에 있습니다.|  
|`OLESCRIPT_S_PENDING`|메서드가 성공적으로 큐에 대기 되었지만 상태가 아직 변경 되지 않았습니다. 상태가 변경 되 면 [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 메서드에서 사이트를 다시 호출 합니다.|  
|`S_FALSE`|메서드가 성공 했지만 스크립트가 이미 닫혔습니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)