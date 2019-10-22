---
title: 'CA2135: 수준 2 어셈블리는 LinkDemands를 포함 하지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1248ac41a757ba2fc26ef0659c0f93ee325bc605
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602939"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: 수준 2 어셈블리는 LinkDemands를 포함해서는 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 클래스 또는 클래스 멤버가 수준 2 보안을 사용 하는 응용 프로그램에서 <xref:System.Security.Permissions.SecurityAction>를 사용 하 고 있습니다.

## <a name="rule-description"></a>규칙 설명
 LinkDemands는 수준 2 보안 규칙 집합에서 사용되지 않습니다. JIT (just-in-time) 컴파일 시 보안을 적용 하는 데 LinkDemands를 사용 하는 대신 메서드, 형식 및 필드를 <xref:System.Security.SecurityCriticalAttribute> 특성으로 표시 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Security.Permissions.SecurityAction>를 제거 하 고 형식 또는 멤버를 <xref:System.Security.SecurityCriticalAttribute> 특성으로 표시 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 <xref:System.Security.Permissions.SecurityAction>를 제거 하 고 메서드를 <xref:System.Security.SecurityCriticalAttribute> 특성으로 표시 해야 합니다.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
