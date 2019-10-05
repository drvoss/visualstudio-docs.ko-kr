---
title: 'CA1043: 인덱서에 정수 또는 문자열 인수를 사용 하 여 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 643d91ad51e9511bbd4440d2f84fbd441c768a53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143208"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: 인덱서에 정수 또는 문자열 인수를 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 아닌 다른 인덱스 형식을 사용 하는 public 또는 protected 인덱서를 포함 <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>하십시오 <xref:System.Object?displayProperty=fullName>, 또는 <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>규칙 설명
 인덱서, 즉 인덱싱된 속성 인덱스에 대 한 정수 또는 문자열 형식을 사용 해야 합니다. 이러한 형식은 일반적으로 사용 데이터 구조를 인덱싱하는 및 라이브러리의 유용성을 증가 시킵니다. 사용 된 <xref:System.Object> 형식 특정 정수 또는 문자열 형식을 디자인 타임에 지정할 수 없는 이러한 경우로만 제한 해야 합니다. 디자인 가지 인덱스에 필요한 경우 형식 논리 데이터 저장소를 나타내는지 여부를 다시 고려해 보아야 합니다. 논리적 데이터 저장소를 나타내지 않는 경우에 메서드를 사용 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 정수 또는 문자열 유형으로 인덱스를 변경 하거나 대신 인덱서 메서드를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 비표준 인덱서에 대 한 필요성을 신중 하 게 고려한 후에이 규칙에서 경고를 표시 합니다.

## <a name="example"></a>예제
 다음 예제에서는 사용 하는 인덱서를 <xref:System.Int32> 인덱스입니다.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1023: 다차원 인덱서 설정 되지 않습니다.](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: 적절 한 속성을 사용 합니다.](../code-quality/ca1024-use-properties-where-appropriate.md)
