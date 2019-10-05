---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs
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
ms.openlocfilehash: 50e8c7baa42d6f2f36dc71b768797dfe2a464bf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992423"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
스마트 호스트를 런타임 오류를 처리 하는 방법을 결정할 수 있습니다.  
  
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
 [in] 발생 한 런타임 오류  
  
 `pfEnterDebugger`  
 [out] 오류 JIT 디버깅을 수행 하도록 디버거를 전달할지 여부를 나타내는 플래그입니다.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] 호출할지 여부를 나타내는 플래그 `IActiveScriptSite::OnScriptError` 디버깅 하지 않고 계속 하려면 사용자가 결정 하는 경우.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값은 포함 되지만 다음 테이블의 값으로 제한 되지 않습니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 스마트 호스트 런타임 오류를 처리 하는 방법을 결정 하려면이 메서드를 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSiteDebug 인터페이스](../../winscript/reference/iactivescriptsitedebug-interface.md)