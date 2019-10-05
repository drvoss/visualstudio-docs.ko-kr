---
title: 디버그 엔진을 사용자 지정 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3756eb105ec562d902d4631318e7a5fc698601a2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345310"
---
# <a name="create-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 만들기
디버그 엔진 (DE)는 구성 요소로, 특정 런타임 아키텍처를 디버깅할 수 있습니다. 일반적으로 런타임 환경 별로 하나의 DE 구현이입니다.

> [!NOTE]
> TRANSACT-SQL 및 JScript에 대 한 별도 DE 구현을 있기는 VBScript 및 JScript 단일 DE 공유 합니다.

 DE와 같은 디버깅 서비스 실행 제어, 중단점 및 식 평가를 위해 인터프리터 또는 작업 시스템에서 작동 합니다. 이러한 서비스 DE 인터페이스를 통해 구현 되 고 다른 운영 모드를 전환 하도록 디버거를 발생할 수 있습니다. 자세한 내용은 [운영 모드](../../extensibility/debugger/operational-modes.md)합니다.

 만들기는 DE 다음 단계로 구성 됩니다.

1. Visual Studio는 DE 등록

2. 디버깅할 프로그램 사용 설정

3. 실행 제어 및 상태 평가 구현 합니다.

4. 이벤트 보내기

5. 종료 및 분리

## <a name="in-this-section"></a>단원 내용
 [사용자 지정 디버그 엔진 등록](../../extensibility/debugger/registering-a-custom-debug-engine.md) 사용할 수 있도록 Visual Studio 디버그 엔진을 등록 하는 데 필요한 단계를 설명 합니다.

 [디버깅할 프로그램 사용 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) 는 프로그램을 디버그할 프로그램 DE 전에 먼저는 DE 시작 하거나 기존 프로그램에 연결에 대해 설명 합니다.

 [실행 제어 및 상태 평가 구현](../../extensibility/debugger/execution-control-and-state-evaluation.md) 이유는 응용 프로그램 디버깅에 필요 실행 제어 기능을 구현에 대해 설명 합니다.

 [이벤트 보내기](../../extensibility/debugger/sending-events.md) DCOM을 기반으로 이벤트 모델로 디버거와 DE 간의 통신을 설명 합니다.

 [종료 및 분리](../../extensibility/debugger/termination-and-detaching.md) 없습니다 중단점, 예외, 런타임 오류 또는 응용 프로그램을 디버깅할 수에 무한 루프는 즉 정상 종료를 수행 하는 방법에 설명 합니다.

 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md) 디버깅 세션에서 발생 하는 이벤트의 호출 순서에 설명 합니다.

 [방법: 사용자 지정 디버그 엔진 디버그](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) 사용자 지정 DE를 디버그 하는 방법에 설명 합니다.

## <a name="see-also"></a>참고자료
- [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)