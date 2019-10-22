---
title: 'CA1058: 형식은 특정 기본 형식을 확장 하면 안 됩니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9a4663fe3bc09b27bad9eeec05e325f07a3de6f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603061"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: 형식은 특정 기본 형식을 확장하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식이 특정 기본 형식을 확장합니다. 현재이 규칙은 다음 형식에서 파생 되는 형식을 보고 합니다.

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
 @No__t_0 버전 1의 경우 <xref:System.ApplicationException>에서 새 예외를 파생 시키는 것이 좋습니다. 권장 사항이 변경 되 고 새 예외는 <xref:System.Exception?displayProperty=fullName> 또는 <xref:System> 네임 스페이스의 서브 클래스 중 하나에서 파생 되어야 합니다.

 기본 개체 모델 또는 데이터 원본의 XML 뷰를 만들려는 경우에는 <xref:System.Xml.XmlDocument>의 서브 클래스를 만들지 마십시오.

### <a name="non-generic-collections"></a>제네릭이 아닌 컬렉션
 가능 하면 언제 든 지 및/또는 제네릭 컬렉션을 확장 하십시오. 이전에 제공 하지 않는 한 코드에서 제네릭이 아닌 컬렉션을 확장 하지 마십시오.

 **잘못 된 사용 예**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **올바른 사용법의 예**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 다른 기본 형식 또는 제네릭 컬렉션에서 형식을 파생 시킵니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 @No__t_0에 대 한 위반에 대해서는이 규칙의 경고를 표시 하지 마십시오. @No__t_0에 대 한 위반에 대 한 경고를이 규칙에서 무시 해도 안전 합니다. 코드가 이전에 릴리스된 경우 제네릭이 아닌 컬렉션에 대 한 경고를 표시 하지 않는 것이 안전 합니다.
