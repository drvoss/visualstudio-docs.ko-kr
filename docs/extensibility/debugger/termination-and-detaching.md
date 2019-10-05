---
title: 종료 및 분리 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aafb94e0a07462d93cc77a34f7199f61f944d0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333720"
---
# <a name="termination-and-detaching"></a>종료 및 분리
다음 섹션에서는 정상 종료를 설명합니다.

## <a name="discussion"></a>토론
 후 합니다 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 하거나 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 인터페이스 계속 없습니다 중단점, 예외, 런타임 오류 또는 응용 프로그램을 디버깅할 수에 무한 루프에 있는 경우 디버깅 중인 프로그램이 완료 될 때까지 실행 됩니다. 이 프로세스는 정상적으로 종료 합니다.

 보내야 하는 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 정상 종료를 구현 합니다. 정상 종료 실행 되어야 합니다 [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) 메서드.

## <a name="see-also"></a>참고자료
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)