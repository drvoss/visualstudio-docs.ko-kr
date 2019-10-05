---
title: 'CA1003: 제네릭 이벤트 처리기 인스턴스를 사용 하 여 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 25c96abd08f9d6c5f519c5f897c43aaf28bc231b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682269"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식에는 대리자는 void를 반환 하며 해당 시그니처에 두 개의 매개 변수 (개체가 첫 번째 및 두 번째는 EventArgs에 할당 될 수 있는 형식) 및 포함 된 어셈블리 대상을 포함 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]합니다.

## <a name="rule-description"></a>규칙 설명
 하기 전에 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], 이벤트 처리기에 사용자 지정 정보를 전달 하기 위해 새 대리자에서 파생 된 클래스를 지정 하는 선언 해야 합니다 <xref:System.EventArgs?displayProperty=fullName> 클래스입니다. 더 이상 그렇습니다 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]는 도입을 <xref:System.EventHandler%601?displayProperty=fullName> 대리자입니다. 파생 되는 모든 클래스를 사용 하는이 제네릭 대리자 <xref:System.EventArgs> 이벤트 처리기와 함께 사용할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 대리자를 제거 하 고 사용 하 여 용도 대체 합니다 <xref:System.EventHandler%601?displayProperty=fullName> 위임 합니다. 대리자가 자동 생성 하는 경우는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 컴파일러를 사용 하 여 이벤트 선언의 구문을 변경는 <xref:System.EventHandler%601?displayProperty=fullName> 대리자입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 대리자를 보여 줍니다. 에 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 예에서 설명 된 규칙을 충족 하기 위해 예제를 수정 하는 방법에 설명 합니다. C# 예제에서는 수정 된 코드를 보여 주는 예로가 따릅니다.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>예제
 다음 예제에서는 규칙을 충족 하 고 사용을 대체 하는 이전 예제에서 대리자 선언을 제거 합니다 `ClassThatRaisesEvent` 하 고 `ClassThatHandlesEvent` 메서드를 사용 하 여는 <xref:System.EventHandler%601?displayProperty=fullName> 대리자.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1005: 제네릭 형식에 매개 변수를 방지 합니다.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션에서 제네릭 인터페이스를 구현 해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 제네릭 형식에 정적 멤버를 선언 하지 마십시오](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: 제네릭 목록을 노출 하지 마십시오](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마십시오.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드 형식 매개 변수를 제공 해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: 적합 한 제네릭을 사용합니다](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>참고 항목
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
