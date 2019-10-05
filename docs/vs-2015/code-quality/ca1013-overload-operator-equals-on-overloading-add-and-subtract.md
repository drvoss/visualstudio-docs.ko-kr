---
title: 'CA1013: 오버 로드에 같음 연산자를 오버 더하기 및 빼기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1b70085c83d842ccb5f8addc661af9109b5a5976
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695618"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: 더하기 및 빼기를 오버로드할 때 같음 연산자를 오버로드하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 public 또는 protected 형식이 같음 연산자를 구현하지 않고 더하기 또는 빼기 연산자를 구현합니다.

## <a name="rule-description"></a>규칙 설명
 더하기 및 빼기 같은 작업을 사용 하 여 형식의 인스턴스를 결합할 수를 반환 하려면 같음 정의 거의 항상 해야 `true` 구성 값이 동일한 두 인스턴스에 대 한 합니다.

 기본 같음 연산자를 같음 연산자의 오버 로드 된 구현을 사용할 수 없습니다. 이렇게 하면 스택 오버플로가 발생 합니다. 같음 연산자를 구현 하려면 구현에서 Object.Equals 메서드를 사용 합니다. 다음 예제를 참조하세요.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 더하기 및 빼기 연산자를 사용 하 여 수학적으로 일관성이 있도록 같음 연산자를 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 같음 연산자의 기본 구현 형식에 대 한 올바른 동작을 제공 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 형식 정의 (`BadAddableType`)는이 규칙을 위반 합니다. 이 형식은 테스트 필드 값이 같으면 두 인스턴스에 확인 하도록 같음 연산자를 구현 해야 `true` 같음에 대 한 합니다. 형식 `GoodAddableType` 수정 된 구현을 보여 줍니다. 이 형식은 또한 같지 않음 연산자를 구현 하 고 재정의 <xref:System.Object.Equals%2A> 다른 규칙을 충족 하도록 합니다. 완전 한 구현도 구현 <xref:System.Object.GetHashCode%2A>합니다.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 같음 연산자에 대 한 기본 및 올바른 동작을 설명 하기 위해이 항목의 이전에 정의 된 형식의 인스턴스를 사용 하 여 같은지 테스트 합니다.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **잘못 된 형식: {2,2} {2,2} 같은지? 아니오**
**적절 한 형식: {3,3} {3,3} 같은지? 예**
**적절 한 형식: {3,3} {3,3} 는 = =?   예**
**잘못 된 형식: {2,2} {9,9} 같은지? 아니오**
**적절 한 형식: {3,3} {9,9} 는 = =?   No**
## <a name="see-also"></a>참고 항목
 [같음 연산자](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
