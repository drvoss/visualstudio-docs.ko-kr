---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc50f9884d40083d9696869c0e1b34284e4a794
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352055"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
현재 예외를 차단 하려는 경우 현재 스택 프레임에는 디버거에서 호출 됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>매개 변수
`dwFlags`\
[in] 다양 한 작업을 지정합니다. 현재만 합니다 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) 값 `IEA_INTERCEPT` 은 지원 되며 지정 해야 합니다.

`pqwCookie`\
[out] 특정 예외를 식별 하는 고유 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

 가장 일반적인 오류는 다음과 같습니다.

|Error|설명|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|현재 예외를 가로챌 수 없습니다.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|현재 실행 프레임 처리기에 대 한 아직 검색 된 되지 않았습니다.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|이 메서드는이 프레임에 대 한 지원 되지 않습니다.|

## <a name="remarks"></a>설명
 예외가 throw 되 면 디버거가 예외 프로세스를 처리 하는 동안 주요 지점에서 런타임에 컨트롤을 얻게 됩니다. 이러한 키 분 동안 디버거 요청할 수 있습니다 현재 스택 프레임 프레임 예외를 차단 하려는 경우. 이러한 방식으로 가로챈된 예외는 기본적으로 즉석에서 예외 처리기는 스택 프레임의 스택 프레임 (예: 프로그램 코드에서 try/catch 블록) 예외 처리기가 없는 하는 경우에 합니다.

 디버거를 알고 있어야 하는 경우 예외를 가로챌 수 해야 하고자 하는 경우 현재 스택 프레임 개체에서이 메서드를 호출 합니다. 이 메서드는 예외의 모든 세부 정보를 처리 하는 일을 담당 합니다. 경우는 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) 인터페이스가 구현 되지 않는 또는 `InterceptStackException` 디버거가 예외를 정상적으로 처리를 계속 한 다음 메서드는 모든 오류를 반환 합니다.

> [!NOTE]
> 예외 가로챌 수 있습니다 관리 되는 코드에만 즉, 런타임에.net 디버깅 중인 프로그램 실행 중일 때. 타사 언어 구현자 구현할 수는 물론, `InterceptStackException` 선택 하는 경우 자신의 디버그 엔진에서입니다.

 가로채기를 완료 한 후는 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) 신호입니다.

## <a name="see-also"></a>참고자료
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)