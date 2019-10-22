---
title: 'CA1802: 필요한 경우 리터럴을 사용 합니다. Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bbcf83772a7a4031cf2e27abe7e8f4c08e21c11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671521"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: 가능하면 리터럴을 사용하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|범주|Microsoft 성능|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 필드는 `static` 및 `readonly` `ReadOnly` `Shared` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)])로 선언 되 고 컴파일 타임에 계산할 수 값으로 초기화 됩니다.

## <a name="rule-description"></a>규칙 설명
 선언 형식에 대 한 정적 생성자가 호출 될 때 `static``readonly` 필드의 값은 런타임에 계산 됩니다. 선언 될 때 `static``readonly` 필드가 초기화 되 고 정적 생성자가 명시적으로 선언 되지 않은 경우 컴파일러는 정적 생성자를 내보내 필드를 초기화 합니다.

 @No__t_0 필드의 값은 컴파일 시간에 계산 되 고 메타 데이터에 저장 되므로 `static``readonly` 필드와 비교할 때 런타임 성능이 향상 됩니다.

 대상 필드에 할당 된 값은 컴파일 시간에 계산할 수 때문에 런타임이 아닌 컴파일 시간에 값이 계산 되도록 선언을 `const` 필드로 변경 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 `static` 및 `readonly` 한정자를 `const` 한정자로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 성능이 중요 하지 않은 경우이 규칙에서 경고를 표시 하지 않거나 규칙을 사용 하지 않도록 설정 하는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식 `UseReadOnly`와 규칙을 충족 하는 형식 `UseConstant`를 보여 줍니다.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
