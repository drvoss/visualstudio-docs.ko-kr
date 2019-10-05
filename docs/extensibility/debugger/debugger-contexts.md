---
title: 디버거 컨텍스트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 011999929fd4cb1508bf4958629e622684f35739
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345990"
---
# <a name="debugger-contexts"></a>디버거 컨텍스트
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅, 디버그 엔진 (DE) 동시에 여러 고유한 컨텍스트 내에서 같이 작동 합니다.

- 프로그램의 실행 스트림의 현재 위치를 설명 하는 코드 컨텍스트.

- 문서 컨텍스트 또는 원본 문서 내의 현재 위치를 설명 하는 위치입니다.

- 식 계산 컨텍스트는 식의 평가 수행 하는 컨텍스트를 설명 합니다.

## <a name="in-this-section"></a>단원 내용
 [코드 컨텍스트](../../extensibility/debugger/code-context.md) 코드를 지침은, 하지만 다른 방법 변수로 표현 되지 않을 수 있습니다 위치 않던 언어 및 오늘날의 런타임 아키텍처에서 프로그램의 명령 스트림의 주소로 코드 컨텍스트에 설명 합니다.

 [문서 위치](../../extensibility/debugger/document-position.md) Visual Studio IDE에 알려진 소스 파일의 위치는 추상화를 사용 하 여 디버깅에 문서 위치를 정의 합니다.

 [문서 컨텍스트](../../extensibility/debugger/document-context.md) 문서 컨텍스트를 나타내는 원본 파일과 관련 된 Visual Studio 디버깅에 대해 설명 합니다. 도 문서 컨텍스트에 기호 처리기 코드 컨텍스트를 매핑하는 방법에 대해 설명 합니다.

 [식 계산 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md) Visual Studio에서 식 평가 컨텍스트에 대 한 정보를 제공 합니다. 예를 들어, 스택 프레임과 연결 된 식 계산 컨텍스트를 로컬 변수, 메서드 매개 변수 및 클래스 멤버를 평가 하는 것에 대 한 컨텍스트를 제공 합니다.

## <a name="related-sections"></a>관련 단원
 [개념 디버그](../../extensibility/debugger/debugger-concepts.md) 디버깅 주요 아키텍처 개념을 설명 합니다.

 [구성 요소를 디버깅할](../../extensibility/debugger/debugger-components.md) Visual Studio 디버그 엔진 (DE), 식 계산기 (EE) 및 기호 처리기 (SH)를 포함 하는 구성 요소 디버깅의 개요를 제공 합니다.

 [디버그 작업](../../extensibility/debugger/debugging-tasks.md) 디버깅 작업, 및와 같은 프로그램을 실행할 식을 계산 하는 다양 한 링크가 포함 되어 있습니다.