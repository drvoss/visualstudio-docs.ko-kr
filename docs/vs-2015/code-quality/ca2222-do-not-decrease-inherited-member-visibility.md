---
title: 'CA2222: 상속 된 멤버 표시 유형 수준을 낮추지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee6228359e84687023a713ee866ebfbb760b206b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142453"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: 상속된 멤버 노출 수준을 낮추지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 봉인 되지 않은 형식에서 private 메서드는 기본 형식에서 선언 된 공용 메서드에 동일한 시그니처가 있습니다. Private 메서드 최종 아닙니다.

## <a name="rule-description"></a>규칙 설명
 상속된 멤버에 대한 액세스 한정자는 변경하면 안 됩니다. 상속된 멤버를 private으로 변경하더라도 호출자가 메서드의 기본 클래스 구현에 액세스하는 것을 막을 수 없습니다. 멤버를 전용으로 전환 하는 경우 형식을 봉인 되지 않은 상속 형식이 상속 계층 구조에서 메서드의 마지막 공용 구현을 호출할 수 있습니다. 액세스 한정자를 변경 해야 하는 경우 해당 메서드를 마지막으로 표시 또는 메서드를 재정의 하지 않도록 하려면 해당 형식이 sealed 여야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 private이 아닌 수에 대 한 액세스를 변경 합니다. 또는 프로그래밍 언어를 지 원하는 경우 가능 메서드를 최종 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
