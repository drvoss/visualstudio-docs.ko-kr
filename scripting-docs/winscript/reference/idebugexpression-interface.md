---
title: IDebugExpression 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1757317e9ab148b508bfed95107b5c3b3369b598
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430020"
---
# <a name="idebugexpression-interface"></a>IDebugExpression 인터페이스
비동기적으로 평가된 식을 나타냅니다. 스크립트 엔진은 일반적으로이 인터페이스를 구현 합니다. 디버거 IDE는 일반적으로 사용을 즉시 실행 창 또는 조사식 창에이 인터페이스를 사용 합니다.  
  
> [!NOTE]
> `IDebugExpression` 인터페이스는 스택 프레임 에서만에서 사용할 수 있습니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugExpression` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|식의 평가 시작합니다.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|식을 중단합니다.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|작업이 완료 되는 경우를 결정 합니다.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|문자열 작업의 반환 값을 식 평가의 결과 반환합니다.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|디버그 속성 및 작업의 반환 값 식 평가의 결과 반환합니다.|