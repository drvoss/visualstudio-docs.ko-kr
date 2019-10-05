---
title: 'CA2111: 포인터는 노출 되는 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8497433088e4c49868a76dd3281d02a5e79babe5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154374"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: 포인터는 노출되면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 public 또는 protected <xref:System.IntPtr?displayProperty=fullName> 또는 <xref:System.UIntPtr?displayProperty=fullName> 필드는 읽기 전용입니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.IntPtr> 및 <xref:System.UIntPtr> 관리 되지 않는 메모리에 액세스 하는 데 사용 되는 포인터 형식이 있습니다. 에 대 한 포인터를 없는 경우 private, internal 또는 읽기 전용 악성 코드가 잠재적 메모리 내 임의의 위치에 대 한 액세스를 허용 하거나 응용 프로그램 또는 시스템 오류를 일으키는 포인터의 값을 변경할 수 있습니다.

 참조 포인터 필드를 포함 하는 형식에 대 한 보안 액세스 하려는 경우 [CA2112: 보안된 형식은 필드를 노출 해야](../code-quality/ca2112-secured-types-should-not-expose-fields.md)합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 읽기 전용, internal 또는 private 있도록 하 여 포인터를 보호 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 포인터의 값에 의존 하지 않는 경우이 규칙에서 경고를 표시 합니다.

## <a name="example"></a>예제
 다음 코드를 위반 하 고 규칙을 충족 하는 포인터를 보여 줍니다. Private이 아닌 포인터도 규칙을 위반 하는 알림 [CA1051: 표시 되는 인스턴스 필드를 선언 하지 마십시오](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)합니다.

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2112: 보안된 형식은 필드를 노출 해야](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: 표시 되는 인스턴스 필드 선언 하지 마십시오.](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>관련 항목
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
