---
title: 'CA1007: 적합한 제네릭을 사용하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0d7783bea936b04fcb600563dadea6a65ac5ef5e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236516"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: 적합한 제네릭을 사용하세요.

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|범주|Microsoft.Design|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
외부에 표시 되는 메서드에는 형식의 <xref:System.Object?displayProperty=fullName>참조 매개 변수 및 포함 하는 어셈블리 대상 .NET Framework 2.0이 포함 됩니다.

## <a name="rule-description"></a>규칙 설명
참조 매개 변수는 `ref` (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 키워드를 사용 하 여 수정 되는 매개 변수입니다. 참조 매개 변수에 대해 제공 된 인수 형식은 참조 매개 변수 형식과 정확 하 게 일치 해야 합니다. 참조 매개 변수 형식에서 파생 된 형식을 사용 하려면 먼저 형식을 캐스팅 하 고 참조 매개 변수 형식의 변수에 할당 해야 합니다. 제네릭 메서드를 사용 하면 형식을 참조 매개 변수 형식으로 먼저 캐스팅 하지 않고 제약 조건에 따라 모든 형식을 메서드에 전달할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 메서드를 제네릭으로 설정 하 고 형식 매개 <xref:System.Object> 변수를 사용 하 여 매개 변수를 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
다음 예제에서는 제네릭이 아닌 메서드와 제네릭 메서드로 구현 되는 범용 교환 루틴을 보여 줍니다. 제네릭이 아닌 메서드와 비교 하 여 제네릭 메서드를 사용 하 여 문자열을 효율적으로 교환 하는 방법을 확인 합니다.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>관련 규칙
[CA1005: 제네릭 형식에 대 한 과도 한 매개 변수 방지](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: 컬렉션은 제네릭 인터페이스를 구현 해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: 정적 멤버를 제네릭 형식으로 선언 하지 마십시오.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: 제네릭 목록을 노출 하지 않습니다.](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마십시오.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: 제네릭 메서드는 형식 매개 변수를 제공 해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: 제네릭 이벤트 처리기 인스턴스 사용](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>참고 항목
[제네릭](/dotnet/csharp/programming-guide/generics/index)