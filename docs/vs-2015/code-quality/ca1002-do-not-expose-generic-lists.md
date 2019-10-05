---
title: 'CA1002: 제네릭 목록을 노출 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2d1b4f67f25db7c0006decc5fc26696c6c5dad01
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685347"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: 제네릭 목록을 노출하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식을 포함 하는 외부에 표시 되는 멤버를 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 형식으로 반환을 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 형식 또는 시그니처를 가진 포함를 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 매개 변수입니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 성능 및 상속이 아니라 하도록 디자인 된 제네릭 컬렉션이입니다. <xref:System.Collections.Generic.List%601?displayProperty=fullName> 쉽게 상속된 된 클래스의 동작을 변경 하는 가상 멤버를 포함 하지 않습니다. 다음 제네릭 컬렉션을 상속 하도록 설계 되었으며 대신 노출 되어야 합니다 <xref:System.Collections.Generic.List%601?displayProperty=fullName>합니다.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 변경 된 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 형식 상속을 위해 디자인 된 제네릭 컬렉션 중 하나입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 경고를 발생 시킨 어셈블리는 재사용 가능한 라이브러리 하려고 하지 않는 한이 규칙에서 경고를 표시 하지 마십시오. 예를 들어 것 성능 조정 된 응용 프로그램에서이 경고를 표시 하지 않아도 안전 제네릭 목록 사용 하 여에서 성능상의 이점을 얻은 위치.

## <a name="related-rules"></a>관련된 규칙
 [CA1005: 제네릭 형식에 매개 변수를 방지 합니다.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션에서 제네릭 인터페이스를 구현 해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 제네릭 형식에 정적 멤버를 선언 하지 마십시오](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마십시오.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드 형식 매개 변수를 제공 해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용 합니다.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적합 한 제네릭을 사용합니다](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>참고 항목
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
