---
title: 'CA2104: 변경 가능한 읽기 전용 참조 형식을 선언 하지 마십시오.'
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232963"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: 변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|범주|Microsoft.Security|
|주요 변경 내용|최신이 아님|

> [!NOTE]
> Rule CA2104는 사용 되지 않으며 Visual Studio의 이후 버전에서 제거 됩니다. 형식의 실제 불변성을 결정 하는 데 필요한 복잡 한 분석으로 인해 [분석기](roslyn-analyzers-overview.md) 로 구현 되지 않습니다.

## <a name="cause"></a>원인

외부에서 볼 수 있는 형식에 변경 가능한 참조 형식인, 외부에서 볼 수 있는 읽기 전용 필드가 포함되었습니다.

## <a name="rule-description"></a>규칙 설명

변경 가능한 형식은 해당 인스턴스 데이터를 수정할 수 있는 형식을 말합니다. 클래스 <xref:System.Text.StringBuilder?displayProperty=fullName> 는 변경 가능한 참조 형식의 예입니다. 클래스의 인스턴스 값을 변경할 수 있는 멤버가 포함 되어 있습니다. 변경할 수 <xref:System.String?displayProperty=fullName> 없는 참조 형식의 예는 클래스입니다. 인스턴스화된 후에는 해당 값이 변경 되지 않습니다.

참조 형식 필드 (의 C#경우 C++) 또는 참조 형식 필드 (의 경우)에 C++대 한 읽기 전용 한정자 (에서[readonly](/dotnet/csharp/language-reference/keywords/readonly) [, in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/readonly) 및 [const](/cpp/cpp/const-cpp) )는 필드가 참조 형식의 다른 인스턴스로 대체 되지 않도록 합니다. 그러나 한정자는 필드의 인스턴스 데이터가 참조 형식을 통해 수정 되는 것을 방지 하지 않습니다.

이 규칙은 실제로 변경할 수 없는 형식에 대 한 위반을 실수로 표시할 수 있습니다. 이 경우 경고를 표시 하지 않는 것이 안전 합니다.

읽기 전용 배열 필드는이 규칙에서 제외 되지만 대신 [CA2105를 위반 합니다. 배열 필드는 읽기 전용](../code-quality/ca2105-array-fields-should-not-be-read-only.md) 규칙이 아니어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 읽기 전용 한정자를 제거 하거나, 주요 변경 내용이 허용 되는 경우 필드를 변경할 수 없는 형식으로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

필드 형식을 변경할 수 없는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제

다음 예제에서는이 규칙을 위반 하는 필드 선언을 보여 줍니다.

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]