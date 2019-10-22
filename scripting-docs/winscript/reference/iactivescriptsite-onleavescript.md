---
title: 'IActiveScriptSite:: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570322"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
스크립트 코드를 실행 하 여 스크립팅 엔진이 반환 했음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>반환 값  
 성공하는 경우 `S_OK`가 반환됩니다.  
  
## <a name="remarks"></a>주의  
 스크립팅 엔진은 스크립팅 엔진을 시작한 호출 응용 프로그램에 컨트롤을 반환 하기 전에이 메서드를 호출 해야 합니다. 예를 들어 스크립트가 스크립팅 엔진에서 처리 하는 이벤트를 발생 시키는 개체를 호출 하는 경우 스크립팅 엔진은 이벤트를 실행 하기 전에 [IActiveScriptSite:: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) 메서드를 호출 하 고 이벤트를 실행 한 후 `IActiveScriptSite::OnLeaveScript`를 호출 해야 합니다. 이벤트를 발생 시킨 개체로 반환 합니다. 이 메서드에 대 한 호출은 중첩 될 수 있습니다. @No__t_0에 대 한 모든 호출에는이 메서드에 대 한 해당 호출이 필요 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)