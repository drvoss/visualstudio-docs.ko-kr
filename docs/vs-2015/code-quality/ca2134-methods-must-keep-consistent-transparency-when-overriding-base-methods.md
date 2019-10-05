---
title: 'CA2134: 메서드는 기본 메서드를 재정의할 때 일관 된 투명도 유지 해야 합니다 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2ccfe43fc110622c70802d2108b6ba5ff7ecb1b3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700377"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: 메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 메서드를 사용 하 여 표시 하는 경우이 규칙이 실행 합니다 <xref:System.Security.SecurityCriticalAttribute> 사용 하 여 표시 되거나 투명 한 메서드를 재정의 합니다 <xref:System.Security.SecuritySafeCriticalAttribute>합니다. 규칙 메서드를 사용 하 여 표시 되거나 투명 한 경우에 발생 합니다 <xref:System.Security.SecuritySafeCriticalAttribute> 로 표시 된 메서드를 재정의 한 <xref:System.Security.SecurityCriticalAttribute>합니다.

 이 규칙은 가상 메서드를 재정의하거나 인터페이스를 구현할 때 적용됩니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙의 상속 체인 메서드 보안 접근성을 변경 하려는 시도가 있을 때 발생 합니다. 예를 들어, 기본 클래스의 가상 메서드를 투명 하거나 안전에 중요 한 경우 다음 파생된 클래스가 재정의 해야 합니다 투명 하거나 안전에 중요 한 메서드를 사용 하 여 합니다. 반대로, 보안에 중요 한 가상 인 경우 파생된 클래스가 재정의 해야 합니다 보안 중요 메서드를 사용 하 여 합니다. 인터페이스 메서드를 구현 하는 것에 대 한 동일한 규칙이 적용 됩니다.

 투명도 규칙에는 코드는 대신 런타임에 컴파일된 JIT 이므로 투명도 계산은 동적 형식 정보가 없는 경우 적용 됩니다. 따라서 투명도 계산의 결과 JIT 컴파일되, 동적 형식에 관계 없이 정적 형식에서 전적으로 결정 될 수 있어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 가상 메서드를 재정의 하거나 인터페이스 메서드를 가상의 투명도 일치 하는 인터페이스를 구현 메서드의 투명도 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 표시 하지 마십시오. 이 규칙을 위반 하면 런타임 <xref:System.TypeLoadException> 수준 2 투명도 사용 하는 어셈블리에 대 한 합니다.

## <a name="examples"></a>예제

### <a name="code"></a>코드
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>참고 항목
 [보안 투명 코드, 수준 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
