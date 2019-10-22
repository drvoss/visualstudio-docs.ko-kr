---
title: 'CA1717: FlagsAttribute 열거형에만 복수형 이름을 사용할 수 있습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0c378d419be0d964c27cfcbe523fbe3a33da97b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669091"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: FlagsAttribute 열거형에만 복수형 이름을 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 열거형의 이름이 복수형 단어로 끝나고 열거형은 <xref:System.FlagsAttribute?displayProperty=fullName> 특성으로 표시 되지 않습니다.

## <a name="rule-description"></a>규칙 설명
 명명 규칙은 열거형의 복수형 이름이 둘 이상의 열거형 값을 동시에 지정할 수 있음을 나타냅니다. @No__t_0는 열거형이 열거형에서 비트 연산을 가능 하 게 하는 비트 필드로 처리 되어야 함을 컴파일러에 알립니다.

 열거형의 값을 한 번에 하나만 지정할 수 있는 경우 열거형의 이름은 단일 단어 여야 합니다. 예를 들어 요일을 정의 하는 열거형은 여러 날짜를 지정할 수 있는 응용 프로그램에서 사용 하기 위한 것입니다. 이 열거형은 <xref:System.FlagsAttribute> 이어야 하며 ' 일 ' 이라고 할 수 있습니다. 하루에 한 번만 지정할 수 있는 유사한 열거형은 특성이 없으며 ' Day '를 호출할 수 있습니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리를 학습 하는 데 필요한 시간이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했다는 확신을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 열거형의 이름을 단수형 단어로 설정 하거나 <xref:System.FlagsAttribute>을 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이름이 단수형 단어로 끝나는 경우 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA1714: 플래그 열거형에는 복수형 이름을 사용해야 합니다.](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: 열거형을 FlagsAttribute로 표시하십시오.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: 열거형을 FlagsAttribute로 표시하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>관련 항목:
 <xref:System.FlagsAttribute?displayProperty=fullName> [열거형 디자인](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
