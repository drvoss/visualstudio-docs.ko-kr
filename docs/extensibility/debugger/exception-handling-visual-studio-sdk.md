---
title: 예외 처리 (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fdb309c01979985d1c00eedab9c496d0af44e07
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315273"
---
# <a name="exception-handling-visual-studio-sdk"></a>예외 처리 (Visual Studio SDK)
다음 예외가 발생할 때 발생 하는 프로세스를 설명 합니다.

## <a name="exception-handling-process"></a>예외 처리 프로세스

1. 먼저 예외가 있지만 디버그 엔진 (DE) 전송 전에 디버깅 중인 프로그램에 예외 처리기에서 처리 되는 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 중지 이벤트로 세션 디버그 관리자 (SDM). `IDebugExceptionEvent2` (디버그 패키지에 예외 대화 상자에서 지정) 예외에 대 한 설정을 지정 된 사용자가 첫째 예외 알림을 중지 하는 경우에 전송 됩니다.

2. SDM 호출 [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) 예외의 속성을 가져옵니다.

3. 디버그 패키지 호출 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 사용자에 게 제공할 옵션을 확인 하려면.

4. 디버그 패키지가 첫째 예외 대화 상자를 열어 예외를 처리 하는 방법을 사용자에 게 요청 합니다.

5. SDM를 호출 하는 경우 사용자가 계속 하기로 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)합니다.

    - 메서드가 S_OK를 반환 하는 경우 호출 [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)합니다.

         또는

         메서드를 프로그램 S_FALSE를 반환 하는 경우 디버깅 중인 예외를 처리 하는 두 번째 기회 제공 됩니다.

6. 디버그 중인 프로그램에 두 번째 예외에 대 한 처리기는 DE 보냅니다는 `IDebugExceptionEvent2` 으로 SDM 하 **EVENT_SYNC_STOP**합니다.

7. 디버그 패키지가 첫째 예외 대화 상자를 열어 예외를 처리 하는 방법을 사용자에 게 요청 합니다.

8. 디버그 패키지 호출 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 사용자에 게 제공할 옵션을 확인 하려면.

9. 디버그 패키지가 두 번째 예외 대화 상자를 열어 예외를 처리 하는 방법을 사용자에 게 요청 합니다.

10. 메서드가 S_OK를 반환 하는 경우 호출 `IDebugExceptionEvent2::PassToDebuggee`합니다.

## <a name="see-also"></a>참고자료
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)