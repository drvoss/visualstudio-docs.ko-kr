---
title: 'CA1401: P-Invoke를 표시 해서는 안 됩니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3f867f14f7a2eca4482f1f8d5fb48149f02f43f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661365"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invoke는 노출되지 않아야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 형식의 public 또는 protected 메서드에 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 특성이 있습니다 ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 `Declare` 키워드에도 구현 됨).

## <a name="rule-description"></a>규칙 설명
 @No__t_0 특성으로 표시 된 메서드 (또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 `Declare` 키워드를 사용 하 여 정의 된 메서드)는 플랫폼 호출 서비스를 사용 하 여 비관리 코드에 액세스 합니다. 이러한 메서드는 노출되지 않아야 합니다. 이러한 메서드를 private 또는 internal로 유지 하면 호출자가 다른 방법으로 호출할 수 없는 관리 되지 않는 Api에 대 한 액세스를 허용 하 여 보안을 위반 하는 데 라이브러리를 사용할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드의 액세스 수준을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 메서드를 선언 합니다.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
