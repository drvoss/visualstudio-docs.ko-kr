---
title: 'IActiveScriptSite:: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570208"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
스크립트가 실행을 완료 했음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pvarResult`  
 진행 스크립트 결과를 포함 하는 변수의 주소 이거나, 스크립트가 결과를 생성 하지 않은 경우 `NULL`입니다.  
  
 `pexcepinfo`  
 진행 스크립트가 종료 될 때 생성 된 예외 정보를 포함 하는 `EXCEPINFO` 구조체의 주소 이거나, 예외가 생성 되지 않은 경우 `NULL`입니다.  
  
## <a name="return-value"></a>반환 값  
 성공하는 경우 `S_OK`가 반환됩니다.  
  
## <a name="remarks"></a>주의  
 스크립팅 엔진은 SCRIPTSTATE_INITIALIZED 플래그가 설정 된 상태에서 [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 메서드에 대 한 호출이 완료 되기 전에이 메서드를 호출 합니다. 이 메서드는 완료 상태와 결과를 호스트에 반환 하는 데 사용할 수 있습니다. 호스트의 이벤트 싱크를 기반으로 하는 많은 스크립트 언어에는 호스트에서 정의 되는 수명 범위가 있습니다. 이 경우이 메서드를 호출할 수 없습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)