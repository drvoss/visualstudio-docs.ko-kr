---
title: 'IDebugApplication:: HandleBreakPoint | Microsoft Docs'
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
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574967"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
현재 스레드가 중단점에 대 한 알림을 디버거 IDE로 차단 하 고 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `br`  
 진행 중단의 원인입니다.  
  
 `pbra`  
 제한이 디버거가 응용 프로그램을 다시 시작할 때 수행할 동작입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 언어 엔진은 중단점에 도달 하는 스레드의 컨텍스트에서이 메서드를 호출 합니다. 이 메서드는 현재 스레드를 차단 하 고 디버거 IDE에 중단점 알림을 보냅니다. 디버거가 응용 프로그램을 다시 시작할 때 `pbra` 매개 변수는 수행할 작업을 지정 합니다.  
  
> [!NOTE]
> 스레드는 스택 프레임 열거 또는 중단점에서 식 계산 등의 작업을 수행 하는 데 언어 엔진을 호출할 수 있습니다.  
  
 이 메서드를 호출 하면 `IApplicationDebugger::onHandleBreakPoint` 호출 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 사이의 [이유 열거](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 열거형](../../winscript/reference/breakresumeaction-enumeration.md)