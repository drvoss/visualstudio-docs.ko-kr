---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a18f546cf43ddff7f445ac0aa04a337487de0538
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192142"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 식 계산에 대 한 컨텍스트를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE) 식이 계산 될 수 있는 컨텍스트를 나타내는 데이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 에 대 한 호출 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 반환 된 인터페이스입니다. 이 인터페이스는 디버그 중인 프로그램 일시 중지 된 스택 프레임은 사용할 수 있는 경우에 액세스할 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugExpressionContext2`합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|평가 컨텍스트에의 이름을 검색합니다.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|평가 대 한 텍스트 기반 식을 구문 분석합니다.|  
  
## <a name="remarks"></a>설명  
 평가 컨텍스트에 식 평가 수행 하는 것에 대 한 범위로 생각할 수 있습니다.  
  
 세션 디버그 관리자 (SDM) 호출 하 여 독일에서 스택 프레임을 가져옵니다 프로그램을 중지 하는 경우 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)합니다. SDM 호출 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 가져오려고 합니다 `IDebugExpressionContext2` 인터페이스입니다. 에 대 한 호출 뒤에 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 만들려는 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 계산할 준비가 구문 분석 된 식을 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
