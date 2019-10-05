---
title: 'CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238111"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

serialize할 수 없는 형식의 인스턴스 필드가 serialize할 수 있는 형식에 정의되었습니다.

## <a name="rule-description"></a>규칙 설명

Serialize 할 수 있는 형식은 <xref:System.SerializableAttribute?displayProperty=fullName> 특성으로 표시 되는 형식입니다. 형식이 serialize <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> 될 때 형식이 serialize 할 수 없는 형식의 인스턴스 필드를 포함 하 *고* 인터페이스를 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 구현 하지 않는 경우 예외가 throw 됩니다.

> [!TIP]
> CA2235는 자체 serialization 논리를 제공 하기 때문에를 <xref:System.Runtime.Serialization.ISerializable> 구현 하는 형식의 인스턴스 필드에 대해 발생 하지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 직렬화 할 수 <xref:System.NonSerializedAttribute?displayProperty=fullName> 없는 필드에 특성을 적용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

필드의 인스턴스를 serialize 및 deserialize 할 수 <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> 있도록 하는 형식을 선언 하는 경우에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제

다음 예제에서는 두 가지 형식을 보여 줍니다. 하나는 규칙을 위반 하 고 다른 하나는 규칙을 만족 합니다.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>설명

규칙 CA2235 <xref:System.SerializableAttribute> 특성으로 표시 되지 않은 경우 인터페이스 <xref:System.Runtime.Serialization.ISerializable> 를 구현 하는 형식을 분석 하지 않습니다. 이는 [규칙 CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) 인터페이스를 <xref:System.Runtime.Serialization.ISerializable> 구현 하는 형식을 <xref:System.SerializableAttribute> 특성으로 표시 하는 것이 이미 권장 되기 때문입니다.

## <a name="related-rules"></a>관련 규칙

- [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출 합니다.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Serialization 메서드를 올바르게 구현 하십시오.](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: 선택적 필드에 deserialization 메서드 제공](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: ISerializable을 올바르게 구현 하십시오.](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: 보안 serialization 생성자](../code-quality/ca2120-secure-serialization-constructors.md)