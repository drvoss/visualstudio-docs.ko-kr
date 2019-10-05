---
title: 'CA2141: 투명 한 메서드 LinkDemands를 충족 해서는 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7c54b472e91aa2be1d8e5bb1a9c32c26c0cb299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142700"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: 투명한 메서드는 LinkDemands를 충족해서는 안 됩니다
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 로 표시 되지 않은 어셈블리의 메서드를 호출 하는 보안 투명 메서드가 합니다 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 특성 또는 보안 투명 메서드가 충족을 <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` 형식 또는 메서드에 대 한 합니다.

## <a name="rule-description"></a>규칙 설명
 LinkDemand를 충족 하는 것은 보안 중요 한 작업 의도 하지 않은 권한 상승이 발생할 수 있습니다. 보안 투명 코드 보안상 중요 한 코드와 같은 보안 감사 요구 사항이 적용 되지 않으므로 LinkDemands를 충족 하지 해야 합니다. 보안 규칙 집합 수준 1 어셈블리의 투명 한 메서드는 런타임에 성능 문제를 일으킬 수 있는 전체 요청을 변환할 수를 충족 하는 모든 LinkDemands를 발생 합니다. 보안 규칙 집합 수준 2 어셈블리에서 투명 한 메서드는 LinkDemand를 충족 하려고 하면 적시에 (JIT) 컴파일러에 컴파일할 수 없게 됩니다.

 어셈블리는 usee 수준 2 보안, 보안 투명 메서드가 충족 시키거나-APTCA 어셈블리의 메서드를 호출 하는 시도 발생 시킵니다는 <xref:System.MethodAccessException>; 수준 1 어셈블리의 LinkDemand 전체 요청이 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 액세스 메서드를 표시 합니다 <xref:System.Security.SecurityCriticalAttribute> 또는 <xref:System.Security.SecuritySafeCriticalAttribute> 특성 또는 액세스 메서드에서 LinkDemand를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 이 예제에서는 투명 메서드는 LinkDemand를 가진 메서드를 호출 하려고 합니다. 이 규칙은이 코드에서 발생 합니다.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
