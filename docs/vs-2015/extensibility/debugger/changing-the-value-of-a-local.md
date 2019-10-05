---
title: 로컬 값을 변경 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383447"
---
# <a name="changing-the-value-of-a-local"></a>로컬 항목 값 변경
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 값 필드에 새 값을 입력 한 경우는 **지역** 창 디버그 패키지 전달 문자열 식 계산기 (EE)을 입력 합니다. EE 간단한 값 또는 식을 포함할 수 있으며 연결 된 로컬에서 결과 값을 저장 합니다.이 문자열을 평가 합니다.  
  
 다음은 로컬 값을 변경 하는 프로세스의 개요입니다.  
  
1. Visual Studio를 호출 하는 사용자가 새 값을 입력 한 후 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 에 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 로컬 연관 된 개체입니다.  
  
2. `IDebugProperty2::SetValueAsString`는 다음 작업을 수행합니다.  
  
   1. 값을 생성 하는 문자열을 평가 합니다.  
  
   2. 연결 된 바인딩합니다 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 가져올 개체를 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체입니다.  
  
   3. 값을 일련의 바이트로 변환합니다.  
  
   4. 호출 [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) 디버깅 중인 프로그램에 액세스할 수 있도록 메모리에 값의 바이트를 배치 하 합니다.  
  
3. Visual Studio를 새로 고칩니다 합니다 **지역** 표시 (참조 [지역 표시](../../extensibility/debugger/displaying-locals.md) 세부 정보에 대 한).  
  
   변수의 값을 변경 하려면이 절차는 또한 합니다 **조사식** 제외 하 고 창은 합니다 `IDebugProperty2` 대신 사용 되는 지역 변수의 값을 사용 하 여 연결 된 개체를 `IDebugProperty2` 로컬 연관 된 개체 자체입니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [값 변경 샘플 구현](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 값을 변경 하는 과정을 단계별로 MyCEE 샘플을 사용 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)
