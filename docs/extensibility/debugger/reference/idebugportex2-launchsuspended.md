---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94810761e546b0cae9eca32fc76bc0bfd396c7e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311124"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
실행 파일을 시작합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>매개 변수
`pszExe`\
[in] 시작할 실행 파일의 이름입니다. 전체 경로 또는 상대에 지정 된 작업 디렉터리에이 수는 `pszDir` 매개 변수입니다.

`pszArgs`\
[in] 실행 파일에 전달할 인수입니다. 인수가 없는 경우 null 값이 될 수 있습니다.

`pszDir`\
[in] 실행 파일에서 사용 하는 작업 디렉터리의 이름입니다. 작업 디렉터리가 필요한 경우 null 값이 될 수 있습니다.

`bstrEnv`\
[in] 환경 블록 뒤에 추가 NULL 종결자를 null로 끝나는 문자열입니다.

`hStdInput`\
[in] 대체 입력 스트림으로 처리 합니다. 리디렉션 필요 하지 않은 경우에 0 일 수 있습니다.

`hStdOutput`\
[in] 대체 출력 스트림으로 처리 합니다. 리디렉션 필요 하지 않은 경우에 0 일 수 있습니다.

`hStdError`\
[in] 대체 오류 출력 스트림으로 처리 합니다. 리디렉션 필요 하지 않은 경우에 0 일 수 있습니다.

`ppPortProcess`\
[out] 반환 된 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 시작된 프로세스를 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드를 일시 중단 하도록 하는 프로세스 및 코드를 실행 하지 시작 됩니다. 합니다 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) 메서드를 호출 하는 프로세스를 다시 시작 합니다.

 또한 디버그 엔진에서 프로그램을 시작할 수 있습니다. 세부 정보를 참조 하세요 [프로그램을 실행할](../../../extensibility/debugger/launching-a-program.md)합니다.

## <a name="see-also"></a>참고자료
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [프로그램 시작](../../../extensibility/debugger/launching-a-program.md)