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
ms.openlocfilehash: b2cdde46484f95aa57404ebe6b6cb4c86ef458c9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440502"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 인터페이스
더 많은 스레드 이벤트를 추가합니다. 이러한 이벤트는 로컬에 합니다. 즉, 구독할 수 있습니다 하 되 고 있는 프로세스에만 디버깅을 사용 하 여 합니다 [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) 싱 및 PDM 응용 프로그램 스레드 개체에서 메서드를 unadvise (구현 하는 개체가 [IDebugApplicationThread 인터페이스](../../winscript/reference/idebugapplicationthread-interface.md)). 생성 되는 스레드에서 발생 합니다.  
  
> [!IMPORTANT]
> 이 인터페이스는 PDM v11.0 이상에 의해 구현됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="methods"></a>메서드  
 `IDebugActivationThreadEvents110` 인터페이스는 다음 메서드를 노출합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|호출 PDM의 스레드를 사용 하 여 스레드를 시작 했습니다 전환 합니다.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|스레드가 중단점에서 다시 시작 및 다시 활성화 됩니다.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|중단점에 대 한 일시 중단 되 고 스레드와 스레드를 완벽 하 게 일시 중단 해야 하는 호출을 처리할 수 있습니다.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|호출 PDM의 스레드를 사용 하 여 스레드를 전환 완료 합니다.|