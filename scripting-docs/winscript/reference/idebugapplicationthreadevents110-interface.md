---
title: IDebugApplicationThreadEvents110 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984397"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 인터페이스
더 많은 스레드 이벤트를 추가 합니다. 이러한 이벤트는 로컬 전용입니다. 즉, PDM 응용 프로그램 스레드 개체 ( [Idebugapplicationthread 인터페이스](../../winscript/reference/idebugapplicationthread-interface.md)를 구현 하는 개체)에서 [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) advise 및 unadvise 메서드를 사용 하 여 디버깅 중인 프로세스 에서만이를 구독할 수 있습니다. 들어오는 스레드에서 발생 합니다.  
  
> [!IMPORTANT]
> 이 인터페이스는 PDM v11.0 이상에 의해 구현됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="methods"></a>메서드  
 `IDebugActivationThreadEvents110` 인터페이스는 다음 메서드를 노출합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|PDM의 스레드 전환을 사용 하 여 스레드를 호출 하는 작업이 시작 되었습니다.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|스레드가 중단점에서 다시 시작 되 고 다시 한 번 활성화 됩니다.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|스레드가 중단점을 일시 중단 하 고 스레드가 완전히 일시 중단 되어야 하는 호출을 처리할 수 있습니다.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|PDM의 스레드 전환을 사용 하는 스레드에 대 한 호출이 완료 되었습니다.|