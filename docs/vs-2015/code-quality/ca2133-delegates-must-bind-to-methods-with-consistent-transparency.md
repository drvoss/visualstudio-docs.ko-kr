---
title: 'CA2133: 대리자는 투명도 일관 된 메서드에 바인딩해야 합니다 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a8a19a84336cc6452f663eb65429326b52268728
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386948"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: 대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

> [!NOTE]
> 이 경고는 CoreCLR (Silverlight 웹 응용 프로그램에 관련 된 CLR의 버전)를 실행 하는 코드에만 적용 됩니다.

## <a name="cause"></a>원인
 이 경고로 표시 된 대리자를 바인딩하는 메서드에서 발생 합니다 <xref:System.Security.SecurityCriticalAttribute> 사용 하 여 표시 되거나 투명 한 메서드에 <xref:System.Security.SecuritySafeCriticalAttribute>합니다. 또한 투명하거나 안전에 중요한 대리자를 중요한 메서드에 바인딩하는 메서드에서도 이 경고가 발생합니다.

## <a name="rule-description"></a>규칙 설명
 대리자 형식과 메서드를 바인딩할 때를 일관 된 투명도 있어야 합니다. 투명 하 고 안전에 중요 한 대리자는 다른 투명 하거나 안전에 중요 한 방법만 바인딩할 수 있습니다. 마찬가지로, 중요 한 메서드에 중요 한 대리자만 바인딩할 수 있습니다. 이러한 바인딩 규칙은 대리자를 통해 메서드를 호출할 수 있는 코드만 호출할 수 동일한 방법을 직접 확인 합니다. 예를 들어 바인딩 규칙 투명 한 대리자를 통해 직접 critical 코드 호출에서 투명 한 코드를 방지 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 경고에 대 한 위반이 해결 하려면 두 투명도 해당 하는 것에 바인딩하는 메서드 또는 대리자의 투명도 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
