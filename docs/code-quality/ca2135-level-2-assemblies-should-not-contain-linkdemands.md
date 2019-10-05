---
title: 'CA2135: 수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66b9e7cb0eba06b00b30c2b7d00fac78206d222f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232239"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: 수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|범주|Microsoft.Security|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
클래스 또는 클래스 멤버가 수준 2 보안을 <xref:System.Security.Permissions.SecurityAction> 사용 하는 응용 프로그램에서를 사용 하 고 있습니다.

## <a name="rule-description"></a>규칙 설명
LinkDemands는 수준 2 보안 규칙 집합에서 사용되지 않습니다. JIT (just-in-time) 컴파일 시 보안을 적용 하는 데 LinkDemands를 사용 하는 대신 <xref:System.Security.SecurityCriticalAttribute> 특성을 사용 하 여 메서드, 형식 및 필드를 표시 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면을 제거 <xref:System.Security.Permissions.SecurityAction> 하 고 <xref:System.Security.SecurityCriticalAttribute> 특성을 사용 하 여 형식 또는 멤버를 표시 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
다음 예제 <xref:System.Security.Permissions.SecurityAction> 에서는를 제거 하 고 메서드를 <xref:System.Security.SecurityCriticalAttribute> 특성으로 표시 해야 합니다.

[!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]