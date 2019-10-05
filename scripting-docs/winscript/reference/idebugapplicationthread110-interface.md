---
title: IDebugApplicationThread110 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 44df7168c241c9a750354e1a603d6c5ba96dabd2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440544"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 인터페이스
에 대 한 더 많은 기능을 제공 합니다 [IDebugApplicationThread 인터페이스](../../winscript/reference/idebugapplicationthread-interface.md) 인터페이스입니다.  
  
> [!IMPORTANT]
> 이 인터페이스는 PDM v11.0 이상에 의해 구현됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="methods"></a>메서드  
 `IDebugApplicationThread110` 인터페이스는 다음 메서드를 노출합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|주 스레드에 대 한 비동기 호출을 만듭니다.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|얼마나 많은 스레드가 요청 메커니즘을 전환 하는 PDM의 스레드에서 현재 처리 중인 개수입니다. 0 또는 1 하지만 하나의 스레드 호출 처리를 시작 하지만 스레드에서 동기 호출을 트리거합니다 또는 그렇지 않은 경우 (예를 들어, 디버거를 발급 하는 IDebugApplicationEvents 이벤트가 트리거될에서 스레드를 일시 중단 하는 경우 더 높은 것으로 가능한의 일반적으로 스레드)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) 이 스레드에서 호출 되었고, 아직 완료 되지 않았습니다.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|이 스레드 (예: SynchronousCallInThread) 메커니즘을 전환 하는 PDM의 스레드를 사용 하 여 호출을 처리할 수 있는 상태입니다.|