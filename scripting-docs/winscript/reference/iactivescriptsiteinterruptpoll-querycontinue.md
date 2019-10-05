---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
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
ms.openlocfilehash: 63ce45c0973d65d240136d7b42aef0c078b00c9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992289"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
스크립트를 종료할지를 지정 하는 호스트 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수 없이 합니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|호출에 성공 하 고 호스트 실행을 계속 하려면 스크립트를 허용 합니다.|  
|`S_FALSE`|호출이 성공 했음 및 스크립트가 종료 되는 호스트 요청 합니다.|  
  
## <a name="remarks"></a>설명  
 호스트 된 스크립트는 경우가 아니면 종료 해야의 반환 값을 `QueryContinue` 메서드는 `S_OK`합니다. 반환 값 `S_FALSE` 호스트 명시적으로 요청 하도록 스크립트의 종료를 나타냅니다.  
  
 다중 스레드 호스트를 사용할 수는 `IActiveScript::InterruptScriptThread` 스크립트를 종료 하는 방법입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSiteInterruptPoll 인터페이스](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)