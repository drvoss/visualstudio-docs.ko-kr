---
title: IDebugBinder | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc00c50e3c340ab0685ab1010c6e924e77a18a09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431703"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 이 인터페이스는 일반적으로 메모리 컨텍스트 또는 기호의 현재 값이 포함 된 개체에 기호 공급자에 의해 반환 되는 기호 필드를 바인딩합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 식 평가 지원 하며 디버그 엔진 (DE)에 의해 구현 되어야 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 이 인터페이스는 식 평가 중 사용 되 고 구현의 일반적으로 사용 됩니다 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 하 고 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugBinder`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|메모리 컨텍스트 또는 기호의 현재 값이 포함 된 개체를 가져옵니다.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|개체의 런타임 형식을 결정합니다.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|메모리 컨텍스트 개체 위치 또는 메모리 주소를 변환합니다.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|가져옵니다는 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 함수 매개 변수를 만드는 데 사용 되는 개체입니다.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|변수에 대 한 정확한 형식을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스에서 식 계산기에서 사용 되는 개체 트리를 구문 분석을 반환 합니다. 식 계산기의 인스턴스를 식에서 기호를 변환 하려면 기호 공급자를 사용 하 여 식을 구문 분석 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), 해당 유형 및 소스 코드의 위치를 기준으로 각 기호를 설명 하는 합니다. 합니다 [바인딩할](../../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드 변환 `IDebugField` 개체를 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 메모리의 실제 값에 연결 하거나 기호 바인딩 개체를 입력 합니다. 이러한 `IDebugObject` 개체 이후 평가 대 한 구문 분석 트리에 저장 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
