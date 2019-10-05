---
title: 스택 프레임 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de3a0267d366f926fa5705c7455b237cafe4820a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348504"
---
# <a name="stack-frames"></a>스택 프레임
디버거 아키텍처에는 *스택 프레임*:

- 스레드의 실행 컨텍스트를 제공 하는 스택의 추상화가입니다. 스레드는 항상 함수 내에서 실행 됩니다. 스택 프레임에 인수를 함수의 로컬 변수를 보유합니다. Visual Studio를 사용 하 여 디버그 하기 위해 언어 또는 디버깅 중인 환경 스택 프레임을 지원 해야 합니다.

- 수 모두 파악 자체에 대해 설명 하 고 관련된 스레드를 반환할 수 있습니다. 스택 프레임을 현재 명령 포인터 및 관련된 설명서를 나타내는 코드 컨텍스트 및 식 평가 컨텍스트를 반환할 수도 있습니다.

- 이름, 형식 및 지역 변수 및 인수 값을 설명 하 고 다양 한 IDE 디버그 창에 표시 되는 속성이 있습니다.

- 로 표시 됩니다는 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스를 일반적으로 디버그 엔진 (DE), 가상 머신에서 스레드 실행의 결과로 생성 합니다.

## <a name="see-also"></a>참고자료
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)