---
title: 이벤트 전송 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a2c87b2e05e4ffe94d77333095438f43b644976
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311335"
---
# <a name="send-events"></a>이벤트 보내기
디버거가 디버그 엔진 (DE) 사이의 통신 메커니즘은 DCOM을 기반으로 하는 이벤트 모델. 이벤트를 COM 개체로 보내고 각 이벤트를 지정 하는 매개 변수를 포함 합니다.

- 이벤트를 호출 하는 DE 합니다.

- 설명 내용입니다.

- 프로세스, 프로그램 및 스레드 정보 이벤트가 발생의 컨텍스트를 식별 하는 합니다. 프로세스는 독일에서 전송 되는 이벤트에 대 한 전송 되지 않습니다.

- 동기 또는 비동기 이벤트 인지 여부를 나타내는 이벤트 형식입니다.

  모든 디버그 이벤트 메서드를 사용 하 여 보내집니다 [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)합니다.

## <a name="in-this-section"></a>단원 내용
 [이벤트 원본](../../extensibility/debugger/event-sources-visual-studio-sdk.md) 이벤트의 두 원본에 설명 합니다: 디버그 엔진 (DE) 및 세션 디버그 관리자 (SDM).

 [지원 되는 이벤트 유형](../../extensibility/debugger/supported-event-types.md) 현재 지원 되는 이벤트 형식에 설명 합니다: 비동기 및 동기입니다.

 [이벤트 설명](../../extensibility/debugger/event-descriptions.md) 이벤트 및 용도 대 한 이유를 정의 합니다.

## <a name="related-sections"></a>관련 단원
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md) 는 DE 작동 인터프리터 또는 운영 체제 디버깅 서비스를 제공 하는 방법에 대해 설명 합니다.