---
title: 'IApplicationDebugger:: onHandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577835"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
중단점 이벤트를 처리 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `prpt`  
 진행 중단점이 발생 한 스레드입니다.  
  
 `br`  
 진행 중단점에 대 한 이유입니다.  
  
 `pError`  
 진행 `br` 값이 BREAKREASON_ERROR 될 때 제공 되는 런타임 오류 정보입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 중단점에 도달 하 고 `IDebugApplication::HandleBreakPoint`를 호출할 때 호출 됩니다.  
  
 디버거 IDE가 `IRemoteDebugApplication::ResumeFromBreakPoint`를 호출할 때까지 응용 프로그램은 일시 중단 된 상태로 유지 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Iapplicationdebugger 인터페이스](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON 열거형](../../winscript/reference/breakreason-enumeration.md)