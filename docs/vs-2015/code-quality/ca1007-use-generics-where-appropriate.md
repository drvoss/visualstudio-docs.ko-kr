---
title: 'CA1007: 적합 한 제네릭을 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2d4f5f7749ad34f62e9dfa5718c6a778d6e7bebf
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704286"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: 적합한 제네릭을 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식의 참조 매개 변수를 포함 하는 외부에 표시 되는 메서드 <xref:System.Object?displayProperty=fullName>, 및 포함 된 어셈블리 대상을 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]합니다.

## <a name="rule-description"></a>규칙 설명
 참조 매개 변수는 사용 하 여 수정 된 매개 변수를 `ref` (`ByRef` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 키워드입니다. 참조 매개 변수에 제공 되는 인수 형식을 참조 매개 변수 형식과 정확히 일치 해야 합니다. 참조 매개 변수 형식에서 파생 된 형식을 사용 하려면 먼저 형식 캐스팅 하 고 참조 매개 변수 형식의 변수에 할당 해야 합니다. 제약 조건 참조 매개 변수 형식 형식으로 먼저 캐스트 하지 않고 메서드에 전달할 수에 따라 모든 형식을 허용 하는 제네릭 메서드를 사용 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 제네릭 메서드를 확인 하 고 대체 된 <xref:System.Object> 형식 매개 변수를 사용 하 여 매개 변수입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 제네릭 및 제네릭이 아닌 메서드로 구현 되는 범용 교환 루틴을 보여 줍니다. 제네릭이 아닌 메서드를 비교 하는 제네릭 메서드를 사용 하 여 문자열을 바꿀 수 있음을 얼마나 효율적으로 note 합니다.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1005: 제네릭 형식에 매개 변수를 방지 합니다.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션에서 제네릭 인터페이스를 구현 해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 제네릭 형식에 정적 멤버를 선언 하지 마십시오](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: 제네릭 목록을 노출 하지 마십시오](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마십시오.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드 형식 매개 변수를 제공 해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용 합니다.](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>참고 항목
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
