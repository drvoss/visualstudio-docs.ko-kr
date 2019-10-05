---
title: 디버거 확장성 시작 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99e2dabf18d3d00034d65a94c41f2e435ad64114
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350007"
---
# <a name="get-started-with-debugger-extensibility"></a>디버거 확장성 시작
합니다 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 만들고 디버거 구성 요소 내에서 프로그램을 디버그 하는 데 사용자 지정 해야 하는 정보를 제공 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 환경입니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 가 이전에 수행 하는 테스트가 광범위 한 유용성에서 파생 하는 향상 된 추가 디버깅 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거. 사용할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다국어 응용 프로그램을 단계별로 디버깅 즉석에서 응용 프로그램 및 다중 언어 솔루션을 디버깅 하는 동안 변수 편집 구현할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅 실행된-out-of-process 디버깅 중인 프로그램을 사용 하 여 이며 따라서 응용 프로그램의 프로세스 공간에서 개입 수준이 낮습니다. 따라서 디버깅 프로그램 영향을 주지 않고 디버거를 사용 하 여 상호 작용 하는 구성 요소를 작성할 쉽습니다.

 효율적으로 사용 하는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], 다음 항목에 알고 있어야 합니다.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 (IDE)

- C++ 프로그래밍 언어

- ATL COM

## <a name="in-this-section"></a>단원 내용
 [디버거 확장 로드맵](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) 컴파일러 및 해당 출력에 따라 제품에서 디버깅을 구현 하는 과정에 간략하게 설명 합니다.

 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md) 의 개요를 제공 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버그 엔진 (DE), 식 계산기 (EE) 및 기호 처리기 (SH)를 포함 하는 구성 요소를 디버깅 합니다.

 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 디버깅 주요 아키텍처 개념을 설명 합니다.

 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) 디버그 엔진 (DE) 동시에 코드, 설명서 및 식 평가 컨텍스트 내에서 작동 하는 방법에 대해 설명 합니다. 세 개의 컨텍스트, 위치, 위치 또는 평가를 관련 각각에 대해 설명합니다.

 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md) 디버깅 작업, 및와 같은 프로그램을 실행할 식을 계산 하는 다양 한 링크가 포함 되어 있습니다.