---
title: 'CA1021: Out 매개 변수 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b52d5a97fc3c2e3a6bf5b4bb938bad9da50d3a7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144821"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: out 매개 변수를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 형식에서 public 또는 protected 메서드는 `out` 매개 변수입니다.

## <a name="rule-description"></a>규칙 설명
 참조로 형식을 전달 (사용 하 여 `out` 또는 `ref`) 포인터를 값 형식과 참조 형식이 어떻게를 이해 하 고 여러 개의 반환 값을 사용 하 여 메서드를 처리 해야 합니다. 간의 차이 뿐만 `out` 고 `ref` 매개 변수는 잘 알려져 있지 않습니다.

 참조 형식 참조""로 전달 되 면 메서드는 개체의 다른 인스턴스를 반환 하려면 매개 변수를 사용 하는입니다. Double 포인터를 포인터 또는 이중 간접 참조에 대 한 포인터를 사용 하 여 참조 형식을 참조로 전달 라고도 합니다. 기본 호출 "값으로"를 전달 하는 규칙을 사용 하 여 이미 참조 형식을 사용 하는 매개 변수 개체에 대 한 포인터를 받습니다. 포인터에서 가리키는 개체가 아닌 값으로 전달 됩니다. 메서드는 참조 형식의 새 인스턴스를 가리키도록에 대 한 포인터를 변경할 수 없는 값 수단으로 전달 합니다. 그러나 가리키는 개체의 내용을 변경할 수 있습니다. 대부분의 응용 프로그램에 대 한 충분이 고 원하는 동작을 생성 합니다.

 메서드는 다른 인스턴스로 반환 해야 하는 경우 이렇게 하려면 메서드의 반환 값을 사용 합니다. 참조 된 <xref:System.String?displayProperty=fullName> 다양 한 문자열에서 작동 하 고 문자열의 새 인스턴스를 반환 하는 방법에 대 한 클래스입니다. 이 모델을 사용 하는 경우 호출자는 원래 개체의 유지 여부를 결정 해야 합니다.

 반환 값은 일반적 이며의 올바른 응용 프로그램을 많이 사용 되지만 `out` 고 `ref` 중간 디자인 및 코딩 기술을 매개 변수가 필요 합니다. 일반 사용자를 대상에는 마스터 작업에 사용자를 사용 해야 합니다.에 대 한 디자인 하는 라이브러리 설계자 `out` 또는 `ref` 매개 변수입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 값 형식에서 발생 하는이 규칙 위반 문제를 해결 하려면 메서드 반환 값으로 개체를 반환 해야 합니다. 메서드가 여러 값을 반환 해야 하는 경우 값을 포함 하는 개체의 단일 인스턴스를 반환 하도록 다시 설계 합니다.

 참조 형식에 의해 발생 하는이 규칙 위반 문제를 해결 하려면 원하는 동작은 참조의 새 인스턴스를 반환 하는 해야 합니다. 이 경우 메서드 이렇게 하려면 해당 반환 값을 사용 해야 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 표시 하지 않아도 안전 합니다. 그러나이 디자인은 사용 편의성 문제를 발생할 수 있습니다.

## <a name="example"></a>예제
 다음 라이브러리에는 사용자의 피드백에 대 한 응답을 생성 하는 클래스의 두 가지 구현을 보여 줍니다. 첫 번째 구현 (`BadRefAndOut`) 라이브러리 사용자가 세 개의 반환 값을 관리 합니다. 두 번째 구현 (`RedesignedRefAndOut`)는 컨테이너 클래스의 인스턴스를 반환 하 여 사용자 환경을 단순화 (`ReplyData`) 단일 단위로 데이터를 관리 하는 합니다.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램은 사용자의 경험을 보여 줍니다. 새로 디자인 된 라이브러리에 대 한 호출 (`UseTheSimplifiedClass` 메서드)는 더 간단 합니다 메서드에서 반환 된 정보를 쉽게 관리 되 고 있습니다. 두 방법 중에서 출력은 동일 합니다.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>예제
 다음 예제 라이브러리를 보여 줍니다 어떻게 `ref` 참조 형식에 대 한 매개 변수는 사용 되 고이 기능을 구현 하는 더 나은 방법을 보여 줍니다.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램 동작을 보여 주기 위해 라이브러리에서 각 메서드를 호출 합니다.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **변경에 대 한 포인터-값으로 전달 합니다.** 
**12345**
**12345**
**Changing 포인터-참조로 전달:** 
**12345**
**12345 ABCDE**
**반환 값으로 전달:** 
**12345 ABCDE**
## <a name="try-pattern-methods"></a>패턴 메서드를 시도 하세요.

### <a name="description"></a>Description
 구현 하는 메서드를 **시도\<항목 >** 같은 패턴 <xref:System.Int32.TryParse%2A?displayProperty=fullName>,이 위반이 발생 하지 않습니다. 다음 예제에서는 구현 하는 구조체 (값 형식)는 <xref:System.Int32.TryParse%2A?displayProperty=fullName> 메서드.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1045: 참조로 형식을 전달 하지 않습니다](../code-quality/ca1045-do-not-pass-types-by-reference.md)
