---
title: 'CA2229: Serialization 생성자를 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 41e296a979557a42a96c2f57ce49610d88b98a40
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201569"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: serialization 생성자를 구현하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 형식에서 구현 된 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 인터페이스, 대리자 또는 인터페이스 아니며 다음 조건 중 하나가 true 인:

- 형식 없는 받아들이는 생성자는 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> 개체 및 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 개체 (serialization 생성자 서명).

- 형식은 봉인 하 고 serialization 생성자에 대 한 액세스 한정자는 없습니다. 보호 된 (제품군)입니다.

- 형식이 sealed 형식 인지 하 고 serialization 생성자에 대 한 액세스 한정자를 개인있지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 사용자 지정 serialization을 지 원하는 형식에 적합 합니다. 형식을 구현 하는 경우 사용자 지정 serialization을 지원 합니다 <xref:System.Runtime.Serialization.ISerializable> 인터페이스입니다. Serialization 생성자를 deserialize 하거나 다시 사용 하 여 serialize 된 개체를 만들 필요는 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 메서드.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결하려면 serialization 생성자를 구현합니다. 봉인 클래스의 경우에는 생성자를 private으로 만들고, 그 밖의 경우에는 protected로 만듭니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 규칙의 위반을 표시 하지 마십시오. 형식을은 역직렬화 할 수, 되지 않으며 대부분의 시나리오에서 작동 하지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 충족 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
