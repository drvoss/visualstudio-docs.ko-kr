---
title: 'CA2237: SerializableAttribute로 ISerializable 형식 표시'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237937"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: SerializableAttribute로 ISerializable 형식 표시

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
외부에서 볼 수 있는 형식이 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 인터페이스를 구현 하 고 형식이 <xref:System.SerializableAttribute?displayProperty=fullName> 특성으로 표시 되지 않습니다. 규칙은 기본 형식을 serialize 할 수 없는 파생 형식을 무시 합니다.

## <a name="rule-description"></a>규칙 설명
공용 언어 런타임에서 serializable로 인식 되려면 형식에서 <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.ISerializable> 인터페이스 구현을 통해 사용자 지정 serialization 루틴을 사용 하는 경우에도 형식을 특성으로 표시 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 형식에 <xref:System.SerializableAttribute> 특성을 적용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
예외 클래스에 대해이 규칙에서 경고를 표시 하지 마십시오 .이 규칙은 응용 프로그램 도메인에서 올바르게 작동 하기 위해 serialize 할 수 있어야 하기 때문입니다.

## <a name="example"></a>예제
다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다. 규칙을 <xref:System.SerializableAttribute> 충족 하려면 특성 줄의 주석 처리를 제거 합니다.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>관련 규칙
[CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출 합니다.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: ISerializable을 올바르게 구현 하십시오.](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Serialization 메서드를 올바르게 구현 하십시오.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239: 선택적 필드에 deserialization 메서드 제공](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: 보안 serialization 생성자](../code-quality/ca2120-secure-serialization-constructors.md)