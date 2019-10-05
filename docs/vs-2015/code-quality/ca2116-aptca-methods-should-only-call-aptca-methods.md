---
title: 'CA2116: APTCA 메서드는 APTCA 메서드만 호출 해야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ac5877ecf22ca8d0d8cc15095d354973ece29eaa
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687350"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA 메서드는 APTCA 메서드만 호출해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 사용 하 여 어셈블리의 메서드는 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 특성 특성이 없는 어셈블리에서 메서드를 호출 합니다.

## <a name="rule-description"></a>규칙 설명
 기본적으로 강력한 이름의 어셈블리에서 public 또는 protected 메서드는 암시적으로 보호 된 여는 [링크 요구가](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) 완전 신뢰에만 완전히 신뢰할 수 있는 호출자에 게는 강력한 이름의 어셈블리에 액세스할 수 있습니다. 강력한 이름의 어셈블리는 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 특성 (APTCA)이이 보호를 권한이 없습니다. 특성 사용 어셈블리와 같은 인터넷 또는 인트라넷에서 실행 되는 코드가 완전히 신뢰 되지 않은 호출자에 게 액세스할 수 있게 하는 링크 요청 하지 않도록 설정 합니다.

 APTCA 특성은 완전히 신뢰할 수 있는 어셈블리에 부분적으로 신뢰할 수 있는 호출자를 허용 하지 않는 다른 어셈블리의 코드를 실행 하는 경우 보안상 위험할 가능성이 있습니다. 경우 두 가지 방법 `M1` 하 고 `M2` 다음 조건을 충족, 악의적인 호출자는 메서드를 사용할 수 있습니다 `M1` 보호 하는 완전 신뢰 암시적 링크 요청을 무시 하도록 `M2`:

- `M1` 공용 메서드는 APTCA 특성이 있는 완전 신뢰 어셈블리에 선언 됩니다.

- `M1` 메서드를 호출 `M2` 외부 `M1`의 어셈블리입니다.

- `M2`어셈블리에 APTCA 특성이 없고, 따라서 실행 하지 않아야 하거나 부분적으로 신뢰할 수 있는 호출자를 대신 하 여 합니다.

  부분적으로 신뢰할 수 있는 호출자 `X` 메서드를 호출할 수 있습니다 `M1`발생 `M1` 호출할 `M2`합니다. 때문에 `M2` APTCA 특성을 직접 호출자 없는 (`M1`) 완전 신뢰에 대 한 링크 요청을 충족 해야 합니다 `M1` 완전 신뢰가 있고 따라서이 검사를 충족 합니다. 보안 위험을 이므로 `X` 만족 보호 하는 링크 요청에 참여 하지 않는 `M2` 신뢰할 수 없는 호출자에서. 따라서 메서드는 APTCA 특성으로 메서드를 호출 해서는 특성이 없는 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 APCTA 특성이 필요한 경우 완전 신뢰 어셈블리를 호출 하는 메서드를 보호 하기 위해 요청을 사용 합니다. 정확한 권한을 요구에 메서드로 노출 하는 기능에 따라 달라 집니다. 가능한 경우 기본 기능을 부분적으로 신뢰할 수 있는 호출자에 게 노출 되지 않도록 하려면 완전 신뢰에 대 한 요청을 사용 하 여 메서드를 보호 합니다. 없는 경우에 노출 된 기능을 효과적으로 보호 하는 사용 권한 집합을 선택 합니다. 요청에 대 한 자세한 내용은 참조 하세요. [수요](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 안전 하 게 표시 하지 않으려면 메서드에서 노출 하는 기능을 허용 하지 않도록 직접 또는 간접적으로 호출자가 중요 한 정보, 작업 또는 안전 하지 않은 방식으로 사용할 수 있는 리소스에 액세스 하도록 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙에서 검색 하는 보안 문제를 설명 하기 위해 두 명의 어셈블리 및 테스트 응용 프로그램을 사용 합니다. 첫 번째 어셈블리에 APTCA 특성 없고 부분적으로 신뢰할 수 있는 호출자에 게 액세스할 수 없습니다 (나타내는 `M2` 이전 토론에서).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>예제
 두 번째 어셈블리를 완전히 신뢰할 수 있는 하 여 부분적으로 신뢰할 수 있는 호출자 허용 (나타내는 `M1` 이전 토론에서).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>예제
 테스트 응용 프로그램 (나타내는 `X` 이전 토론에서) 부분적으로 신뢰할 수 있습니다.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **전체 신뢰: 요청에 대 한 요청에 실패 했습니다.** 
**ClassRequiringFullTrust.DoWork 호출 되었습니다.**
## <a name="related-rules"></a>관련된 규칙
 [CA2117: APTCA 형식은 APTCA 기본 형식만 확장 해야](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>참고 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [코드에 부분적으로 신뢰할 수 있는.NET Framework 어셈블리에서 호출할](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [신뢰할 수 있는 코드에서 라이브러리를 사용 하 여 부분적으로](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [요구](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
