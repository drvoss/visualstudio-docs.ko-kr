---
title: 'CA2117: APTCA 형식은 APTCA 기본 형식만 확장 해야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 078b7f5535dc80261917ef662b3a2f0069cb33a8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687295"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 사용 하 여 어셈블리의 public 또는 protected 형식은 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 특성 특성이 없는 어셈블리에 선언 된 형식에서 상속 합니다.

## <a name="rule-description"></a>규칙 설명
 기본적으로 강력한 이름의 어셈블리에서 public 또는 protected 형식이 암시적으로 보호를 [상속 요청](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) 완전 신뢰에 대 한 합니다. 강력한 이름의 어셈블리는 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 특성 (APTCA)이이 보호를 권한이 없습니다. 특성 상속 요청을 해제합니다. 이렇게 하면 완전 신뢰 되지 않은 형식에서 노출 된 형식 상속 가능한 어셈블리에서 선언 합니다.

 APTCA 특성은 완전히 신뢰할 수 있는 어셈블리에 부분적으로 신뢰할 수 있는 호출자를 허용 하지 않는 형식에서 어셈블리의 형식 상속을 보안 악용 가능성이 있습니다. 두 가지 형식이 면 `T1` 하 고 `T2` 다음 조건을 충족, 악의적인 호출자가 형식을 사용할 수 `T1` 보호 하는 암시적 완전 신뢰 상속 요청을 건너뛸 수 `T2`:

- `T1` APTCA 특성을 갖는 완전 신뢰 어셈블리에서 public 형식을 선언 됩니다.

- `T1` 형식에서 상속 `T2` 어셈블리 외부에 있습니다.

- `T2`어셈블리에 APTCA 특성이 없고, 따라서 부분적으로 신뢰할 수 있는 어셈블리의 형식에서에서 상속 될 수 없습니다.

  부분적으로 신뢰할 수 있는 형식을 `X` 에서 상속할 수 있습니다 `T1`에 액세스 권한을 제공 상속 된 멤버에 선언 된 `T2`합니다. 때문에 `T2` APTCA 특성을 직접 파생된 형식 없는 (`T1`) 완전 신뢰에 대 한 상속 요청을 충족 해야 합니다 `T1` 완전 신뢰가 있고 따라서이 검사를 충족 합니다. 보안 위험을 이므로 `X` 보호 하는 상속 요구를 만족 시키는에 참여 하지 않는 `T2` 신뢰할 수 없는 하위 클래스에서. 이러한 이유로 APTCA 특성을 사용 하 여 형식 특성이 없는 형식을 확장 하지 해야 합니다.

  다른 보안 문제 및 가장 자주 하나는 파생된 형식 (`T1`)를 프로그래머 오류 보호 된 멤버 노출 완전 신뢰가 필요한 형식에서 (`T2`). 이 경우 신뢰할 수 없는 호출자는 완전히 신뢰할 수 있는 형식에만 사용할 수 있는 정보에 액세스할을 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 위반에 의해 보고 형식 APTCA 특성이 필요 하지 않은 어셈블리에 있으면 제거 합니다.

 APTCA 특성이 필요한 경우 완전 신뢰에 대 한 상속 요청 형식으로 추가 합니다. 이 신뢰할 수 없는 형식에서 상속을 보호합니다.

 위반에 의해 보고 된 기본 형식의 어셈블리에 APTCA 특성을 추가 하 여 위반 문제를 해결 하는 것이 가능 합니다. 이 첫 번째는 어셈블리의 모든 코드 및 어셈블리에 종속 된 모든 코드 집약적인 보안 검토를 수행 하지 않고 수행 하지 않습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 안전 하 게 표시 하지 않으려면는 해당 형식에서 노출 하는 보호 된 멤버 허용 하지 않습니다 직접 또는 간접적으로 신뢰할 수 없는 호출자가 중요 한 정보, 작업 또는 안전 하지 않은 방식으로 사용할 수 있는 리소스에 액세스 하도록 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙에서 검색 하는 보안 문제를 설명 하기 위해 두 명의 어셈블리 및 테스트 응용 프로그램을 사용 합니다. 첫 번째 어셈블리에 APTCA 특성 없고 부분적으로 신뢰할 수 있는 형식 상속 되지 않습니다 (나타내는 `T2` 이전 토론에서).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>예제
 두 번째 어셈블리를 나타내는 `T1` 이전 토론에서 되므로 완전히 신뢰할 수 있는 부분적으로 신뢰할 수 있는 호출자를 허용 합니다.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>예제
 나타내는 테스트 종류에 `X` 부분적으로 신뢰할 수 있는 어셈블리에는 이전 설명 합니다.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **수상한 일 감사에서 충족 2003 년 2 월 22 일 오전 12시: 00! **
**에서 테스트: sunny 목초지**
**화창한 목초지 만나고 2003 년 2 월 22 일 오전 12시: 00!**
## <a name="related-rules"></a>관련된 규칙
 [CA2116: APTCA 메서드는 APTCA 메서드만 호출 해야 합니다.](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>참고 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [코드에 부분적으로 신뢰할 수 있는.NET Framework 어셈블리에서 호출할](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [신뢰할 수 있는 코드에서 라이브러리를 사용 하 여 부분적으로](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [상속 요구](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)
