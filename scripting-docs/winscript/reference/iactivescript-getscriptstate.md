---
title: 'IActiveScript:: GetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575730"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
스크립팅 엔진의 현재 상태를 검색 합니다. 이 메서드는 기본이 아닌 스레드에서 개체를 호스트 하거나 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스를 호스트 하는 경우를 제외 하 고는 기본이 아닌 스레드에서 호출 될 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pss`  
 제한이 [Scriptstate 열거형](../../winscript/reference/scriptstate-enumeration.md) 열거형에 정의 된 값을 수신 하는 변수의 주소입니다. 값은 호출 스레드와 연결 된 스크립팅 엔진의 현재 상태를 나타냅니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 잘못 된 포인터가 지정 된 경우 `E_POINTER`을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)