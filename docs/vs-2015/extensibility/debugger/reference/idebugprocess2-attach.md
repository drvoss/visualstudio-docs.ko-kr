---
title: IDebugProcess2::Attach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4664f164675c445510d8976f33577684dbd1d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188104"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

세션 디버그 관리자 (SDM) 프로세스에 연결 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버그 이벤트 알림에 사용 되는 개체입니다.  
  
 `rgguidSpecificEngines`  
 [in] 배열 프로세스에서 실행 되는 프로그램을 디버그 하는 데 사용할 디버그 엔진의 Guid입니다. 이 매개 변수는 null 값일 수 있습니다. 세부 정보에 대 한 설명을 참조 하세요.  
  
 `celtSpecificEngines`  
 [in] 수가 디버그 엔진에 `rgguidSpecificEngines` 배열과의 크기는 `rghrEngineAttach` 배열입니다.  
  
 `rghrEngineAttach`  
 [out에서] 디버그 엔진에서 반환 된 HRESULT 코드의 배열입니다. 에 지정 된이 배열의 크기는 `celtSpecificEngines` 매개 변수입니다. 각 코드는 일반적으로 `S_OK` 또는 `S_ATTACH_DEFERRED`합니다. 후자는 DE 없는 프로그램에 현재 연결 되어 있는지 나타냅니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서 가능한 다른 값을 보여 줍니다.  
  
|값|Description|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|지정된 된 프로세스 디버거가 이미 연결 되어 있습니다.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|연결 절차 동안 보안 위반이 발생 했습니다.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|데스크톱 프로세스는 디버거에 연결할 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 에 지정 된 디버그 엔진 (DE)에서 디버깅할 수 있는 해당 프로세스에서 실행 중인 모든 프로그램 SDM 연결 프로세스에 연결 하는 `rgguidSpecificEngines` 배열입니다. 설정 합니다 `rgguidSpecificEngines` 매개 변수를 null 값 또는 포함 `GUID_NULL` 프로세스에서 모든 프로그램에 연결 된 배열의 합니다.  
  
 프로세스에서 발생 하는 모든 디버그 이벤트가 전송 되는 지정 된 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다. 이 `IDebugEventCallback2` SDM이이 메서드를 호출 하는 경우 개체는 제공 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
