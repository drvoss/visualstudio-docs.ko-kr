---
title: 'CA2126: 형식 링크 요청에는 상속 요청이 필요합니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f01ba5af7640521333093e4bba1f36a95363b60
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232462"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: 형식 링크 요청에는 상속 요청이 필요합니다.

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|범주|Microsoft.Security|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
봉인 되지 않은 public 형식은 링크 요청으로 보호 되 고, 재정의 가능한 메서드를 포함 하며, 형식 또는 메서드가 상속 요청으로 보호 되지 않습니다.

## <a name="rule-description"></a>규칙 설명
메서드 또는 해당 선언 형식에 대 한 링크 요청에는 메서드에 대 한 직접 호출자가 지정 된 사용 권한을 가져야 합니다. 메서드의 상속 요청에는 재정의 메서드가 지정 된 사용 권한을 가져야 합니다. 형식에 대 한 상속 요청에는 파생 클래스가 지정 된 사용 권한을 가져야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 링크 요청과 동일한 사용 권한에 대 한 상속 요청을 사용 하 여 형식 또는 메서드를 보호 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>관련 규칙
[CA2108: 값 형식에 대 한 선언적 보안 검토](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112: 보안 형식은 필드를 노출 하면 안 됩니다.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122: 링크 요청이 있는 메서드를 간접적으로 노출 하지 마십시오.](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123: 재정의 링크 요청은 base와 동일 해야 합니다.](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>참고 항목

- [보안 코딩 지침](/dotnet/standard/security/secure-coding-guidelines)
- [링크 요청](/dotnet/framework/misc/link-demands)