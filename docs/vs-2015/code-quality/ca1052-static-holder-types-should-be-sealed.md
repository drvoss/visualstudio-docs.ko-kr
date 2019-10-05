---
title: 'CA1052: 정적 소유자 형식은 sealed 여야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d973d7ff5464b76228e917c83b3e62116e115718
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693795"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: 정적 소유자 형식은 sealed여야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 정적 멤버만 포함 하 고 사용 하 여 선언 되지 않은 합니다 [봉인](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) 한정자.

## <a name="rule-description"></a>규칙 설명
 이 규칙 형식에서 파생된 된 형식에서 재정의할 수 있는 모든 기능을 제공 하지 않으므로 정적 멤버만 포함 하는 형식에서 상속 하도록 설계 되지 않았습니다 하는 것으로 가정 합니다. 상속되지 않는 형식은 기본 형식으로 사용되지 않도록 `sealed` 한정자로 표시해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 형식 표시 `sealed`합니다. 대상으로 하는 경우 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 더 나은 방법으로 형식을 표시 하는 것 2.0 이전의 `static`합니다. 이런 방식으로 않아도 클래스를 만들지 않으려면 private 생성자를 선언 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식 상속 하도록 하는 경우에이 규칙에서 경고를 표시 합니다. 없는 경우는 `sealed` 한정자 제안 형식이 기본 형식으로 유용 합니다.

## <a name="example-of-a-violation"></a>위반의 예

### <a name="description"></a>설명
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

### <a name="code"></a>코드
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Static 한정자를 사용 하 여 해결

### <a name="description"></a>설명
 다음 예제에서는 사용 하 여 형식을 표시 하 여이 규칙 위반 문제를 해결 하는 방법의 `static` 한정자입니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1053: 정적 소유자 형식에는 생성자를 사용 해야 합니다.](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
