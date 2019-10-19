---
title: 'CA1027: 열거형을 FlagsAttribute로 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6f2dc7dcd79fbcaf47a2db3cf49f22f3467a06ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661927"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: 열거형을 FlagsAttribute로 표시하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 Public 열거형의 값이 2의 거듭제곱 이거나 열거형에 정의 된 다른 값의 조합이 며 <xref:System.FlagsAttribute?displayProperty=fullName> 특성이 없는 경우 가양성을 줄이기 위해이 규칙은 연속 값을 포함 하는 열거에 대 한 위반을 보고 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 명명 된 상수를 의미 있게 결합할 수 있는 경우 열거형에 <xref:System.FlagsAttribute>을 적용 합니다. 예를 들어 응용 프로그램에서 요일에 사용할 수 있는 리소스를 추적 하는 요일을 열거 하는 것이 좋습니다. @No__t_0 있는 열거를 사용 하 여 각 리소스의 가용성을 인코딩한 경우 일의 조합을 나타낼 수 있습니다. 특성이 없으면 요일을 한 개만 표현할 수 있습니다.

 결합 가능한 열거형을 저장 하는 필드의 경우 개별 열거형 값은 필드의 비트 그룹으로 처리 됩니다. 따라서 이러한 필드를 *비트 필드*라고도 합니다. 비트 필드의 저장소에 대 한 열거 값을 결합 하려면 부울 조건부 연산자를 사용 합니다. 비트 필드를 테스트 하 여 특정 열거형 값이 있는지 여부를 확인 하려면 부울 논리 연산자를 사용 합니다. 비트 필드가 결합 된 열거형 값을 올바르게 저장 하 고 검색 하려면 열거형에 정의 된 각 값이 2의 거듭제곱 이어야 합니다. 이 경우를 제외 하 고 부울 논리 연산자는 필드에 저장 된 개별 열거형 값을 추출할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.FlagsAttribute>을 열거에 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 열거형 값을 결합할 수 없도록 하려면이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제
 다음 예제에서 `DaysEnumNeedsFlags`은 <xref:System.FlagsAttribute> 사용에 대 한 요구 사항을 충족 하지만 포함 하지 않는 열거형입니다. @No__t_0 열거형은 2의 거듭제곱 값을 포함 하지 않지만 <xref:System.FlagsAttribute>를 잘못 지정 합니다. 이 [는 열거형을 FlagsAttribute로 표시 하지 않습니다. 규칙 CA2217를](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)위반 합니다.

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2217: 열거형을 FlagsAttribute로 표시하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>관련 항목:
 <xref:System.FlagsAttribute?displayProperty=fullName>
