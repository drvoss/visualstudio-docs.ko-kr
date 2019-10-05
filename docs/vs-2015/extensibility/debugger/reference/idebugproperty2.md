---
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f72a66e6dbfe2749910019760c16f6363498785
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403268"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 스택 프레임 속성, 프로그램 문서 속성 또는 다른 일부 속성을 나타냅니다. 속성은 일반적으로 식 평가의 결과입니다.  
  
> [!NOTE]
> "Property"이이 사용 해야 혼동 하지 해당 클래스의 멤버 변수 의미 하지만 `IDebugProperty2` 이러한 엔터티를 나타낼 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE 특정 종류의 값을 나타내는 데이 인터페이스를 구현 합니다. 예를 들어, 값 식 계산, 메모리 또는 레지스터 및 해당 값의 목록을 표시 하는 데 메모리 컨텍스트 결과로 숫자 값을 수 있습니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 호출 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 하거나 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 평가의 결과 나타내는이 인터페이스를 가져올 수 있습니다. `IDebugExpression2::EvaluateAsync` 전송 하 여이 인터페이스를 반환 합니다는 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 인터페이스를 호출 하는 SDM [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 속성을 검색 합니다.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) 관련된 스크립트 문서를 제공 하려면이 인터페이스를 반환 합니다.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) 함수의 반환 값을 표시 하려면이 인터페이스를 반환 합니다.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) 이름을 또는 메모리 컨텍스트에서 같은 프로그램의 다양 한 속성을 나타내는 데이 인터페이스를 반환 합니다.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 로컬 변수와 같은 스택 프레임의 다양 한 속성을 나타내기 위해이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugProperty2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|채웁니다를 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 속성을 설명 하는 구조입니다.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|문자열에서 속성의 값을 설정 합니다.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|지정한 참조의 값에서 속성의 값을 설정 합니다.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|속성의 자식을 열거합니다.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|속성의 부모를 반환 합니다.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|속성의 가장 많이 파생 된 속성을 설명 하는 속성을 반환 합니다.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|속성의 값을 구성 하는 메모리 (바이트)를 반환 합니다.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|속성 값에 대 한 메모리 컨텍스트를 반환합니다.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|속성 값의 바이트에서 크기를 반환 합니다.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|이 속성의이 값에 대 한 참조를 반환합니다.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|속성의 확장된 정보를 반환합니다.|  
  
## <a name="remarks"></a>설명  
 속성에 의해 표시 된 대로 `IDebugProperty2` 인터페이스, 이름, 형식 및 주소를 사용 하 여 값으로 생각할 수 있습니다. 보다 일반적인 용어로 `IDebugProperty2` 부모 및 자식 노드를 사용 하 여 계층 구조는 모든 항목을 나타낼 수 있습니다.  
  
 속성은 일반적으로 일시적인 지속만 현재 스택 프레임으로 예를 들어 있습니다. 반면에 의해 표시 된 대로 참조를 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 인터페이스 유지 되는 기간 값을 메모리에 유지 합니다.  
  
 IDE에서 사용할 수는 `IDebugProperty2` 인터페이스를 검색 하 고 런타임에 속성을 수정할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
