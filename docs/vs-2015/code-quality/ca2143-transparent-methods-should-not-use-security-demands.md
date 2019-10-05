---
title: 'CA2143: 투명 한 메서드는 보안 요청을 사용 하지 않아야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f9983f832c8793140f79e9b835e26e44fae1927
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142674"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: 투명 메서드는 보안 요청을 사용할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 투명 형식 또는 메서드를 사용 하 여 선언적으로 표시를 <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` 수요 또는 메서드 호출을 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> 메서드.

## <a name="rule-description"></a>규칙 설명
 보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다. 보안 투명 코드는 보안에 중요한 결정을 내리는 데 전체 요청을 사용해야 하며 안전에 중요한 코드는 전체 요청을 위해 투명 코드를 사용해서는 안 됩니다. 보안 요구와 같은 보안 검사를 수행 하는 모든 코드는 대신 안전에 중요 한 이어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 일반적으로이 규칙 위반 문제를 해결 하려면 사용 하 여 메서드를 표시 합니다 <xref:System.Security.SecuritySafeCriticalAttribute> 특성입니다. 또한 요청을 제거할 수 있습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 투명 메서드는 선언적 보안 요청을 수행 하기 때문에 다음 코드에서 규칙 파일입니다.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>참고 항목
 [CA2142: 투명 코드는 LinkDemands를 사용 하 여 보호 해서는 안](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
