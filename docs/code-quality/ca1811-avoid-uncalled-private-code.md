---
title: 'CA1811: 호출되지 않는 전용 코드를 사용하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a7542499eceeccbd62ce327b386dc099b726b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233616"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: 호출되지 않는 전용 코드를 사용하지 마세요.

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|범주|Microsoft.Performance|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
Private 또는 internal (어셈블리 수준) 멤버는 어셈블리에 호출자가 없으며 공용 언어 런타임에 의해 호출 되지 않으며 대리자에 의해 호출 되지 않습니다. 다음 멤버는이 규칙에 의해 확인 되지 않습니다.

- 명시적 인터페이스 멤버입니다.

- 정적 생성자.

- Serialization 생성자.

- <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 또는<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>로 표시 된 메서드

- 재정의 하는 멤버입니다.

## <a name="rule-description"></a>규칙 설명
이 규칙은 현재 규칙 논리에 의해 식별 되지 않는 진입점이 발생 하는 경우 가양성을 보고할 수 있습니다. 또한 컴파일러는 호출 가능 하지 않은 코드를 어셈블리로 내보낼 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 호출 가능 하지 않은 코드를 제거 하거나 호출 하는 코드를 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙
[CA1812: 인스턴스화되지 않은 내부 클래스를 사용 하지 마십시오.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: 사용 하지 않는 매개 변수 검토](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: 사용 하지 않는 지역 제거](../code-quality/ca1804-remove-unused-locals.md)