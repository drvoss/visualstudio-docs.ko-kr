---
title: 'IActiveScriptSiteDebug:: OnScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572210"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
스마트 호스트에서 런타임 오류를 처리 하는 방법을 결정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pErrorDebug`  
 진행 발생 한 런타임 오류입니다.  
  
 `pfEnterDebugger`  
 제한이 JIT 디버깅을 수행 하기 위해 디버거에 오류를 전달할지 나타내는 플래그입니다.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 제한이 사용자가 디버깅 하지 않고 계속 하기로 결정 한 경우 `IActiveScriptSite::OnScriptError`를 호출할 것인지 나타내는 플래그입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값은 다음 표에 나와 있는 값을 포함 하지만이에 제한 되지 않습니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 스마트 호스트는이 메서드를 사용 하 여 런타임 오류를 처리 하는 방법을 결정할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSiteDebug 인터페이스](../../winscript/reference/iactivescriptsitedebug-interface.md)