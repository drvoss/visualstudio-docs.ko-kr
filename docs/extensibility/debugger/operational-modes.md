---
title: 운영 모드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81011a6962bc874188aa04b6b1bb8ea538f3db49
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351529"
---
# <a name="operational-modes"></a>운영 모드
세 가지 모드는 IDE 작동할 수 있습니다, 다음과 같습니다.

- [디자인 모드](#vsconoperationalmodesanchor1)

- [실행된 모드](#vsconoperationalmodesanchor2)

- [중단 모드](#vsconoperationalmodesanchor3)

  전환 메커니즘을 사용 하 여 알고 있어야 하는 구현을 결정 하는 경우 사용자 지정 디버그 엔진 (DE) 이러한 모드를 전환 하는 방법 DE 있고 이러한 모드에 직접 구현 하지 않을 수 있습니다. 이러한 모드는 실제로 디버그 패키지 모드 전환 하는 사용자 작업 또는 이벤트는 DE에서 기반으로 합니다. 예를 들어 중단 모드로 실행된 모드에서 전환은 DE의 중지 이벤트에 의해 간섭 됩니다. 중단 모드 또는 단계 모드 실행에서 전환 단계 또는 Execute 등의 작업을 수행 하는 사용자가 발생 시킨 됩니다. DE 전환에 대 한 자세한 내용은 참조 하세요. [실행 제어](../../extensibility/debugger/control-of-execution.md)입니다.

## <a name="vsconoperationalmodesanchor1"></a> 디자인 모드
 디자인 모드에는 디버깅 응용 프로그램에서 기능을 설정할 수 있습니다이 기간 동안 Visual Studio 디버깅 nonrunning 상태입니다.

 몇 가지 디버깅 기능 디자인 모드에 있는 동안 사용 됩니다. 개발자는 중단점을 설정 또는 조사식 식을 만들 수 있습니다. DE 로드 되거나 IDE가 디자인 모드에서 호출 되지 않습니다. DE와의 상호 작용 하는 동안 실행 및 중단 모드에만 수행이 됩니다.

## <a name="vsconoperationalmodesanchor2"></a> 실행된 모드
 실행된 모드는 IDE의 디버깅 세션에서 프로그램 실행 될 때 발생 합니다. 중단점 적중 될 때까지 또는 예외가 발생 될 때까지 응용 프로그램이 종료 될 때까지 실행 합니다. 디자인 모드로 DE 전환 종료 되도록 응용 프로그램입니다. 중단점이 적중 되는 또는 예외가 throw 되는 DE 중단 모드로 전환 됩니다.

## <a name="vsconoperationalmodesanchor3"></a> 중단 모드
 중단 모드에는 디버깅 프로그램 실행을 일시 중단 되 면 발생 합니다. 중단 모드에서는 개발자 중단 시 응용 프로그램의 스냅숏을 제공 하 고 개발자가 응용 프로그램의 상태를 분석 하 고 응용 프로그램이 실행 되는 방식을 변경할 수 있습니다. 개발자 수 및 코드 편집, 검사 또는 데이터 수정, 응용 프로그램을 다시 시작, 실행 종료 보거나 동일한 지점에서 실행을 계속 합니다.

 중단 모드는 DE 동기 중지 이벤트를 보내면 입력 됩니다. 동기 중지 이벤트를 라고도 함 중지 이벤트를 알리는 세션 디버그 관리자 (SDM) 및 IDE는 디버깅 중인 응용 프로그램 코드 실행을 중지 했습니다. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 하 고 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 인터페이스는 stopping 이벤트의 예입니다.

 중지 이벤트를 실행 하거나 모드 단계 중단 모드에서 디버거를 전환 하는 다음 방법 중 하나를 호출 하 여 계속 됩니다.

- [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="vsconoperationalmodesanchor4"></a> 한 단계씩 실행 모드
 단계 모드 코드 또는 into, 또는 함수에서 다음 줄으로 이동 하는 경우 발생 합니다. 메서드를 호출 하 여 실행 되는 단계의 [단계](../../extensibility/debugger/reference/idebugprocess3-step.md)합니다. 이 메서드를 사용 하려면 `DWORD`지정 하는 합니다 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 및 [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 입력된 매개 변수로 열거형입니다.

 프로그램 코드 또는 함수에 다음 줄으로 성공적으로 단계 또는 중단점을 설정 하거나 커서까지 실행을 중단 모드로 돌아갑니다는 DE 자동으로 전환 됩니다.

## <a name="see-also"></a>참고자료
- [실행 제어](../../extensibility/debugger/control-of-execution.md)