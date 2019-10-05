---
title: 'CA2146: 형식은 최소한 기본 형식 및 인터페이스 만큼 중요 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d1a0120caf16fbed34fa87ab71fe50abc4467d51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142667"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: 형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 투명 한 형식으로 표시 된 형식에서 파생 됩니다는 <xref:System.Security.SecuritySafeCriticalAttribute> 또는 <xref:System.Security.SecurityCriticalAttribute>, 또는 형식으로 표시 되는 <xref:System.Security.SecuritySafeCriticalAttribute> 특성으로 표시 된 형식에서 파생 됩니다는 <xref:System.Security.SecurityCriticalAttribute> 특성입니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 파생 형식에 기본 형식 또는 구현된 인터페이스만큼 중요하지 않은 보안 투명성 특성이 있을 때 적용됩니다. 중요한 기본 형식에서 파생되거나 중요한 인터페이스를 구현할 수 있는 것은 중요한 형식뿐이고, 안전에 중요한 기본 형식에서 파생되거나 안전에 중요한 인터페이스를 구현할 수 있는 것은 중요하거나 안전에 중요한 형식뿐입니다. 수준 2 투명도에이 규칙의 위반 발생을 <xref:System.TypeLoadException> 파생된 형식에 대 한 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 위반을 해결 하려면 최소한 기본 형식 또는 인터페이스 만큼 중요 투명도 특성을 사용 하 여 구현 또는 파생 형식을 표시 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
