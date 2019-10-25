---
title: 'CA2234: 문자열 대신 System.uri 개체를 전달 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6ad30048f9f7e30d47545435db49d2d1d7e66ff6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662798"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: 문자열 대신 System.Uri 개체를 전달하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 이름에 "uri", "Uri", "urn", "Urn", "url" 또는 "Url"이 포함 된 문자열 매개 변수가 있는 메서드에 대 한 호출을 수행 합니다. 메서드의 선언 형식에는 <xref:System.Uri?displayProperty=fullName> 매개 변수를 포함 하는 해당 메서드 오버 로드가 포함 됩니다.

## <a name="rule-description"></a>규칙 설명
 매개 변수 이름은 카멜식 대/소문자 규칙을 기반으로 하는 토큰으로 분할 된 다음 각 토큰을 검사 하 여 "uri", "Uri", "urn", "Urn", "url" 또는 "Url"과 일치 하는지 여부를 확인 합니다. 일치 하는 항목이 있는 경우 매개 변수는 URI (uniform resource identifier)를 나타내는 것으로 간주 됩니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. @No__t_0 클래스는 안전 하 고 안전한 방식으로 이러한 서비스를 제공 합니다. URI 표시와 관련 하 여 서로 다른 두 오버 로드 중에서 선택 하는 경우 사용자는 <xref:System.Uri> 인수를 사용 하는 오버 로드를 선택 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Uri> 인수를 사용 하는 오버 로드를 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 문자열 매개 변수가 URI를 나타내지 않는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 <xref:System.Uri> 오버 로드를 올바르게 호출 하는 메서드, `SaferWay` 규칙을 위반 하는 `ErrorProne` 메서드를 보여 줍니다.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1057: 문자열 URI 오버 로드는 System.uri 오버 로드를 호출 ](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: URI 속성은 문자열이 면 안 됩니다 ](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI 매개 변수는 문자열이 면 안 됩니다 ](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI 반환 값은 문자열이 면 안 됩니다 ](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
