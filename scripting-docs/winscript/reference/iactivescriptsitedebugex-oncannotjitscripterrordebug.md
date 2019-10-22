---
title: 'IActiveScriptSiteDebugEx:: OnCanNotJITScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572187"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
프로세스 디버그 관리자가 Just-in-time 스크립트 디버거를 찾지 못하는 경우 호스트에 스크립트 런타임 오류를 알립니다.  
  
 호스트에서 디버거를 구현 하려면 [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)를 처리 해야 합니다. 사용자 동작에 따라 호스트는 디버거를 연결 하 고를 반환 하거나 OnScriptErrorDebug `pfEnterDebugger` 매개 변수에서 디버거의 시작을 반환할 수 있습니다. 또한 프로세스 디버그 관리자가 해석할 수 있는 외부 디버거가 없더라도이 인터페이스를 구현 하 여 런타임 오류에 대 한 알림을 가져와야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pErrorDebug`  
 진행 발생 한 런타임 오류입니다.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 제한이 사용자가 디버깅 하지 않고 계속 하도록 결정 한 경우 [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) 를 호출 하는지 여부입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 또한 알림을 받으려면이 인터페이스를 구현 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSiteDebugEx 인터페이스](../../winscript/reference/iactivescriptsitedebugex-interface.md)