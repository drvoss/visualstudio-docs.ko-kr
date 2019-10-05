---
title: IActiveScriptSite::OnScriptTerminate | Microsoft Docs
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
ms.openlocfilehash: 664f974b26a2cae0d1e16d37dc3bc66e95993d6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992648"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
스크립트 실행을 완료 했음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pvarResult`  
 [in] 스크립트 결과 포함 하는 변수의 주소 또는 `NULL` 스크립트 없는 결과 생성 하는 경우.  
  
 `pexcepinfo`  
 [in] 주소는 `EXCEPINFO` 스크립트가 종료 될 때 생성 되는 예외 정보를 포함 하는 구조 또는 `NULL` 예외가 생성 된 경우.  
  
## <a name="return-value"></a>반환 값  
 성공하는 경우 `S_OK`가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 스크립팅 엔진을 호출 하기 전에이 메서드를 호출 합니다 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) SCRIPTSTATE_INITIALIZED 플래그 집합으로 메서드가 완료 되기 합니다. 호스트에 완료 상태 및 결과 반환할이 메서드를 사용할 수 있습니다. 호스트에서 이벤트를 싱크하기에 기반 하는 여러 스크립트 언어를 호스트에 의해 정의 된 수명 범위는 note 합니다. 이 경우이 메서드를 호출 하지 않을 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)