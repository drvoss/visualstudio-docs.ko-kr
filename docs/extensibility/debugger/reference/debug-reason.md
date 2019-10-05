---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0502ab10398d37bcafee5316ba7e7566dbab4e01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346159"
---
# <a name="debugreason"></a>DEBUG_REASON
디버깅에 대 한 프로세스를 실행 하는 이유를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>필드
`DEBUG_REASON_ERROR`\
관련 되지 않은 오류가 발생 했습니다 (이 기본 조건으로 맞춤 이유는 다른 경우).

`DEBUG_REASON_USER_LAUNCHED`\
프로세스는 사용자의 요청 시 시작 되었습니다.

`DEBUG_REASON_USER_ATTACHED`\
이미 실행 중인 프로세스에 사용자가 연결 되었습니다.

`DEBUG_REASON_AUTO_ATTACHED`\
프로세스를 시작 될 때 자동으로 연결 됩니다.

`DEBUG_REASON_CAUSALITY`\
로 인해 프로세스가 시작 된를 *Just In Time* (JIT) 디버깅 이벤트입니다.

## <a name="remarks"></a>설명
반환 된 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
