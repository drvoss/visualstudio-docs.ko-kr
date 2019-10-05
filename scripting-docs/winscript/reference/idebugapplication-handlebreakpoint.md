---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e3444e6eedde9576216552e41abb0e97aafa2d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412387"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
현재 스레드를 차단 하 고 디버거 IDE 중단점에 대 한 알림을 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `br`  
 [in] 중단 된 이유입니다.  
  
 `pbra`  
 [out] 디버거에서 응용 프로그램을 다시 시작 될 때 수행할 동작입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 언어 엔진의 중단점에 도달 하는 스레드 컨텍스트에서이 메서드를 호출 합니다. 이 메서드는 현재 스레드를 차단 하 고 디버거 IDE에 중단점 알림을 보냅니다. 디버거에서 응용 프로그램을 다시 시작 될 때를 `pbra` 매개 변수는 수행할 작업을 지정 합니다.  
  
> [!NOTE]
> 언어 엔진 프레임 또는 중단점 중 식을 평가할 스택 열거와 같은 작업을 수행 하는 스레드에서 호출할 수 있습니다.  
  
 이 메서드를 사용 하면 `IApplicationDebugger::onHandleBreakPoint` 호출할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 열거형](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 열거형](../../winscript/reference/breakresumeaction-enumeration.md)