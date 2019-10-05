---
title: 'CA2230: 가변 인수로 params를 사용하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0639d30771b3a6bb288ddbf9644dda2efcd5f90d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231354"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: 가변 인수로 params를 사용하세요.

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|범주|Microsoft.Usage|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
공용 또는 보호 된 형식에 `VarArgs` 호출 규칙을 사용 하는 public 또는 protected 메서드가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
`VarArgs` 호출 규칙은 다양 한 매개 변수를 사용 하는 특정 메서드 정의와 함께 사용 됩니다. `VarArgs` 호출 규칙을 사용 하는 메서드는 CLS (공용 언어 사양) 규격이 아니고 프로그래밍 언어에서 액세스 하지 못할 수 있습니다.

에서 C#호출 규칙은 메서드의 매개 변수 `__arglist` 목록이 키워드로 끝날 때 사용 됩니다. `VarArgs` Visual Basic는 `VarArgs` 호출 규칙을 지원 하지 않으며 시각적 개체 C++ 는 타원 `...` 표기법을 사용 하는 비관리 코드 에서만 사용할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
에서 C#이 규칙 위반 문제를 해결 하려면 대신 [params](/dotnet/csharp/language-reference/keywords/params) `__arglist`키워드를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
다음 예제에서는 규칙을 위반 하는 메서드와 규칙을 충족 하는 두 가지 메서드를 보여 줍니다.

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>참고 항목

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [언어 독립성 및 언어 독립적 구성 요소](/dotnet/standard/language-independence-and-language-independent-components)