---
title: 'CA2141: 투명한 메서드는 LinkDemands를 충족해서는 안 됩니다'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0365d82917b8cfbaf291d557a6ac2d95c220562a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232125"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: 투명한 메서드는 LinkDemands를 충족해서는 안 됩니다

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|범주|Microsoft.Security|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
보안 투명 메서드가 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 특성으로 표시 되지 않은 어셈블리의 메서드를 호출 하거나, 보안 투명 메서드가 형식 또는 메서드에 대 한를 <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` 충족 합니다.

## <a name="rule-description"></a>규칙 설명
LinkDemand를 만족 시키는 것은 의도 하지 않은 권한 상승을 일으킬 수 있는 보안 관련 작업입니다. 보안 투명 코드는 보안에 중요 한 코드와 같은 보안 감사 요구 사항이 적용 되지 않으므로 LinkDemands를 충족 해서는 안 됩니다. 보안 규칙 집합 수준 1 어셈블리의 투명 한 메서드는 런타임에 만족 하는 모든 LinkDemands가 전체 요청으로 변환 되어 성능 문제가 발생할 수 있습니다. 보안 규칙 집합 수준 2 어셈블리에서는 LinkDemand를 충족 하려고 할 때 투명 메서드가 JIT (just-in-time) 컴파일러에서 컴파일되지 않습니다.

수준 2 보안을 사용 하는 어셈블리에서 보안 투명 메서드가 LinkDemand를 충족 하거나 비 APTCA 어셈블리의 메서드를 호출 하려고 하면 <xref:System.MethodAccessException>이 발생 합니다. 수준 1 어셈블리에서는 LinkDemand가 전체 요청이 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 액세스 방법을 <xref:System.Security.SecurityCriticalAttribute> 또는 <xref:System.Security.SecuritySafeCriticalAttribute> 특성으로 표시 하거나 액세스 된 메서드에서 LinkDemand를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
이 예제에서 투명 메서드는 LinkDemand가 있는 메서드를 호출 하려고 합니다. 이 규칙은이 코드에서 발생 합니다.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]