---
title: 'IActiveScriptSite:: OnStateChange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba8441d36f193f287dfec7406d5f136280c5a42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570157"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
스크립팅 엔진의 상태가 변경 되었음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ssScriptState`  
 진행 새 스크립트 상태를 나타내는 값입니다. 상태에 대 한 설명은 [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 메서드를 참조 하세요.  
  
## <a name="return-value"></a>반환 값  
 성공하는 경우 `S_OK`가 반환됩니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)