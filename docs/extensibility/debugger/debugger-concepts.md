---
title: 디버거 개념 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1d9905281c83287b8b54f57a233c2056462226f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345929"
---
# <a name="debugger-concepts"></a>디버거 개념
Visual Studio 디버그 패키지를 빌드하려면 패키지 디자인에 사용 되는 아키텍처 개념을 숙지 해야 합니다.

## <a name="in-this-section"></a>단원 내용
 [디버그 세션](../../extensibility/debugger/debug-session.md) 디버깅 아키텍처에서 세션의 역할에 설명 합니다.

 [서버](../../extensibility/debugger/servers-visual-studio-sdk.md) abstract 이면 서 실제 조건에서 아키텍처를 디버깅 하는 측면에서 어떤 서버를 정의 합니다.

 [포트 공급자](../../extensibility/debugger/port-suppliers.md) 디버깅 아키텍처 측면에서 어떤 포트 공급자가 정의 합니다.

 [포트](../../extensibility/debugger/ports.md) 어떤 포트는 디버깅 아키텍처 측면에서 정의 합니다.

 [프로세스](../../extensibility/debugger/processes.md) 어떤 프로세스는 디버깅 아키텍처 측면에서 정의 합니다.

 [노드 프로그램](../../extensibility/debugger/program-nodes.md) 디버깅 자체 및 프로세스에서 실행 중인 식별할 수 있습니다 하는 방법을 포함 한 아키텍처를 기준으로 프로그램 노드를 정의 합니다.

 [프로그램](../../extensibility/debugger/programs.md) 디버깅 아키텍처 측면에서 프로그램을 정의 합니다.

 [스레드](../../extensibility/debugger/threads.md) 스레드 디버깅 아키텍처 측면에서 특성을 정의 합니다.

 [스택 프레임](../../extensibility/debugger/stack-frames.md) 디버깅 아키텍처 측면에서 스택 프레임을 정의 합니다. 스택 프레임에는 스레드의 실행 컨텍스트를 제공 하는 스택의 추상화입니다.

 [모듈](../../extensibility/debugger/modules.md) 아키텍처와 같은 실행 파일 또는 DLL 코드의 물리적 컨테이너 디버깅 측면에서 모듈을 정의 합니다.

 [중단점](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) 세 가지 유형의 중단점 정의-보류 중 및 오류-디버깅 아키텍처를 기준으로 합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) 디버그 엔진 (DE) 동시에 코드, 설명서 및 식 평가 컨텍스트 내에서 작동 하는 방법에 대해 설명 합니다. 세 개의 컨텍스트, 위치, 위치 또는 평가를 관련 각각에 대해 설명합니다.

 [구성 요소를 디버거](../../extensibility/debugger/debugger-components.md) 디버그 엔진 (DE), 식 계산기 (EE) 및 기호 처리기 (SH) 포함 하는 Visual Studio 디버깅 구성 요소의 개요를 제공 합니다.

 [디버그 작업](../../extensibility/debugger/debugging-tasks.md) 디버깅 작업, 및와 같은 프로그램을 실행할 식을 계산 하는 다양 한 링크가 포함 되어 있습니다.