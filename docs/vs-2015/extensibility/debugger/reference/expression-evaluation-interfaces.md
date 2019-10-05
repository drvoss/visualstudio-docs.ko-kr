---
title: 식 계산 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8a710019390120768b665cf3b27174831a67f0cc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435039"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 다음은에 대 한 식 계산 인터페이스는 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debugging SDK.  
  
## <a name="discussion"></a>토론  
 이러한 인터페이스는 중단 모드에 있는 동안 호출 스택의 식 평가에 사용 됩니다. 공용 언어 런타임 식 계산기 (EE)에 대해서만 구현 됩니다.  
  
 테이블의 각 인터페이스에서는 다음 목록에서 구현할 수 있는 구성 요소를 보여 줍니다.  
  
- 디버그 엔진 (DE)  
  
- 식 계산기 (EE)  
  
- Visual Studio (VS)  
  
|인터페이스|에 의해 구현|설명|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|변수에 대 한 숫자 별칭을 나타냅니다.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|숫자 변수에 별칭을 나타내며 식 계산기 (EE) 응용 프로그램 도메인 별칭을 가져올 수 있습니다.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|배열 개체를 나타냅니다.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|관리 되는 배열 개체를 나타내며 식 계산기 (EE) 배열에 대 한 기본 인덱스 (하위 범위)를 확인할 수 있습니다.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|바인딩합니다 디버그 메모리의 실제 주소로 기호는 바인더를 나타냅니다.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|와 동일 합니다 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 하지만 인터페이스 형식, 별칭 및 사용자 지정 시각화 도우미에 액세스를 제공 합니다.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|식 계산기를 나타냅니다.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|식 계산기 (EE)의 향상 된 버전을 나타냅니다.|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|향상 된 파서 트리는 식 계산기를 (EE)을 나타냅니다.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|함수를 나타냅니다.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|함수를 나타내는 향상 시킬 수는 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스입니다.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|디버거의 출력 창에 메시지를 표시 하는 식 계산기 (EE)을 사용 하도록 설정 합니다.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|관리 코드 개체를 나타냅니다.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|모든 기호를 나타내는 기본 인터페이스는 메모리 주소에 바인딩됩니다.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|와 동일 합니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스 하지만 추가 정보에 대 한 액세스를 제공 합니다.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|평가할 준비가 구문 분석 된 식을 나타냅니다.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|포인터를 나타냅니다.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|구문 분석 트리에 대 한 포인터를 나타내며 확장 합니다 **IDebugPointerObject** 인터페이스입니다.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|형식 시각화 도우미를 통해 형식의 값을 수정 하는 기능을 제공 합니다.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|사용자 지정 뷰어 및 형식 시각화 도우미에 대 한 액세스를 제공합니다.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|만들 수는 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 개체입니다.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|컬렉션을 나타냅니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [CLR 식 계산기 작성](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
