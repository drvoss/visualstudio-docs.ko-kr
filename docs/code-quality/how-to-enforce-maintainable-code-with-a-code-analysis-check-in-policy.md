---
title: 코드 분석 체크 인 정책을 사용 하 여
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0924d3c7b6f39e4ec026a77ee8e0418361e311ba
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260917"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>방법: 코드 분석 체크 인 정책 사용 하 여 유지 관리 가능한 코드 적용

개발자가 복잡 하 고 해당 코드의 유지 관리 용이성 측정 코드 메트릭 도구를 사용할 수 있지만 코드 메트릭 체크 인 정책의 일부로 호출할 수 없습니다. 그러나 코드 메트릭 표준 사용 하 여 코드의 호환성을 확인 하는 코드 분석 규칙을 사용 하도록 설정 하 고 체크 인 정책을 통해 규칙을 적용할 수 있습니다. 코드 메트릭에 대 한 자세한 내용은 참조 하세요. [메트릭 값을 코드](../code-quality/code-metrics-values.md)합니다.

상속 깊이, 클래스 결합, 유지 관리 인덱스 고 복잡성 규칙 코드 분석 체크 인 정책을 통해 유지 관리 가능한 코드에 적용할 수 있습니다. 이러한 규칙의 모든 네는 코드 분석 정책 편집기에서 "유지 관리 규칙" 범주에 있습니다.

Team foundation 버전 제어의 관리자는 체크 인 정책 요구 사항에 코드 분석 유지 관리 규칙을 추가할 수 있습니다. 이러한 체크 인 정책 체크 인 시작 하기 전에 이러한 규칙 변경 내용에 따라 코드 분석을 실행 하려면 개발자가 필요 합니다.

## <a name="to-open-the-code-analysis-policy-editor"></a>코드 분석 정책 편집기를 열려면

1. **팀 탐색기**프로젝트를 마우스 오른쪽 단추로 클릭, 클릭 **프로젝트 설정**를 클릭 하 고 **소스 제어**입니다.

     합니다 **소스 제어** 대화 상자가 나타납니다.

2. 에 **check-in Policy** 탭을 클릭 **추가**합니다.

     합니다 **체크 인 정책 추가** 대화 상자가 나타납니다.

3. 에 **체크 인 정책** 목록에서 합니다 **코드 분석** 확인란을 선택한 다음 클릭 **확인**합니다.

     합니다 **코드 분석 정책 편집기** 대화 상자가 나타납니다.

## <a name="to-enable-code-analysis-maintainability-rules"></a>코드 분석 유지 관리 규칙을 사용 하도록 설정 하려면

1. 에 **코드 분석 정책 편집기** 대화 상자의 **규칙 설정**를 확장 합니다 **유지 관리 규칙** 노드.

2. 다음 규칙에 대 한 확인란을 선택 합니다.

   - 상속 수준: **CA1501 AvoidExcessiveInheritance** -임계값: 5 개 수준 깊이에서 경고 발생

   - 복잡성: **CA1502 AvoidExcessiveComplexity** -임계값: 경고에서 25 개가 넘는

   - 유지 관리 인덱스: **CA1505 AvoidUnmaintainableCode** - Threshold: 20 개 미만의에서 경고 발생

   - 클래스 결합 합니다. **CA1506 AvoidExcessiveClassCoupling** -임계값: 클래스에 대해 80 개 및 30 개 이상의 메서드에 대 한 경고

     또한 성공적인 빌드를 방지 하기 위해 규칙 위반을 선택 합니다 **경고를 오류로** 규칙 설명 옆의 확인란 합니다.

3. **확인**을 클릭합니다. 새 체크 인 정책을 이제 이후의 체크 인에 적용 됩니다.

## <a name="see-also"></a>참고자료

- [코드 메트릭 값](../code-quality/code-metrics-values.md)
- [코드 분석 체크 인 정책 만들기 및 사용](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
