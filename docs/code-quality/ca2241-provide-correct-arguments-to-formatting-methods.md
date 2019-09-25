---
title: 'CA2241: 서식 지정 메서드에 올바른 인수를 제공하십시오.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 10a4cdaa1e2de768cadc569424a490aa4adb7135
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253208"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: 서식 지정 메서드에 올바른 인수를 제공하십시오.

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
<xref:System.Console.WriteLine%2A>, `format` 또는<xref:System.Console.Write%2A>와 같은 메서드에 전달 된 문자열 인수에 각 개체 인수에 해당 하는 형식 항목이 포함 되어 있지 않거나 그 반대의 경우도 마찬가지입니다. <xref:System.String.Format%2A?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
<xref:System.Console.WriteLine%2A> <xref:System.Object?displayProperty=fullName> ,<xref:System.String.Format%2A> , 등의 메서드에 대 한 인수는 형식 문자열과 여러 인스턴스로 구성 됩니다. <xref:System.Console.Write%2A> 서식 문자열은 {index [, alignment] [: formatString]} 형식의 텍스트 및 포함 된 서식 항목으로 구성 됩니다. 'index'는 형식을 지정할 개체 부분을 나타내는 0부터 시작하는 정수입니다. 개체에 형식 문자열의 해당 인덱스가 없는 경우 개체는 무시 됩니다. ' Index ' <xref:System.FormatException?displayProperty=fullName> 로 지정 된 개체가 없으면 런타임에이 throw 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 각 개체 인수에 형식 항목을 제공 하 고 각 형식 항목에 대 한 개체 인수를 제공 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
다음 예제에서는 규칙의 두 가지 위반을 보여 줍니다.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]