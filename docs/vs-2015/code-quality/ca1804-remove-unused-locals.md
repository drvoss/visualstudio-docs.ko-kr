---
title: 'CA1804: 사용 되지 않는 로컬 항목을 제거 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38fe76bbdf2fdafa69ca12caf4f131a05f783954
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143124"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: 사용되지 않는 로컬 항목을 제거하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 지역 변수를 선언 하지만 사용 하지 않습니다 제외 하 고 변수의 가능한 대입문의 받는 사람으로 합니다. 이 규칙에 따라 분석에 대 한 디버깅 정보로 테스트 되는 어셈블리를 빌드해야 하 고 연결된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
 사용되지 않는 지역 변수와 불필요한 할당으로 어셈블리의 크기가 증가하고 성능이 저하될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 제거 하거나 지역 변수를 사용 합니다. C# 컴파일러 되는 포함 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 사용 되지 않는 로컬 변수를 제거 때는 `optimize` 옵션을 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 컴파일러는 변수를 내보낸 경우이 규칙에서 경고를 표시 합니다. 또한 성능 및 코드 유지 관리 주요 관심사 없는 경우에이 규칙에서 경고를 표시 하거나 규칙을 사용 하지 않으려면 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 몇 가지 사용 되지 않는 로컬 변수를 보여 줍니다.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1809: 과도 한 지역 변수를 방지 합니다.](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: 호출 되지 않는 전용 코드를 방지 합니다.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: 인스턴스화되지 않은 내부 클래스를 방지 합니다.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: 사용 되지 않는 매개 변수를 검토](../code-quality/ca1801-review-unused-parameters.md)
