---
title: 로컬 항목 표시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cdbba0cfa48792127accc71cba75f8542556d67
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409375"
---
# <a name="displaying-locals"></a>로컬 항목 표시
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 항상 실행 메서드를 포함 하는 메서드를 라고도 또는 현재 메서드의 컨텍스트 내에서 이루어집니다. 실행이 일시 중지 하는 경우 Visual Studio 디버그 엔진 (DE) 로컬 변수 목록을 가져오려면 및 인수를 메서드의 지역 변수를 통칭를 호출 합니다. Visual Studio에서는 이러한 지역 및 해당 값을 표시 합니다 **지역** 창입니다.  
  
 지역 변수를 표시 하는 DE 호출을 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) EE에 속하는 메서드에 평가 컨텍스트를, 기호 공급자 (SP), 현재 실행 주소 및 바인더를 제공 합니다. 자세한 내용은 [평가 컨텍스트에](../../extensibility/debugger/evaluation-context.md)합니다. 호출이 성공 하면 합니다 `IDebugExpressionEvaluator::GetMethodProperty` 메서드가 반환 되는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 현재 실행 주소를 포함 하는 메서드를 나타내는 개체입니다.  
  
 DE 호출 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 가져오려는 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 만 지역 변수를 반환 하도록 필터링 되 고 목록을 생성 하기 위해 열거 개체 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)구조입니다. 각 구조는 이름, 형식 및 로컬 값을 포함합니다. 형식 및 값 형식이 지정 된 문자열을 표시 하기에 적합으로 저장 됩니다. 이름, 형식 및 값은 일반적으로 함께 표시 한 줄을 **지역** 창입니다.  
  
> [!NOTE]
> 합니다 **간략 한 조사식** 및 **조사식** windows는 동일한 형식 이름, 값 및 형식으로 변수를 표시할 수도 있습니다. 호출 하 여 해당 값을 가져오는 하는 반면 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 대신 `IDebugProperty2::EnumChildren`합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [로컬 항목의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)  
 지역 변수를 구현 하는 과정을 단계별로 예제를 사용 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)  
 식 계산기 (EE)를 호출 하는 디버그 엔진 (DE)를 통과 하는지 세 개의 인수를 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
