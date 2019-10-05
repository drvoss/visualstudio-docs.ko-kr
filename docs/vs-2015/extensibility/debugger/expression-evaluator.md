---
title: 식 계산기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 423df66e8bd6bc1257a32236aa4ffbb28b80d655
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152748"
---
# <a name="expression-evaluator"></a>식 계산기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

식 계산기 (EE)를 IDE 중단 모드에 있을 때 사용자가 볼 수 있도록 하는 언어 구문 분석 하 고 런타임 시 변수 및 식 평가를 구문을 검사 합니다.  
  
## <a name="using-expression-evaluators"></a>식 계산기를 사용 하 여  
 식을 사용 하 여 만들어집니다 합니다 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 다음과 같이 합니다.  
  
1. 디버그 엔진 (DE)를 구현 하는 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다.  
  
2. 디버그 패키지를 가져옵니다는 `IDebugExpressionContext2` 에서 개체를 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스 및 호출 합니다 `IDebugStackFrame2::ParseText` 메서드를 가져오려고는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체입니다.  
  
3. 디버그 패키지 호출을 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 메서드 또는 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드를 식의 값을 가져옵니다. `IDebugExpression2::EvaluateAsync` 명령/직접 실행 창에서 호출 됩니다. 다른 모든 UI 구성 요소 호출 `IDebugExpression2::EvaluateSync`합니다.  
  
4. 식 계산의 결과 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 이름, 형식 및 식 평가의 결과 값을 포함 하는 개체입니다.  
  
   식 평가 중 EE 기호 공급자 구성 요소 정보가 필요 합니다. 기호 공급자를 식별 하 고 구문 분석된 된 식을 이해에 사용 되는 기호 정보를 제공 합니다.  
  
   비동기 식 평가 완료 하는 경우 비동기 이벤트 완료 식 평가 IDE에 알리기 위해 세션 디버그 관리자 SDM ()를 통해 독일에서 전송 됩니다. 평가의 결과에 대 한 호출에서 반환 됩니다 동기 식 평가 완료 하는 경우는 `IDebugExpression2::EvaluateSync` 메서드.  
  
## <a name="implementation-notes"></a>구현 참고 사항  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 공용 언어 런타임 (CLR) 인터페이스를 사용 하 여 식 계산기를 사용 하 여 이야기 하고자 하는 디버그 엔진입니다. 결과적으로, 식 계산기를 함께 작동 하는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버그 엔진에서 CLR를 지원 해야 합니다 (모든 CLR 디버깅 인터페이스의 전체 목록은 일부인 debugref.doc에서 찾을 수 있습니다의 [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]).  
  
## <a name="see-also"></a>관련 항목  
 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
