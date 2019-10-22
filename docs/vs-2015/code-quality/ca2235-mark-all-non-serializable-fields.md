---
title: 'CA2235: serialize 할 수 없는 모든 필드를 표시 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 709bc3dea92752d9e18c3163fe43864f5896471c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666767"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 serialize할 수 없는 형식의 인스턴스 필드가 serialize할 수 있는 형식에 정의되었습니다.

## <a name="rule-description"></a>규칙 설명
 Serializable 형식은 <xref:System.SerializableAttribute?displayProperty=fullName> 특성으로 표시 된 형식입니다. 형식이 serialize 되 면 형식에 serialize 할 수 없는 형식의 인스턴스 필드가 포함 된 경우 <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> 예외가 throw 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 직렬화 할 수 없는 필드에 <xref:System.NonSerializedAttribute?displayProperty=fullName> 특성을 적용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 필드의 인스턴스를 serialize 및 deserialize 할 수 있도록 하는 <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> 형식이 선언 된 경우에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식 및 규칙을 충족 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable을 올바르게 구현하십시오.](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: serialization 메서드를 올바르게 구현하십시오.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: ISerializable 형식을 SerializableAttribute로 표시하십시오.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: 선택적 필드에 deserialization 메서드를 제공하십시오.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: serialization 생성자를 안전하게 하십시오.](../code-quality/ca2120-secure-serialization-constructors.md)
