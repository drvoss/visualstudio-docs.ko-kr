---
title: 'CA1804: 사용되지 않는 로컬 항목을 제거하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0a83d0afffc50c7697fad98c4dc49e31770d63d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233743"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: 사용되지 않는 로컬 항목을 제거하세요.

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|범주|Microsoft.Performance|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
메서드는 지역 변수를 선언 하지만 대입문을 받는 사람이 될 수 있다는 점을 제외 하 고는 변수를 사용 하지 않습니다. 이 규칙에의 한 분석을 위해 테스트 된 어셈블리는 디버깅 정보로 빌드해야 하며 연결 된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
사용되지 않는 지역 변수와 불필요한 할당으로 어셈블리의 크기가 증가하고 성능이 저하될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 지역 변수를 제거 하거나 사용 합니다.

> [!NOTE]
> 옵션 C# 을 사용 하 `optimize` 는 경우 컴파일러는 사용 되지 않는 지역 변수를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
변수가 컴파일러에서 발생 한 경우이 규칙에서 경고를 표시 하지 않습니다. 또한이 규칙에서 경고를 표시 하지 않거나 성능 및 코드 유지 관리가 주요 관심사가 아닐 경우 규칙을 사용 하지 않도록 설정 하는 것이 안전 합니다.

## <a name="example"></a>예제
다음 예제에서는 사용 되지 않는 여러 지역 변수를 보여 줍니다.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>관련 규칙
[CA1809: 과도 한 지역 방지](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: 호출 되지 않는 private 코드 방지](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: 인스턴스화되지 않은 내부 클래스를 사용 하지 마십시오.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: 사용 하지 않는 매개 변수 검토](../code-quality/ca1801-review-unused-parameters.md)