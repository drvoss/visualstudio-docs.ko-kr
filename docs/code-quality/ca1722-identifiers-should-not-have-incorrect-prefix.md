---
title: 'CA1722: 식별자에는 올바른 접두사를 사용해야 합니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb41f2ad4548933d10137e7f72cae59643d33043
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233883"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: 식별자에는 올바른 접두사를 사용해야 합니다.

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|범주|Microsoft.Naming|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
식별자에 잘못 된 접두사가 있습니다.

## <a name="rule-description"></a>규칙 설명
규칙에 따라 특정 프로그래밍 요소에만 특정 접두사로 시작하는 이름을 사용할 수 있습니다.

형식 이름에는 특정 접두사가 없으며 ' C ' 접두사가 없어야 합니다. 이 규칙은 ' CMyClass '과 같은 형식 이름에 대 한 위반을 보고 하 고 ' Cache '와 같은 형식 이름에 대 한 위반을 보고 하지 않습니다.

명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이러한 일관성은 새로운 소프트웨어 라이브러리에 필요한 학습 곡선을 줄이고 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했다는 확신을 높입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
식별자에서 접두사를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="related-rules"></a>관련 규칙
[CA1715: 식별자에는 올바른 접두사가 있어야 합니다.](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)