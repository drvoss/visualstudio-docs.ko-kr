---
title: 'CA2142: 투명 코드는 LinkDemands를 사용 하 여 보호 해서는 안 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 11bd1668e4ab599461d3619c63cd3c9732a05b4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142686"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: 투명 코드는 LinkDemands로 보호될 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 투명 한 메서드를 사용 하려면를 <xref:System.Security.Permissions.SecurityAction> 또는 다른 보안 요청 합니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 액세스하는 데 LinkDemands가 필요한 투명한 메서드에 적용됩니다. 보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다. 투명 한 메서드는 보안 중립 할 때문에 이러한 내려서는 안 보안 의사 결정 합니다. 또한가 이전에 이러한 결정을 위해 투명 코드에서 하지 않습니다 보안 결정을 안전 하 게 중요 한 코드를 신뢰 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 투명 메서드에 링크 요청을 제거 하거나 메서드를 사용 하 여 표시 <xref:System.Security.SecuritySafeCriticalAttribute> 보안 요구 사항 등을 보안 수행 하는 경우 특성을 검사 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서에서 규칙이 실행 메서드는 메서드가 이루어집니다 LinkDemand 표시 되어 있기 때문에 <xref:System.Security.PermissionSet> 를 포함 하는 <xref:System.Security.Permissions.SecurityAction>합니다.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 이 규칙에서는 경고를 표시해야 합니다.
