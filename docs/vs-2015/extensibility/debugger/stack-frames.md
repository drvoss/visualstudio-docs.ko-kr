---
title: 스택 프레임 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423389"
---
# <a name="stack-frames"></a>스택 프레임
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면을 **스택 프레임**:  
  
- 스레드의 실행 컨텍스트를 제공 하는 스택의 추상화가입니다. 스레드는 항상 함수 내에서 실행 됩니다. 스택 프레임에 지역 변수, 함수 및 인수를 보유합니다. Visual Studio를 사용 하 여 디버그 하기 위해 언어 또는 디버깅 중인 환경 스택 프레임을 지원 해야 합니다.  
  
- 수 모두 파악 자체에 대해 설명 하 고 관련된 스레드를 반환할 수 있습니다. 스택 프레임을 현재 명령 포인터와 관련된 설명서를 나타내는 코드 컨텍스트 및 식 평가 컨텍스트를 반환할 수도 있습니다.  
  
- 이름, 형식 및 지역 변수 및 인수 값을 설명 하 고 다양 한 IDE 디버그 창에 표시 되는 속성이 있습니다.  
  
- 로 표시 됩니다는 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스를 일반적으로 디버그 엔진 (DE), 가상 머신에서 스레드 실행의 결과로 생성 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
