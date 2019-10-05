---
title: 'CA1710: 식별자에는 올바른 접미사를 사용 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 16b4c2fb13a8de1824233b491d752b796aea907d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676543"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: 식별자에는 올바른 접미사를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|범주|Microsoft.Naming|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 식별자는 올바른 접미사는 없습니다.

## <a name="rule-description"></a>규칙 설명
 규칙에 따라 특정 기본 형식을 확장 하거나 특정 인터페이스 또는 이러한 형식에서 파생 된 형식을 구현 하는 형식의 이름을 기본 형식 또는 인터페이스와 연결 된 접미사를 갖습니다.

 명명 규칙은 공통 된 모양을 라이브러리에 대 한 해당 공용 언어 런타임을 대상으로 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 대 한 필수 항목이 며 관리 코드 개발의 전문 지식을 가진 사람이 라이브러리를 개발 하는 고객 신뢰도 증가 하는 학습 곡선을 줄어듭니다.

 다음 표에서 기본 형식 및 연관 된 접미사가 있는 인터페이스를 나열 합니다.

|기본 형식/인터페이스|접미사|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|특성|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|예외|
|<xref:System.Collections.ICollection?displayProperty=fullName>|컬렉션|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|사전|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|컬렉션|
|<xref:System.Collections.Queue?displayProperty=fullName>|컬렉션 또는 큐|
|<xref:System.Collections.Stack?displayProperty=fullName>|컬렉션 또는 스택|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|컬렉션|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|사전|
|<xref:System.Data.DataSet?displayProperty=fullName>|데이터 세트|
|<xref:System.Data.DataTable?displayProperty=fullName>|컬렉션 또는 DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|스트림|
|<xref:System.Security.IPermission?displayProperty=fullName>|사용 권한|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|조건|
|이벤트 처리기 대리자입니다.|이벤트 처리기|

 구현 하는 형식 <xref:System.Collections.ICollection> 사전, 스택 또는 큐 이름 형식의 용도 대 한 의미 있는 정보를 제공 하는 수와 같은 데이터 구조의 일반화 된 유형은 및 합니다.

 구현 하는 형식 <xref:System.Collections.ICollection> 및 특정 항목의 컬렉션인 'Collection' 라는 단어로 끝나는 이름이 됩니다. 예를 들어, 컬렉션의 <xref:System.Collections.Queue> 개체 이름 'QueueCollection' 해야 합니다. 'Collection' 접미사를 사용 하 여 컬렉션의 멤버를 열거할 수 있습니다 의미 합니다 `foreach` (`For Each` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 문입니다.

 구현 하는 형식을 <xref:System.Collections.IDictionary> 도 구현 하는 경우에 '사전' 라는 단어로 끝나는 이름이 <xref:System.Collections.IEnumerable> 또는 <xref:System.Collections.ICollection>합니다. 'Collection' 및 '사전' 접미사 명명 규칙을 사용 하면 다음과 같은 두 개의 열거형 패턴을 구분할 수 있도록 합니다.

 유형 'Collection' 접미사를 사용 하 여이 열거형 패턴을 따릅니다.

```
foreach(SomeType x in SomeCollection) { }
```

 '사전' 접미사를 사용 하 여 형식 열거형 패턴을 따릅니다.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 A <xref:System.Data.DataSet> 개체의 컬렉션으로 구성 됩니다 <xref:System.Data.DataTable> 개체의 컬렉션으로 구성 된 <xref:System.Data.DataColumn?displayProperty=fullName> 및 <xref:System.Data.DataRow?displayProperty=fullName> 특히 개체입니다. 이러한 컬렉션은 구현 <xref:System.Collections.ICollection> 기본 통해 <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> 클래스입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 형식을 이름을 올바른 용어 붙습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식이 확장 될 수 또는 임의 집합 다양 한 항목을 보유 하는 일반화 된 데이터 구조 이면 'Collection' 접미사를 사용할 때는 경고를 표시 하지 않으려면 안전 합니다. 이 경우 구현, 성능 또는 기타 특성의 데이터 구조에 대 한 의미 있는 정보를 제공 하는 이름을 적합할 수 있습니다 (예를 들어 BinaryTree). 여기서 형식 나타냅니다 (예를 들어 StringCollection) 특정 형식의 컬렉션인 경우에 숨기지 않으면,이 규칙에서 경고 유형을 사용 하 여 열거할 수는 나타내므로 접미사는 `foreach` 문입니다.

 다른 접미사에 대 한이 규칙에서 경고를 표시 하지 마십시오. 접미사를 사용 하면 형식 이름에서 알 수 되도록 용도입니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1711: 식별자에는 접미사를 사용 해야 합니다.](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>참고 항목
 [특성](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: 이벤트 및 대리자](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
