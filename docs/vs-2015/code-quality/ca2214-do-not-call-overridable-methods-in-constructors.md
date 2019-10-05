---
title: 'CA2214: 생성자의 재정의 가능한 메서드를 호출 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a2e107429bb48b2bf17a625e25866a19c7781b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142413"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: 재정의 가능한 메서드를 생성자에서 호출하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 봉인 되지 않은 형식의 생성자는 해당 클래스에 정의 된 가상 메서드를 호출 합니다.

## <a name="rule-description"></a>규칙 설명
 가상 메서드가 호출 되 면 런타임까지 메서드를 실행 하는 실제 형식을 선택 하지 않았습니다. 생성자는 가상 메서드를 호출 하는 경우 가능 메서드를 호출 하는 인스턴스에 대해 생성자가 실행 되지 않도록 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 형식의 생성자 내에서 형식의 가상 메서드를 호출 하지 마세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 생성자는 가상 메서드에 대 한 호출을 제거 하기 위해 다시 디자인 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반의 효과 보여 줍니다. 테스트 응용 프로그램의 인스턴스를 만듭니다 `DerivedType`, 기본 클래스인 경우 (`BadlyConstructedType`) 생성자를 실행 합니다. `BadlyConstructedType`생성자의 가상 메서드를 올바르게 호출 `DoSomething`합니다. 출력에서 볼 수 있듯이 `DerivedType.DoSomething()` 실행 되 고 되기 전에 `DerivedType`의 생성자를 실행 합니다.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 이 예제의 결과는 다음과 같습니다.

 **기본 생성자를 호출 합니다.** 
**파생 DoSomething 라고-초기화? 아니오**
**호출 ctor를 파생 합니다.**
