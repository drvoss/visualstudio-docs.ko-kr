---
title: 'CA2237: ISerializable 형식을 SerializableAttribute로 표시 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c548eb76ba36099d0cef5b651a095f35d64e033c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666686"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: ISerializable 형식을 SerializableAttribute로 표시하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식이 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 인터페이스를 구현 하 고 형식이 <xref:System.SerializableAttribute?displayProperty=fullName> 특성으로 표시 되어 있지 않습니다. 규칙은 기본 형식을 serialize 할 수 없는 파생 형식을 무시 합니다.

## <a name="rule-description"></a>규칙 설명
 공용 언어 런타임에서 serializable로 인식할 수 있도록 하려면 형식이 <xref:System.Runtime.Serialization.ISerializable> 인터페이스의 구현을 통해 사용자 지정 serialization 루틴을 사용 하는 경우에도 <xref:System.SerializableAttribute> 특성으로 표시 되어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.SerializableAttribute> 특성을 형식에 적용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 예외 클래스에 대해이 규칙에서 경고를 표시 하지 마십시오 .이 규칙은 응용 프로그램 도메인에서 올바르게 작동 하기 위해 serialize 할 수 있어야 하기 때문입니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다. 규칙을 충족 하려면 <xref:System.SerializableAttribute> 특성 줄의 주석 처리를 제거 합니다.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable을 올바르게 구현하십시오.](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: serialization 메서드를 올바르게 구현하십시오.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: 선택적 필드에 deserialization 메서드를 제공하십시오.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: serialization 생성자를 안전하게 하십시오.](../code-quality/ca2120-secure-serialization-constructors.md)
