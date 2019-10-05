---
title: 공용 언어 런타임 식 계산기 작성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 961a4d646a61fedda381f9451902b3bcdcc956d6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435274"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>공용 언어 런타임 식 계산기 작성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 식 계산기 (EE) 구문을 처리 하는 디버그 엔진 (DE)의 일부 이며 디버깅 중인 코드를 생성 하는 프로그래밍 언어의 의미 체계. 프로그래밍 언어의 컨텍스트 내에서 식 평가 되어야 합니다. 예를 들어, 일부 언어에서 식 "A + B" 의미 "합계 a와 B" 다른 언어에서는 같은 식 것일 수 "는 또는 2." 따라서 별도 EE 써야 Visual Studio IDE에서 코드를 디버깅할 개체를 생성 하는 각 프로그래밍 언어에 대 한 합니다.  
  
 Visual Studio 디버그 패키지의 일부 구성 요소는 프로그래밍 언어의 컨텍스트에서 코드를 해석 해야 합니다. 예를 들어 경우 실행이 중단 된 중단점에 사용자가 입력 하는 모든 식에는 **조사식** 창을 평가 하 고 표시 해야 합니다. 사용자가에 식을 입력 하 여 로컬 변수의 값을 변경할 수는 또한을 **Watch** 창 또는 합니다 **직접 실행** 창.  
  
## <a name="in-this-section"></a>섹션 내용  
 [공용 언어 런타임 및 식 계산](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Visual Studio IDE에 소유 프로그래밍 언어를 통합 하는 경우는 EE 쓰기 전용 언어의 컨텍스트 내에서 식을 평가할 수 있는 컴파일할 수 있도록는 MSIL (Microsoft intermediate language)을 설명 합니다. 디버그 엔진을 작성 하지 않고  
  
 [식 계산기 아키텍처](../../extensibility/debugger/expression-evaluator-architecture.md)  
 필요한 EE 인터페이스를 구현 및 공용 언어 런타임 기호 공급자 (SP) 및 바인더 인터페이스를 호출 하는 방법에 설명 합니다.  
  
 [식 계산기 등록](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 등록 하는 EE 해야 자체 공용 언어 런타임 및 Visual Studio 런타임 환경을 모두 사용 하 여 클래스 팩터리로 기록 됩니다.  
  
 [식 계산기 구현](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 식을 평가 하 여 프로세스 디버그 엔진 (DE), 기호 공급자 (SP), 바인더 개체 및 식 계산기 (EE)을 포함 하는 방법을 설명 합니다.  
  
 [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)  
 호출 하는 방법, 실행이 일시 중지 하는 경우 디버그 패키지가 로컬 변수 및 인수 목록을 가져오려면 DE 설명 합니다.  
  
 [조사식 창 식 계산](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Visual Studio 디버그 패키지는 조사 목록에서 각 식의 현재 값을 확인 하는 DE를 호출 하는 방법을 설명 합니다.  
  
 [로컬 항목 값 변경](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 로컬 값을 변경, 지역 창의 각 줄에 이름, 형식 및 로컬의 현재 값을 제공 하는 연결된 개체를 설명 합니다.  
  
 [형식 시각화 도우미 및 사용자 지정 뷰어 구현](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 형식 시각화 도우미 및 사용자 지정 뷰어를 지원 하도록 구성 요소에서 구현 해야 하는 인터페이스에 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
