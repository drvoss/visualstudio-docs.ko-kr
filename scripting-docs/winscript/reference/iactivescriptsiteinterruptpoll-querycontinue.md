---
title: 'IActiveScriptSiteInterruptPoll:: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572228"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
호스트가 스크립트를 종료 하도록 지정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|호출에 성공 하 고 호스트에서 스크립트를 계속 실행할 수 있습니다.|  
|`S_FALSE`|호출이 성공 하 고 호스트가 스크립트가 종료 되도록 요청 합니다.|  
  
## <a name="remarks"></a>주의  
 `QueryContinue` 메서드의 반환 값을 `S_OK`하지 않으면 호스팅된 스크립트가 종료 됩니다. `S_FALSE`의 반환 값은 호스트가 스크립트가 종료 되도록 명시적으로 요청 함을 나타냅니다.  
  
 다중 스레드 호스트는 `IActiveScript::InterruptScriptThread` 메서드를 사용 하 여 스크립트를 종료할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSiteInterruptPoll 인터페이스](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)