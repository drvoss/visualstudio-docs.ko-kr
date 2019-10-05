---
title: 'CA1023: 인덱서 다차원 안 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2b9cf9cd97dd50577a466ed4d433e0e1dbd5da4d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158041"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: 다차원 인덱서를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 둘 이상의 인덱스를 사용 하는 public 또는 protected 인덱서를 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 인덱서, 즉 인덱싱된 속성에는 단일 인덱스를 사용 해야 합니다. 다차원 인덱서는 라이브러리의 유용성을 크게 줄일 수 있습니다. 디자인 여러 인덱스에 필요한 경우 형식 논리 데이터 저장소를 나타내는지 여부를 다시 고려해 보아야 합니다. 그러지 않으면 메서드를 사용 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 유일한 정수나 문자열 인덱스를 사용 하도록 디자인을 변경 하거나 인덱서 대신 메서드를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 비표준 인덱서에 대 한 필요성을 신중 하 게 고려한 후에이 규칙에서 경고를 표시 합니다.

## <a name="example"></a>예제
 다음 예제에서는 형식 `DayOfWeek03`, 규칙을 위반 하는 다차원 인덱서를 사용 하 여 합니다. 인덱스 변환의 형식으로 볼 수 있습니다 및 메서드로 노출 보다 적절 하 게 됩니다. 형식으로 다시 디자인 `RedesignedDayOfWeek03` 규칙을 충족 하도록 합니다.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1043: 인덱서에 정수 또는 문자열 인수를 사용 하 여](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: 적절 한 속성을 사용 합니다.](../code-quality/ca1024-use-properties-where-appropriate.md)
