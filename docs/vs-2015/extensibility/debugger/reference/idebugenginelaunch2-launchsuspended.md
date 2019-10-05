---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08f59f9f099f4cec52760c8a8364feb8f5481ffa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195750"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 디버그 엔진 (DE)를 사용 하 여 프로세스를 시작합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```csharp  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszMachine`  
 [in] 프로세스를 시작 하는 컴퓨터의 이름입니다. Null 값을 사용 하 여 로컬 컴퓨터를 지정 합니다.  
  
 `pPort`  
 [in] 합니다 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 에서 프로그램이 실행 되는 포트를 나타내는 인터페이스입니다.  
  
 `pszExe`  
 [in] 시작할 실행 파일의 이름입니다.  
  
 `pszArgs`  
 [in] 실행 파일에 전달할 인수입니다. 인수가 없는 경우 null 값이 될 수 있습니다.  
  
 `pszDir`  
 [in] 실행 파일에서 사용 하는 작업 디렉터리의 이름입니다. 작업 디렉터리가 필요한 경우 null 값이 될 수 있습니다.  
  
 `bstrEnv`  
 [in] 환경 블록 뒤에 추가 NULL 종결자를 NULL로 끝나는 문자열입니다.  
  
 `pszOptions`  
 [in] 실행 파일에 대 한 옵션입니다.  
  
 `dwLaunchFlags`  
 [in] 지정 된 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) 세션에 대 한 합니다.  
  
 `hStdInput`  
 [in] 대체 입력 스트림으로 처리 합니다. 리디렉션 필요 하지 않은 경우에 0 일 수 있습니다.  
  
 `hStdOutput`  
 [in] 대체 출력 스트림으로 처리 합니다. 리디렉션 필요 하지 않은 경우에 0 일 수 있습니다.  
  
 `hStdError`  
 [in] 대체 오류 출력 스트림으로 처리 합니다. 리디렉션 필요 하지 않은 경우에 0 일 수 있습니다.  
  
 `pCallback`  
 [in] 합니다 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버거 이벤트를 받는 개체입니다.  
  
 `ppDebugProcess`  
 [out] 결과 반환 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 시작된 프로세스를 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 일반적으로 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 사용 하 여 프로그램을 시작 합니다 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 메서드 다음 일시 중단 된 프로그램에 디버거를 연결 합니다. 그러나이 경우 (예를 들어 디버그 엔진에 속한 경우 인터프리터의 디버그 중인 프로그램은 해석 된 언어), 프로그램을 실행 하는 디버그 엔진을 해야 하는 경우도 있습니다. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 사용 하 여 `IDebugEngineLaunch2::LaunchSuspended` 메서드 .  
  
 합니다 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) 메서드가 호출 되어 일시 중단된 된 상태에서 프로세스를 성공적으로 실행 된 후 프로세스를 시작 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
