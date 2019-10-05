---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59489af368c2e95a2d3cc93edbd6f7ab02a1c156
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195646"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

실행에 대 한 감시 (또는 실행에 대 한 감시 중지) 지정한 스레드에서 발생 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pOriginatingProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 단계별 되 고 프로그램을 나타내는 개체입니다.  
  
 `dwTid`  
 [in] 조사할 스레드의 식별자를 지정 합니다.  
  
 `fWatch`  
 [in] 0이 아닌 (`TRUE`) 수단으로 식별 되는 스레드에서 실행에 대 한 감시 시작 `dwTid`이 고, 그렇지 않으면 0 (`FALSE`) 의미에서 실행에 대 한 감시 중지 `dwTid`합니다.  
  
 `dwFrame`  
 [in] 단계 형식을 제어 하는 프레임 인덱스를 지정 합니다. 이 경우 값은 영 (0), 단계 형식이 "step into" 및로 식별 되는 스레드 때마다 프로그램을 중지 해야 `dwTid` 실행 합니다. 때 `dwFrame` 0이 아닌, 단계 형식이 "step over" 및 프로그램으로 스레드를 식별 하는 경우에 중지 해야 `dwTid` 인덱스는 같음 또는 보다는 스택의 상위 프레임에서 실행 되 고 `dwFrame`입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 세션 디버그 관리자 (SDM)로 식별 되는 프로그램 단계 하는 경우는 `pOriginatingProgram` 매개 변수를에 알립니다 다른 모든 연결 된 프로그램은이 메서드를 호출 하 여 합니다.  
  
 이 메서드는 동일한 스레드에서 단계별 실행에 적용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
