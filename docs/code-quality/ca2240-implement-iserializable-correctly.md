---
title: 'CA2240: ISerializable을 올바르게 구현하십시오.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2640fddcde0d8777363a3c56e398e7ff307a20c7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237875"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable을 올바르게 구현하십시오.

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

외부에서 볼 수 있는 형식은 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 인터페이스에 할당할 수 있으며 다음 조건 중 하나에 해당 합니다.

- 형식은를 상속 하지만 메서드를 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 재정의 하지 않으며 형식에서 <xref:System.NonSerializedAttribute?displayProperty=fullName> 특성으로 표시 되지 않은 인스턴스 필드를 선언 합니다.

- 형식이 sealed가 아니고 형식이 외부적으로 표시 되지 않고 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 재정의할 수 있는 메서드를 구현 합니다.

## <a name="rule-description"></a>규칙 설명
인터페이스를 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 상속 하는 형식에서 선언 된 인스턴스 필드는 serialization 프로세스에 자동으로 포함 되지 않습니다. 필드를 포함 하려면 형식이 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 메서드 및 serialization 생성자를 구현 해야 합니다. 필드를 serialize 하지 않아야 하는 경우 필드에 <xref:System.NonSerializedAttribute> 특성을 적용 하 여 결정을 명시적으로 지정 합니다.

봉인 되지 않은 형식에서 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 메서드의 구현은 외부에서 볼 수 있어야 합니다. 따라서 메서드는 파생 형식에 의해 호출 될 수 있으며 재정의할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 메서드를 표시 하 고 재정의 가능 하 게 설정 하 고 모든 인스턴스 필드가 serialization 프로세스에 포함 되거나 명시적으로 <xref:System.NonSerializedAttribute> 특성으로 표시 되도록 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
다음 예제에서는 규칙을 위반 하는 serialize 할 수 있는 두 가지 형식을 보여 줍니다.

[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>예제
다음 예제에서는 Book 클래스에서의 <xref:System.Runtime.Serialization.ISerializable.GetObjectData> 재정의 가능 구현을 제공 하 고 라이브러리 클래스에서의 `GetObjectData` 구현을 제공 하 여 두 가지 이전 위반을 수정 합니다.

[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>관련 규칙

- [CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출 합니다.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Serialization 메서드를 올바르게 구현 하십시오.](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: 선택적 필드에 deserialization 메서드 제공](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: 보안 serialization 생성자](../code-quality/ca2120-secure-serialization-constructors.md)