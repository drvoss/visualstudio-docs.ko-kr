---
title: 'CA2214: 생성자에서 재정의할 수 있는 메서드를 호출 하지 마십시오. | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662904"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: 재정의 가능한 메서드를 생성자에서 호출하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 봉인 되지 않은 형식의 생성자는 해당 클래스에 정의 된 가상 메서드를 호출 합니다.

## <a name="rule-description"></a>규칙 설명
 가상 메서드가 호출 되 면 메서드를 실행 하는 실제 형식이 런타임까지 선택 되지 않습니다. 생성자가 가상 메서드를 호출 하는 경우 메서드를 호출 하는 인스턴스에 대 한 생성자가 실행 되지 않았을 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 형식의 생성자 내에서 형식의 가상 메서드를 호출 하지 마십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 가상 메서드에 대 한 호출을 제거 하려면 생성자를 다시 디자인 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 경우의 영향을 보여 줍니다. 테스트 응용 프로그램은 기본 클래스 (`BadlyConstructedType`) 생성자가 실행 되도록 하는 `DerivedType`의 인스턴스를 만듭니다. `BadlyConstructedType`의 생성자가 가상 메서드를 잘못 호출 `DoSomething`입니다. 출력에 표시 된 대로 `DerivedType.DoSomething()` 실행 되 고 `DerivedType`의 생성자가 실행 되기 전에 수행 됩니다.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 이 예제의 결과는 다음과 같습니다.

 **Base ctor를 호출 합니다.** **파생 된 DoSomething를 초기화 
? ** **파생 Ctor를 호출** 하는 
 없습니다.
