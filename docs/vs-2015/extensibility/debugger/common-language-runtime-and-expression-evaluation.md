---
title: 공용 언어 런타임 및 식 평가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b75cb1b0604f3611c0e51c6f458939433d2a5470
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383522"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>공용 언어 런타임 및 식 계산
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 컴파일러, Visual Basic 및 C# (c-sharp 발음), 공용 언어 런타임 (CLR)을 대상으로 하는 생성 언어 MSIL (Microsoft Intermediate), 이후는 같은 네이티브 코드로 컴파일됩니다. CLR (DE) 결과 코드를 디버그 하려면 디버그 엔진을 제공 합니다. 독점 프로그래밍 언어가 Visual Studio IDE에 통합 하려는 경우에 MSIL로 컴파일하는 데 선택할 수 있으며 따라서 고유한 DE 쓰기 않아도 됩니다. 그러나 프로그래밍 언어의 컨텍스트 내에서 식을 평가할 수 있는 식 계산기 (EE)를 작성 해야 합니다.  
  
## <a name="discussion"></a>토론  
 데이터 개체의 집합 및 조작 하는 데 사용 되는 연산자 집합을 생성 하는 컴퓨터 언어 식은 구문 분석 일반적으로 됩니다. 예를 들어 데이터에 더하기 연산자 (+)를 적용 하려면 분석할 수 있습니다 "A + B" 식 "A"와 "B" 발생할 다른 데이터 개체의 개체입니다. 데이터 개체, 연산자 및 해당 연결의 전체 집합을 트리 노드에서 연산자 및 분기에 데이터 개체 트리로 프로그램에서 가장 자주 표시 됩니다. 트리 형식으로 분류 되어 있는 식은 구문 분석 된 트리를 라고 합니다.  
  
 식을 구문 분석 되 면 각 데이터 개체를 평가 하는 기호 공급자 (SP) 라고 합니다. 예를 들어, "A"는 둘 이상의 메서드를 다음 질문에 정의 된 경우 "A는?" 값을 조사할 수 있습니다 전에 응답 해야 합니다. SP에서 반환한 응답은 "다섯 번째 스택 프레임에 세 번째 item" 또는 "정적 메모리의 시작 부분을 벗어나면 50 바이트는이 메서드를 할당 합니다."  
  
 프로그램 자체에 대 한 MSIL을 생성 하는 것 외에도 CLR 컴파일러는 프로그램 데이터베이스 (.pdb) 파일에 기록 되는 매우 설명이 포함 된 디버깅 정보를 생성할 수도 수 있습니다. 전용 언어 컴파일러를 같은 형식으로 CLR 컴파일러에 디버그 정보를 생성 하는 경우 CLR의 SP 하는 언어의 명명 된 데이터 개체를 식별할 수 있습니다. 명명 된 데이터 개체를 식별 한 후 EE 바인더 개체를 해당 개체의 값을 보유 하는 메모리 영역에 데이터 개체를 연결 (또는 바인딩)를 사용 합니다. 다음는 DE 가져오거나 데이터 개체에 대 한 새 값을 설정할 수 있습니다.  
  
 전용 컴파일러를 호출 하 여 정보를 디버깅 하는 CLR을 제공할 수는 `ISymbolWriter` 인터페이스 (네임 스페이스의.NET Framework에 정의 되어 있는 `System.Diagnostics.SymbolStore`). MSIL로 컴파일 하 고 이러한 인터페이스를 통해 디버그 정보를 작성, CLR DE 및 SP. 전용 컴파일러를 사용할 수 있습니다. 이 크게 Visual Studio IDE 자체 언어 통합 간소화 합니다.  
  
 CLR DE 식을 평가 하는 전용 EE를 호출 하는 경우는 DE SP를 바인더 개체 인터페이스를 사용 하 여 EE를 제공 합니다. 따라서 CLR 기반 디버그 엔진 수단을 쓰는 것이 적절 한 식 계산기 인터페이스를 구현 하는 데에 필요 CLR은 바인딩 및 기호를 처리를 담당 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
