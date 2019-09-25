---
title: 'CA1027: 열거형을 FlagsAttribute로 표시하세요.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8375d2096417948b19a228d8a4f02accac7c0b5f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236121"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: 열거형을 FlagsAttribute로 표시하세요.

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|범주|Microsoft.Design|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

열거형 값이 2의 거듭제곱 이거나 열거형에 정의 된 다른 값의 조합이 며 <xref:System.FlagsAttribute?displayProperty=fullName> 특성이 없는 경우 가양성을 줄이기 위해이 규칙은 연속 값을 포함 하는 열거에 대 한 위반을 보고 하지 않습니다.

기본적으로이 규칙은 공용 열거만을 찾지만이는 [구성 가능](#configurability)합니다.

## <a name="rule-description"></a>규칙 설명

열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 명명 <xref:System.FlagsAttribute> 된 상수를 의미 있게 결합할 수 있는 경우 열거형에 적용 합니다. 예를 들어 응용 프로그램에서 요일에 사용할 수 있는 리소스를 추적 하는 요일을 열거 하는 것이 좋습니다. <xref:System.FlagsAttribute> 존재 하는 열거형을 사용 하 여 각 리소스의 가용성을 인코딩한 경우 일의 조합을 표현할 수 있습니다. 특성이 없으면 요일을 한 개만 표현할 수 있습니다.

결합 가능한 열거형을 저장 하는 필드의 경우 개별 열거형 값은 필드의 비트 그룹으로 처리 됩니다. 따라서 이러한 필드를 *비트 필드*라고도 합니다. 비트 필드의 저장소에 대 한 열거 값을 결합 하려면 부울 조건부 연산자를 사용 합니다. 비트 필드를 테스트 하 여 특정 열거형 값이 있는지 여부를 확인 하려면 부울 논리 연산자를 사용 합니다. 비트 필드가 결합 된 열거형 값을 올바르게 저장 하 고 검색 하려면 열거형에 정의 된 각 값이 2의 거듭제곱 이어야 합니다. 이 경우를 제외 하 고 부울 논리 연산자는 필드에 저장 된 개별 열거형 값을 추출할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면를 열거 <xref:System.FlagsAttribute> 에 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

열거형 값을 결합할 수 없도록 하려면이 규칙에서 경고를 표시 하지 않습니다.

## <a name="configurability"></a>구성이

레거시 분석이 아닌 [FxCop 분석기](install-fxcop-analyzers.md) 에서이 규칙을 실행 하는 경우 해당 액세스 가능성에 따라이 규칙을 실행할 코드 베이스 부분을 구성할 수 있습니다. 예를 들어 public이 아닌 API 화면에 대해서만 규칙을 실행 하도록 지정 하려면 프로젝트의 editorconfig 파일에 다음 키-값 쌍을 추가 합니다.

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

이 규칙에 대해서만이 옵션을 구성 하거나, 모든 규칙에 대해 또는이 범주의 모든 규칙에 대해이 옵션을 구성할 수 있습니다 (디자인). 자세한 내용은 [FxCop 분석기 구성](configure-fxcop-analyzers.md)을 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는를 `DaysEnumNeedsFlags` 사용 <xref:System.FlagsAttribute> 하기 위한 요구 사항을 충족 하지만이를 포함 하지 않는 열거형입니다. 열거형 `ColorEnumShouldNotHaveFlag` 에 2의 거듭제곱 이지만 잘못 지정 <xref:System.FlagsAttribute>된 값이 있는 경우 규칙 [CA2217를 위반 합니다. 열거형을 FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)로 표시 하지 않습니다.

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>관련 규칙

- [CA2217: 열거형을 FlagsAttribute로 표시 하지 않습니다.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>참고 항목

- <xref:System.FlagsAttribute?displayProperty=fullName>