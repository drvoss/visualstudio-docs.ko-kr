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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6603e0869a9eb7947735c52a4c438b39d64b9140
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157707"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: 열거형을 FlagsAttribute로 표시하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 Public 열거형의 값은 2의 거듭제곱 또는 열거형에 정의 된 다른 값의 조합이 및 <xref:System.FlagsAttribute?displayProperty=fullName> 특성이 존재 합니다. 가양성을 줄이기 위해이 규칙에는 연속 값이 있는 열거형에 대 한 위반을 보고 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 적용 <xref:System.FlagsAttribute> 열거형 때 명명 된 상수를 의미 있게 조합할 수 있습니다. 예를 들어 추적 하는 날짜의 리소스가 사용 가능한 응용 프로그램에서 요일의 열거형입니다. 각 리소스의 가용성에는 열거형을 사용 하 여 인코딩된 경우 <xref:System.FlagsAttribute> 현재 일의 조합을 나타낼 수 있습니다. 특성이 없으면만 1 일 주를 나타낼 수 있습니다.

 Combinable 열거형을 저장 하는 필드에 대 한 개별 열거형 값은 비트 필드에 그룹으로 처리 됩니다. 따라서 이러한 필드는 라고도 *비트 필드*합니다. 비트 필드의 저장소에 대 한 열거형 값을 결합 하려면 부울 조건 연산자를 사용 합니다. 특정 열거형 값이 있는지 여부를 확인 하려면 비트 필드를 테스트 하려면 부울 논리 연산자를 사용 합니다. 저장 하 고 결합 된 열거형 값을 올바르게 검색 비트 필드에 대 한 열거형에 정의 된 각 값에는 2의 거듭제곱 이어야 합니다. 그렇지 않은, 부울 논리 연산자 필드에 저장 되는 각 열거형 값을 추출할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 추가 <xref:System.FlagsAttribute> 의 열거형입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 열거형 값의 조합을 허용 하지 않을 경우이 규칙에서 경고를 표시 합니다.

## <a name="example"></a>예제
 다음 예에서 `DaysEnumNeedsFlags` 사용에 대 한 요구 사항을 충족 하는 열거형은 <xref:System.FlagsAttribute>, 하지만 갖지 않습니다. 합니다 `ColorEnumShouldNotHaveFlag` 열거형 값 2의 거듭제곱 없지만 잘못 지정 <xref:System.FlagsAttribute>합니다. 이 규칙을 위반 [CA2217: 열거형을 FlagsAttribute로 표시 하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)합니다.

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2217: 열거형을 FlagsAttribute로 표시 하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>관련 항목
 <xref:System.FlagsAttribute?displayProperty=fullName>
