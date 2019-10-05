---
title: 유지 관리 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752a637ef01c33aa4e93083e9578d01f00977960
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976160"
---
# <a name="maintainability-warnings"></a>유지 관리 경고

유지 관리 경고 라이브러리 및 응용 프로그램 유지 관리를 지원 합니다.

## <a name="in-this-section"></a>단원 내용

| 규칙 | 설명 |
|-----------|-----------------------------------|
| [CA1500: 변수 이름은 필드 이름과 일치 하지는](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | 인스턴스 메서드는 매개 변수 또는 이름이 오류는 선언 형식의 인스턴스 필드와 지역 변수를 선언 합니다. |
| [CA1501: 과도 한 상속을 방지](../code-quality/ca1501-avoid-excessive-inheritance.md) | 형식이 상속 계층 구조에서 네 단계보다 아래에 있습니다. 여러 번 중첩된 형식 계층 구조는 추적하고, 이해하고, 유지 관리하기가 어렵습니다. |
| [CA1502: 과도 한 복잡성을 방지 합니다.](../code-quality/ca1502-avoid-excessive-complexity.md) | 이 규칙은 메서드를 통과하는 선형 독립 경로의 수를 측정하며 조건부 분기의 수와 복잡성에 의해 결정됩니다. |
| [CA1504: 잘못 된 필드 이름을 검토 하십시오.](../code-quality/ca1504-review-misleading-field-names.md) | 인스턴스 필드의 이름이 정적의 이름 또는 "s_"로 시작 (공유 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 필드 "m_"로 시작 합니다. |
| [CA1505: 유지 관리할 수 없는 코드를 방지 합니다.](../code-quality/ca1505-avoid-unmaintainable-code.md) | 형식 또는 메서드에 낮은 유지 관리 인덱스 값이 있습니다. 낮은 유지 관리 인덱스는 형식 또는 메서드가 유지 관리하기 어렵고 다시 디자인될 수 있음을 나타냅니다. |
| [CA1506: 클래스 결합을 방지](../code-quality/ca1506-avoid-excessive-class-coupling.md) | 이 규칙은 형식 또는 메서드에 들어 있는 고유한 형식 참조의 개수를 계산하여 클래스 결합을 측정합니다. |
| [CA1507: 문자열 대신 nameof를 사용 합니다.](../code-quality/ca1507.md) | 리터럴 문자열을 인수로 사용 위치를 `nameof` 식을 사용할 수 있습니다. |

## <a name="see-also"></a>참고자료

- [복잡성과 관리 되는 코드의 관리 용이성 측정](../code-quality/code-metrics-values.md)