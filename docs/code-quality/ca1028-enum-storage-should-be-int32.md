---
title: 'CA1028: 열거형 저장소는 Int32여야 합니다.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 51e4177b01dc15177b74394d6967651905da2122
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547830"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: 열거형 저장소는 Int32여야 합니다.

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 열거형의 기본 형식이 아닙니다 <xref:System.Int32?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 기본적으로 <xref:System.Int32?displayProperty=fullName> 데이터 형식은 상수 값을 저장 하는 데 사용 됩니다. 하지만 기본 형식을 변경할 수 있습니다, 것 아닙니다 필요 하거나 권장 되는 대부분의 시나리오에 대 한 합니다. 보다 작은 데이터 형식을 사용 하 여 없습니다 상당한 수준의 성능 향상을 수행할는 <xref:System.Int32>합니다. 공용 언어 시스템 (CLS)의 하나를 사용 해야 기본 데이터 형식을 사용할 수 없으면,-규격 정수 형식 <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, 또는 <xref:System.Int64> 열거형의 모든 값에 나타낼 수 있는지 확인 하려면 Cls 규격이 아닌 프로그래밍 언어입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 크기 또는 호환성 문제가 발생 하지 않는 한이 규칙 위반의 문제를 해결 하려면 사용 <xref:System.Int32>합니다. 상황에 대 한 위치 <xref:System.Int32> 값을 보유를 사용 하 여 충분히 크지 않은 <xref:System.Int64>합니다. 이전 버전과 호환성을 보다 작은 데이터 형식에 필요한 경우 사용 하 여 <xref:System.Byte> 또는 <xref:System.Int16>합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우
 이전 버전과 호환성 문제에 필요한 경우에이 규칙에서 경고를 표시 합니다. 응용 프로그램에서 일반적으로이 규칙을 준수 하지 못하면 문제를 발생 하지 않습니다. 언어 상호 운용성이 필요한 라이브러리에서이 규칙을 준수 하지 못하면 사용자에 게 저하 될 수 있습니다.

## <a name="example-of-a-violation"></a>위반의 예

### <a name="description"></a>설명
 다음 예에서는 권장 되는 기본 데이터 형식을 사용 하지 않는 두 개의 열거형을 보여 줍니다.

### <a name="code"></a>코드
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>수정 하는 방법의 예

### <a name="description"></a>설명
 다음 예제에서는 기본 데이터 형식을 변경 하 여 위반을 해결 <xref:System.Int32>합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>관련된 규칙
 [CA1008: 열거형에는 0 값이 있어야 합니다.](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: 열거형을 FlagsAttribute로 표시하십시오.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: 열거형을 FlagsAttribute로 표시하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: 열거형 값의 이름을 'Reserved'로 지정하지 마십시오.](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: 열거형 값에 형식 이름을 접두사로 사용하지 마십시오.](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>참고자료

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>