---
title: 'CA2242: NaN에 대해 정확하게 테스트하십시오.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e74ec49667a4fe66c399bd15e8b24aa6589ce88
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237836"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: NaN에 대해 정확하게 테스트하십시오.

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
식은 또는 <xref:System.Single.NaN?displayProperty=fullName> <xref:System.Double.NaN?displayProperty=fullName>에 대해 값을 테스트 합니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Double.NaN?displayProperty=fullName>-숫자가 아닌를 나타내는 이며 산술 연산이 정의 되지 않은 경우에 발생 합니다. 값이 같은지 여부를 테스트 하 고 <xref:System.Double.NaN?displayProperty=fullName> 항상를 반환 `false`하는 식입니다. 값이 같지 않은지 테스트 하 고 <xref:System.Double.NaN?displayProperty=fullName> 항상를 반환 `true`하는 식입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하 고 값이 나타내는지 <xref:System.Double.NaN?displayProperty=fullName>여부를 정확 하 게 확인 하려면 또는 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 를 사용 <xref:System.Single.IsNaN%2A?displayProperty=fullName> 하 여 값을 테스트 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
다음 예에서는에 대해 <xref:System.Double.NaN?displayProperty=fullName> 잘못 된 값을 테스트 하는 두 개의 식과 값을 테스트 하기 위해 올바르게 사용 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 하는 식을 보여 줍니다.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]