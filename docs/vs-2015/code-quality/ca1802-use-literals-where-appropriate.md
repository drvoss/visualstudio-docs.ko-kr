---
title: 'CA1802: 리터럴을 사용 하십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5990d8ea3720098651d3ed696f6ee5ff907b82f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143142"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: 가능하면 리터럴을 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 필드가 선언 되었습니다 `static` 하 고 `readonly` (`Shared` 및 `ReadOnly` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), 컴파일 시간에 계산할 수 있는 값으로 초기화 됩니다.

## <a name="rule-description"></a>규칙 설명
 값을 `static``readonly` 필드 선언 형식에 대 한 정적 생성자를 호출할 때 런타임 시 계산 됩니다. 경우는 `static``readonly` 필드 선언 되 고 정적 생성자 선언 되지 않았습니다 명시적으로 컴파일러에서 필드를 초기화 하는 정적 생성자는 초기화 됩니다.

 값을 `const` 필드는 컴파일 시 계산 하며에 비하면 런타임 성능을 향상 시키는 메타 데이터에 저장을 `static``readonly` 필드입니다.

 컴파일 시간에 대상된 필드에 할당 된 값을 계산할 이기 때문에 선언을 변경 하 여를 `const` 필드 값을 런타임 대신 컴파일 시간에 계산 되도록 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 대체 합니다 `static` 하 고 `readonly` 한정자와 함께 `const` 한정자입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 성능이 중요 하지 않은 경우이 규칙에서 경고를 표시 하거나 규칙을 사용 하지 않도록 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 형식 `UseReadOnly`, 규칙을 위반 하는 형식이 있는 `UseConstant`, 규칙을 충족 하는 합니다.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
