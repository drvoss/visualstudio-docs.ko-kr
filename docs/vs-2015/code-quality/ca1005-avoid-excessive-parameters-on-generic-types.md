---
title: 'CA1005: 제네릭 형식에 매개 변수를 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc2986a81b0b21b2e2a4fd87b9c5a453e7d05c32
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704303"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 표시 되는 제네릭 형식에 두 개 이상의 형식 매개 변수입니다.

## <a name="rule-description"></a>규칙 설명
 제네릭 형식에 포함된 형식 매개 변수가 많을수록 각 형식 매개 변수가 무엇을 나타내는지를 파악하거나 기억하기가 더 어렵습니다. 것 같이 하나의 형식 매개 변수를 사용 하 여 일반적으로 분명 `List<T>`, 및 에서처럼 두 형식 매개 변수를 사용 하 여 특정 사례에서 `Dictionary<TKey, TValue>`합니다. 두 개 이상의 형식 매개 변수가 하는 경우는 너무 어렵습니다 대부분의 사용자 (예를 들어 `TooManyTypeParameters<T, K, V>` C# 또는 `TooManyTypeParameters(Of T, K, V)` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 두 개의 형식 매개 변수를 사용 하는 디자인을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 디자인 두 개 이상의 형식 매개 변수를 반드시 필요한 경우가 아니라면이 규칙에서 경고를 표시 하지 마십시오. 새 라이브러리의 도입 률을 높이고 학습에 걸리는 시간이 줄어듭니다 제네릭을 이해 및 사용 하기 쉬운 구문 제공 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1010: 컬렉션에서 제네릭 인터페이스를 구현 해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 제네릭 형식에 정적 멤버를 선언 하지 마십시오](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: 제네릭 목록을 노출 하지 마십시오](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마십시오.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드 형식 매개 변수를 제공 해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용 합니다.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적합 한 제네릭을 사용합니다](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>참고 항목
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
