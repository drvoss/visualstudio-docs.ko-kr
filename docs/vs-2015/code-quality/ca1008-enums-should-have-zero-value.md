---
title: 'CA1008: 열거형 값이 0 이면 있어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e9b607c3a3fd7992bf8947c003d240d3d5b1d312
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182621"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: 열거형에는 0 값이 있어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|범주|Microsoft.Design|
|변경 수준|아님-한 경우 추가 메시지가 표시 되는 **없음** 비 플래그 열거형 값입니다. 주요-이름 바꾸기 또는 열거형 값을 제거 하는 메시지가 있습니다.|

## <a name="cause"></a>원인
 적용 되지 않은 열거형 <xref:System.FlagsAttribute?displayProperty=fullName> 0 또는 적용 된 열거형의 값이 있는 멤버를 정의 하지 않습니다 <xref:System.FlagsAttribute> 멤버 정의 합니다. 0 값이 있는 있지만 해당 이름이 'None', 또는 열거형 값이 0 인 여러 정의 멤버입니다.

## <a name="rule-description"></a>규칙 설명
 다른 값 형식과 마찬가지로 초기화 되지 않은 열거형의 기본값은 0입니다. 비 플래그 열거형에는 기본 값이 열거형의 유효한 값이 되도록 0 값을 가진 멤버를 정의 해야 합니다. 해당 하는 경우 멤버의 이름을 '없음'입니다. 가장 자주 사용 되는 멤버에 0이 고, 그렇지 할당 합니다. 참고, 기본적으로 선언에서 첫 번째 열거형 멤버의 값을 설정 하지 않으면 해당 값은 0입니다.

 경우에 열거형을 <xref:System.FlagsAttribute> 적용 값이 0 인 멤버를 정의 합니다. 해당 이름은 열거형에 값이 없는 설정 되어 있다고 나타내기 위해 ' 없음' 이어야 합니다. 다른 용도로 달리 사용에 대 한 값이 0 인 멤버를 사용 하는 <xref:System.FlagsAttribute> 에 AND 및 또는 비트 연산자는 멤버와 의미가 없습니다. 즉, 해당 멤버가 하나만 값 0을 할당 해야 합니다. 여러 멤버가 있는 경우 0 값 발생 플래그 특성을 사용 하는 열거형에 참고 `Enum.ToString()` 은 0이 아닌 멤버에 대 한 잘못 된 결과 반환 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 비 플래그 열거형에 대 한이 규칙 위반 문제를 해결 하려면 0의 값을 가진 멤버를 정의 합니다. 이 줄 바꿈하지 않는 변경 내용입니다. 플래그 특성을 사용 하는 열거형 값이 0 인 멤버를 정의 '없음'이 멤버 이름 및 0; 값이 있는 다른 멤버를 삭제 합니다. 주요 변경 내용입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 에 이전에 제공 된 플래그 특성을 사용 하는 열거형을 제외 하 고이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 충족 하는 두 개의 열거형 및 열거형 `BadTraceOptions`, 규칙을 위반 하는 합니다.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2217: 열거형을 FlagsAttribute로 표시 하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: 열거형 값 ' 이름을 바꾸지 마십시오](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: 열거형 값 형식 이름의 접두사로 사용 하지 마세요](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: 열거형 저장소는 Int32 여야 합니다.](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: 열거형을 FlagsAttribute로 표시](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Enum?displayProperty=fullName>
