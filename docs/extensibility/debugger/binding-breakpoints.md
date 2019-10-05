---
title: 중단점 바인딩 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f861875e15a9051ab05d1b7398ea5902189830b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332560"
---
# <a name="bind-breakpoints"></a>중단점 바인딩
사용자 설정 중단점, 아마도 키를 눌러 **F9**, IDE 요청을 작성 하 고 중단점을 만들려고 하면 디버그 세션의 메시지를 표시 합니다.

## <a name="set-a-breakpoint"></a>중단점 설정
 중단점 설정 이므로 2 단계 프로세스, 코드 또는 중단점의 영향을 받는 데이터를 아직 사용할 수 없습니다. 중단점을 설명 해야 합니다 하 고 그런 다음 코드 또는 데이터를 사용할 수 있는,이에 연결 해야 코드 또는 데이터를 사용 하는 다음과 같이 먼저:

1. 관련 디버그 엔진 (DEs)에서 중단점을 요청 하 고 중단점에 바인딩된 코드 또는 데이터를 사용할 수 있는 키를 누릅니다.

2. 중단점 요청은 모든 관련 DEs로 전송 하는 디버그 세션에 전송 됩니다. 중단점을 처리 하도록 선택 하는 모든 DE 해당 보류 중단점을 만듭니다.

3. 디버그 세션은 보류 중인 중단점을 수집 하 고 디버그 패키지 (Visual Studio의 디버깅 구성)에 다시 보냅니다.

4. 디버그 패키지가 보류 중인 중단점 코드나 데이터에 바인딩할 디버그 세션을 요청 합니다. 디버그 세션에 모든 관련 DEs이이 요청을 보냅니다.

5. DE 중단점을 바인딩할 수 있으면 중단점 디버그 세션에 다시 이벤트를 바인딩된 보냅니다. 그렇지 않은 경우 대신 중단점 오류 이벤트를 보냅니다.

## <a name="pending-breakpoints"></a>보류 중인 중단점
 보류 중인 중단점 여러 코드 위치에 바인딩할 수 있습니다. 예를 들어, 소스 코드 줄을 C++ 템플릿 템플릿에서 생성 되는 모든 코드 시퀀스를 바인딩할 수 있습니다. 디버그 세션 중단점이 바인딩된 이벤트를 사용 하 여 이벤트가 전송 된 시간에 중단점을 바인딩할 코드 컨텍스트 열거를 수 있습니다. 자세한 코드 컨텍스트는 DE 여러 중단점 바인딩된 각 바인딩 요청에 대 한 이벤트를 보낼 수 있습니다 나중에 바인딩할 수 있습니다. 그러나는 DE 바인딩 요청당 하나의 중단점 오류 이벤트를 전송 해야 합니다.

## <a name="implementation"></a>구현
 디버그 패키지 세션 디버그 관리자 SDM ()를 호출 하 고 제공 하는 프로그래밍 방식으로 [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 래핑하는 인터페이스를 [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) 설명 하는 구조는 중단점을 설정할 수 있습니다. 중단점의 다양 한 형태를 사용할 수 있지만 궁극적으로 코드 또는 데이터 컨텍스트를 확인 합니다.

 SDM 호출 하 여 각 관련 DE이이 호출을 전달 해당 [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 메서드. 중단점을 처리 하는 DE 싶다면 만들고 반환 된 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스입니다. 이러한 인터페이스를 수집 하 고 단일 디버그 패키지로 다시 전달 하는 SDM `IDebugPendingBreakpoint2` 인터페이스입니다.

 지금 이벤트가 생성 되었습니다.

 디버그 패키지가 시도 호출 하 여 코드 또는 데이터에 보류 중인 중단점을 바인딩할 [바인딩할](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)는 DE 여 구현 하는 합니다.

 중단점 바인딩되는 DE 보냅니다는 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 디버그 패키지에 대 한 이벤트 인터페이스입니다. 모든 코드 컨텍스트 (또는 단일 데이터 컨텍스트)를 열거 하기 위해이 인터페이스를 호출 하 여 중단점을 바인딩할 디버그 패키지 사용 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)를 하나 이상 반환 하는 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 인터페이스입니다. 합니다 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) 반환 인터페이스는 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 인터페이스 및 [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 반환을 [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) 코드 또는 데이터 컨텍스트를 포함 하는 공용 구조체입니다.

 DE 중단점을 바인딩할 수 없는 경우 단일 보냅니다 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 디버그 패키지에 대 한 이벤트 인터페이스입니다. 호출 하 여 오류 유형 (오류 또는 경고) 및 정보 메시지를 검색 하는 디버그 패키지가 [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)차례로 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 고 [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)합니다. 반환이 [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) 오류 유형 및 메시지를 포함 하는 구조입니다.

 형식의 오류를 반환 하기는 DE 중단점을 처리 하지만 이어서 바인딩할 수 없습니다 경우 `BPET_TYPE_ERROR`합니다. IDE 내에서 중단점 문자 모양 소스 코드 줄의 왼쪽에는 느낌표 문자 모양 배치 및 디버그 패키지는 오류 대화 상자를 표시 하 여 응답 합니다.

 독일에 바인딩할 수도 DE 중단점을 처리 하지만, 일부 다른 바인딩할 수 없습니다 경우 경고를 반환 합니다. IDE는 소스 코드 줄의 왼쪽에 중단점 문자 모양 내 질문 문자 모양을 배치 하 여 응답 합니다.

## <a name="see-also"></a>참고자료
- [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)