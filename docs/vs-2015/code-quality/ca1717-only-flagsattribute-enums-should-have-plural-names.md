---
title: 'CA1717: FlagsAttribute 열거형에는 복수형 이름을 사용 해야 합니다. 전용 | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aa0c51eaa10503a92c21960dc3dd074aa7541f5c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694953"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: FlagsAttribute 열거형만 복수형 이름을 가질 수 있습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|범주|Microsoft.Naming|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 표시 되는 열거형의 이름을 복수 word에서 끝나고 열거형으로 표시 되지 않으면를 <xref:System.FlagsAttribute?displayProperty=fullName> 특성입니다.

## <a name="rule-description"></a>규칙 설명
 명명 규칙을 열거형에는 복수형 이름을 나타내는 열거형의 하나 이상의 값을 동시에 지정할 수 있음을 나타냅니다. <xref:System.FlagsAttribute> 열거형을 비트 연산은 열거형을 사용 하도록 설정 하는 비트 필드로 처리 해야 함을 컴파일러에 지시 합니다.

 경우에 한 번에 하나의 열거형 값을 지정할 수 있습니다, 열거형의 이름은는 단일 단어 여야 합니다. 예를 들어 일 주를 정의 하는 열거형 수 사용 하려는 응용 프로그램에서 여러 날짜를 지정할 수 있습니다. 이 열거형 있어야는 <xref:System.FlagsAttribute> '일' 호출할 수 없습니다. 하루를 지정할 수 있도록 유사한 열거형은 특성 없고 수 'Day'를 호출 합니다.

 명명 규칙은 공통 된 모양을 라이브러리에 대 한 해당 공용 언어 런타임을 대상으로 합니다. 이 관리 코드 개발의 전문 지식을 가진 사람이 라이브러리를 개발 하는 고객 신뢰도 높이고 새 소프트웨어 라이브러리를 익히는 데 필요한 시간이 줄어듭니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 열거형의 이름을 단 수 단어를 확인 하거나 추가 된 <xref:System.FlagsAttribute>합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이름을 단수형 단어로 끝나는 경우 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1714: 플래그 열거형에는 복수형 이름을 사용 해야 합니다.](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: 열거형을 FlagsAttribute로 표시](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: 열거형을 FlagsAttribute로 표시 하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>참고 항목
 <xref:System.FlagsAttribute?displayProperty=fullName> [열거형 디자인](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
