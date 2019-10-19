---
title: 'CA1043: 인덱서에 정수 또는 문자열 인수를 사용 하십시오. | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 528b3a1f301544ccb20cfa6bddc31c0a5c50d1ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668298"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: 인덱서에 정수 또는 문자열 인수를 사용하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> 또는 <xref:System.String?displayProperty=fullName> 이외의 인덱스 유형을 사용 하는 public 또는 protected 인덱서를 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 인덱싱된 속성인 인덱서는 인덱스에 정수 또는 문자열 형식을 사용 해야 합니다. 이러한 형식은 일반적으로 데이터 구조를 인덱싱하는 데 사용 되며 라이브러리의 유용성을 향상 시킵니다. @No__t_0 형식의 사용은 디자인 타임에 특정 정수 또는 문자열 형식을 지정할 수 없는 경우에만 사용 해야 합니다. 디자인에서 인덱스에 다른 형식이 필요한 경우 형식이 논리적 데이터 저장소를 나타내는지 여부를 고려해 야 합니다. 논리적 데이터 저장소를 나타내지 않는 경우 메서드를 사용 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 인덱스를 정수 또는 문자열 유형으로 변경 하거나 인덱서 대신 메서드를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 비표준 인덱서에 대 한 필요성을 신중 하 게 고려한 후에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제
 다음 예에서는 <xref:System.Int32> 인덱스를 사용 하는 인덱서를 보여 줍니다.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1023: 다차원 인덱서는 사용하지 마십시오.](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: 적합한 속성을 사용하십시오.](../code-quality/ca1024-use-properties-where-appropriate.md)
