---
title: 디버그할 프로그램을 사용 하도록 설정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b939b692e4e93243f5f346fcd2fcb2872e989615
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341637"
---
# <a name="enable-a-program-to-be-debugged"></a>디버깅할 프로그램 사용 설정
디버그 엔진 (DE) 프로그램을 디버그하기 전에 먼저는 DE 시작 하거나 기존 프로그램에 연결 합니다.

## <a name="in-this-section"></a>단원 내용
 [포트를 가져오기](../../extensibility/debugger/getting-a-port.md) 디버그할 프로그램을 사용 하도록 설정 하는 첫 번째 단계로 포트를 가져오는 방법에 설명 합니다.

 [프로그램을 등록](../../extensibility/debugger/registering-the-program.md) 디버그할 프로그램을 사용 하도록 설정 하는 다음 단계를 설명 합니다: 포트를 사용 하 여 등록 합니다. 등록 되 면 프로그램을 디버깅할 수 있습니다 하거나 프로세스를 연결 하거나 디버깅 하는 시간 (JIT)입니다.

 [프로그램에 연결](../../extensibility/debugger/attaching-to-the-program.md) 다음 단계에 설명 합니다: 프로그램에 디버거를 연결 합니다.

 [실행 기반 첨부](../../extensibility/debugger/launch-based-attachment.md) SDM 하 여 시작 시 자동 프로그램 실행 기반 첨부 파일에 설명 합니다.

 [필요한 이벤트를 보내는](../../extensibility/debugger/sending-the-required-events.md) 디버그 엔진 (DE)를 만들 때 필수 이벤트를 단계별로 안내 하 고 프로그램에 연결 합니다.

## <a name="related-sections"></a>관련 단원
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md) 디버그 엔진 (DE)를 정의 하 고 어떻게 서로 다른 운영 모드를 전환 하도록 디버거를 초래할 수 있습니다 및 DE 인터페이스를 통해 구현 된 서비스를 설명 합니다.