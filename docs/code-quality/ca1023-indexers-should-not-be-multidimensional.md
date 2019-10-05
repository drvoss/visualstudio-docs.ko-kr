---
title: 'CA1023: 다차원 인덱서를 사용하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f788ded21ef5dd9c84d218cedb55ec8dcf7eff2d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236173"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: 다차원 인덱서를 사용하지 마세요.

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|범주|Microsoft.Design|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
Public 또는 protected 형식이 둘 이상의 인덱스를 사용 하는 공용 또는 보호 된 인덱서를 포함 합니다.

## <a name="rule-description"></a>규칙 설명
인덱싱된 속성인 인덱서는 단일 인덱스를 사용 해야 합니다. 다차원 인덱서를 사용 하면 라이브러리의 유용성을 크게 줄일 수 있습니다. 디자인에 여러 인덱스가 필요한 경우 형식이 논리적 데이터 저장소를 나타내는지 여부를 고려해 야 합니다. 그렇지 않은 경우 메서드를 사용 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 유일한 정수 또는 문자열 인덱스를 사용 하도록 디자인을 변경 하거나 인덱서 대신 메서드를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
비표준 인덱서에 대 한 필요성을 신중 하 게 고려한 후에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제
다음 예제에서는 규칙을 위반 하 `DayOfWeek03`는 다차원 인덱서가 포함 된 형식을 보여 줍니다. 인덱서는 변환 형식으로 볼 수 있으므로 메서드로 보다 적절 하 게 노출 됩니다. 규칙을 충족 하기 위해 `RedesignedDayOfWeek03` 형식이에서 다시 디자인 되었습니다.

[!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
[!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
[!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>관련 규칙
[CA1043: 인덱서에 정수 또는 문자열 인수를 사용 하십시오.](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

[CA1024: 적절 한 경우 속성 사용](../code-quality/ca1024-use-properties-where-appropriate.md)