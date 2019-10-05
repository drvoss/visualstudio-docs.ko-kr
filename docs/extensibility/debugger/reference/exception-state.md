---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8f05596b12151b3a40b87c6fc2f15659a38e3431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337682"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
예외 상태를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>필드
`EXCEPTION_NONE`\
예외에서 중지 하지 마십시오.

`EXCEPTION_STOP_FIRST_CHANCE`\
예외의 첫 번째 실행에서 중지 합니다. 예외 이벤트를 설명 하는 경우이 플래그는 예외 이벤트는 첫 번째 예외 이벤트를 나타냅니다.

`EXCEPTION_STOP_SECOND_CHANCE`\
두 번째 예외 발생 시 중지 합니다. 예외 이벤트를 설명 하는 경우 예외 이벤트는 두 번째 예외 이벤트를 나타냅니다.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
첫 번째 사용자 모드 예외를 발생 시 중지 합니다. 예외 이벤트를 설명 하는 경우에 예외 이벤트는 첫째 사용자 예외 이벤트를 나타냅니다.

`EXCEPTION_STOP_USER_UNCAUGHT`\
사용자 모드 예외 잡히지 않는 중지 합니다. 예외 이벤트를 설명 하는 경우에 예외 이벤트를 확인할 수 없는 사용자 모드 예외 이벤트 인지를 나타냅니다.

`EXCEPTION_STOP_ALL`\
예외에서 중지 합니다. 예외 이벤트를 설명 하는 경우 사용 되지 않습니다.

`EXCEPTION_CANNOT_BE_CONTINUED`\
예외 이벤트를 설명 하는 경우에서 예외를 계속할 수 없습니다 나타냅니다.

`EXCEPTION_CODE_SUPPORTED`\
이 예외는이 지 원하는 코드를 나타냅니다. 예외가 표시 사용

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
예외 코드를 16 진수에서 표시 되어야 함을 나타냅니다. 사용 하는 예외를 표시 합니다.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
예외 코드 JustMyCode 지원함을 나타냅니다. 사용 하는 예외를 표시 합니다.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
관리 되는 code 디버거 예외를 처리 해야 나타냅니다. 그렇지 않은 경우는 예외를 처리 하는 기본 디버거에서 집합. 이 전달 되는 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 메서드에서는 사용 되지 합니다 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조입니다.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
사용 되지 않는, 사용 하지 마세요.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
사용 되지 않는, 사용 하지 마세요.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
사용 되지 않는, 사용 하지 마세요.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
사용 되지 않는, 사용 하지 마세요.

## <a name="remarks"></a>설명
로 사용 합니다 `dwState` 의 멤버는 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 예외 및에 대 한 수행할 수 있는 작업의 상태를 나타내는 구조입니다.

이러한 값은 또한 전달 된 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 모든 예외 상태를 설정 하는 방법.

이러한 플래그는 비트 OR 연산자를 사용 하 여 결합할 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
