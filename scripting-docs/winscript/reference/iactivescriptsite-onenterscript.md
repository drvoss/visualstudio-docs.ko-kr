---
title: 'IActiveScriptSite:: OnEnterScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570358"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
스크립팅 엔진이 스크립트 코드 실행을 시작 했음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>반환 값  
 성공하는 경우 `S_OK`가 반환됩니다.  
  
## <a name="remarks"></a>주의  
 스크립팅 엔진은 모든 항목에 대해이 메서드를 호출 하거나 스크립팅 엔진으로 재진입이 야 합니다. 예를 들어 스크립트가 스크립팅 엔진에서 처리 하는 이벤트를 발생 시키는 개체를 호출 하는 경우 스크립팅 엔진은 이벤트를 실행 하기 전에 `IActiveScriptSite::OnEnterScript`를 호출 하 고 이벤트를 실행 한 후에 [IActiveScriptSite:: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) 메서드를 호출 해야 합니다. 이벤트를 발생 시킨 개체로 반환 하기 전에 이 메서드에 대 한 호출은 중첩 될 수 있습니다. 이 메서드에 대 한 모든 호출에는 `IActiveScriptSite::OnLeaveScript`에 대 한 해당 호출이 필요 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)