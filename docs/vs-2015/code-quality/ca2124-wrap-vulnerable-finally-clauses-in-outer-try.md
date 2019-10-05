---
title: 'CA2124: 취약 한 finally 절 외부 try에 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: de2bd0bfbf60ef717e00daaa668475cb43a9d35c
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890933"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: 취약한 finally 절을 외부 try에 래핑하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 버전 1.0 및 1.1의 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], public 또는 protected 메서드가 포함을 `try` / `catch` / `finally` 블록입니다. `finally` 보안 상태를 되돌리려면 나타나고 되지 않은 블록을 `finally` 블록입니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙을 찾습니다 `try` / `finally` 의 버전 1.0 및 1.1을 대상으로 하는 코드 블록을 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 는 호출 스택에 있는 악성 예외 필터에 노출 될 수 있습니다. 필터 전에 실행할 수 있습니다 가장 등의 중요 한 작업 try 블록에서 발생 하 고 예외가 throw 되는 `finally` 블록입니다. 가장 예를 들어 필터 가장된 된 사용자로 실행 될 수는이 의미 합니다. 필터는 현재 Visual Basic에서 구현할 수 있습니다.

> [!WARNING]
> 버전 2.0 이상에 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], 런타임에서 자동으로 보호를 `try` / `catch` /  `finally` 재설정 메서드 내에서 직접 발생 하는 경우 악의적인 예외 필터에서 차단 하는 예외 블록을 포함합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 배치는 래핑되지 않은 `try` / `finally` 외부 try 블록에 있습니다. 뒤에 오는 두 번째 예제를 참조 하세요. 이렇게 하면는 `finally` 필터 코드 보다 먼저 실행 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="pseudo-code-example"></a>의사 코드 예제

### <a name="description"></a>Description
 다음 의사 코드에서는 이 규칙에 의해 검색되는 패턴을 보여 줍니다.

### <a name="code"></a>코드

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>예제
 다음 의사 코드는 코드를 보호 하 고이 규칙을 충족 하는 데 사용할 수 있는 패턴을 보여 줍니다.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
