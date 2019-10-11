---
title: 'CA1707: 식별자에는 밑줄을 사용할 수 없습니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252576"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: 식별자에는 밑줄을 사용할 수 없습니다.

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|범주|Microsoft.Naming|
|주요 변경 내용|중단-어셈블리에서 발생 하는 경우<br /><br /> 중단-형식 매개 변수에 대해 발생 하는 경우|

## <a name="cause"></a>원인

식별자 이름에는 밑줄 (\_) 문자가 포함 됩니다.

## <a name="rule-description"></a>규칙 설명

규칙에 따라 식별자 이름에 밑줄 (\_) 문자가 포함 되지 않습니다. 규칙은 네임 스페이스, 형식, 멤버 및 매개 변수를 확인 합니다.

명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이름에서 밑줄 문자를 모두 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

프로덕션 코드에 대 한 경고를 표시 하지 않습니다. 그러나 테스트 코드에 대해이 경고를 표시 하지 않는 것이 안전 합니다. [심각도](use-roslyn-analyzers.md#rule-severity) 를 **none**으로 설정 하 여이 규칙에서 경고를 표시 하지 않을 수 있습니다. 

## <a name="related-rules"></a>관련 규칙

- [CA1709: 식별자의 대/소문자를 올바르게 지정 해야 합니다. @ no__t-0
- [CA1708: 식별자는 case @ no__t-0과 달라 야 합니다.
