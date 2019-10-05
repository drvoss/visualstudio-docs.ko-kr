---
title: 'CA1810: 참조 형식 정적 필드를 인라인으로 초기화 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dd0372ca3264bedd6fbb17ef3c8326471cb6e99f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538917"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: 참조 형식 정적 필드를 인라인으로 초기화하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 참조 형식에서 명시적인 정적 생성자를 선언합니다.

## <a name="rule-description"></a>규칙 설명
 형식이 명시적인 정적 생성자를 선언하면 JIT(Just-in-Time) 컴파일러는 형식의 각 정적 메서드와 인스턴스 생성자에 검사를 추가하여 정적 생성자를 이전에 호출했는지 확인합니다. 정적 초기화는 정적 멤버에 액세스할 때 또는 형식의 인스턴스를 만들 때 트리거됩니다. 그러나 형식의 변수를 선언 하지만 사용 하지 않는 것을 초기화 하는 전역 상태를 변경 하는 경우 중요 한으로 사용 되는 경우 정적 초기화를 트리거되지 않습니다.

 Microsoft MSIL (intermediate language) 컴파일러를 추가 하는 모든 정적 데이터를 인라인으로 초기화 하 고 명시적인 정적 생성자 선언 되지 않은 경우는 `beforefieldinit` 플래그 및 MSIL 형식에 정적 데이터를 초기화 하는 암시적 정적 생성자 정의 합니다. JIT 컴파일러가 발생 하는 경우는 `beforefieldinit` 플래그를 대부분의 정적 생성자 검사 추가 되지 않습니다. 정적 초기화는 정적 메서드 또는 인스턴스 생성자를 호출 하기 전에 없습니다 하지만 모든 정적 필드에 액세스 하기 전에 특정 시간에 발생 하도록 보장 됩니다. 정적 초기화를 해당 형식의 변수가 선언 된 후 언제 든 지 발생할 수 있습니다 note 합니다.

 정적 생성자 검사로 인해 성능이 저하될 수 있습니다. 종종 정적 생성자는 초기화만 있는지 확인 해야 해당 정적 초기화 하는 경우 정적 필드의 첫 번째 액세스 하기 전에 발생 하는 정적 필드에만 사용 됩니다. `beforefieldinit` 동작은 이러한 및 대부분의 다른 형식에 적합 합니다. 이 적절 한 정적 초기화 전역 상태에 영향을 다음 중 하나가 true 인 경우:

- 전역 상태에 대 한 영향 비용이 많이 드는지 및 형식을 사용 하지 않는 경우 필요 하지 않습니다.

- 전역 상태 정보는 형식의 정적 필드에 액세스 하지 않고 액세스할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결하려면 모든 정적 데이터를 선언할 때 초기화하고 정적 생성자를 제거합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 안전 성능이; 별로 중요 하지 않은 경우이 규칙에서 경고를 표시 합니다. 정적 초기화로 발생 하는 전역 상태 변경 내용을 비용이 많이 드는 해야 하는지 여부 또는 형식의 정적 메서드를 호출 하거나 형식의 인스턴스를 만들 발생 보장할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 형식 `StaticConstructor`, 규칙을 위반 하는 형식이 있는 `NoStaticConstructor`, 정적 생성자는 규칙을 충족 하기 위해 인라인 초기화를 사용 하 여 대체 합니다.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 추가 된 `beforefieldinit` 플래그에 대 한 MSIL 정의에 `NoStaticConstructor` 클래스.

 **공용.class auto ansi StaticConstructor** **확장 [mscorlib]System.Object**
 **{**
 **} / / 끝 StaticConstructor클래스** 
 **.class 공용 자동 ansi beforefieldinit NoStaticConstructor** **확장 [mscorlib]System.Object**
 **{** 
 **} / / 끝 NoStaticConstructor 클래스**
## <a name="related-rules"></a>관련된 규칙
 [CA2207: 값 형식 정적 필드를 인라인으로 초기화](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
