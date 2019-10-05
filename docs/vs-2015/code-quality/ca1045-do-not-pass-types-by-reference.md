---
title: 'CA1045: 참조로 형식을 전달 하지 않습니다 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6bbdcb2e2ac8f905a2b52cfb41ed90217d215b4b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431550"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: 참조로 형식을 전달하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 형식에서 public 또는 protected 메서드는 `ref` 기본 형식, 참조 형식 또는 값 형식을 사용 하는 매개 변수는 기본 제공 형식 중 하나가 없습니다.

## <a name="rule-description"></a>규칙 설명
 참조로 형식을 전달 (사용 하 여 `out` 또는 `ref`) 포인터를 값 형식과 참조 형식이 어떻게를 이해 하 고 여러 값을 반환 하는 메서드를 처리 해야 합니다. 간의 차이 뿐만 `out` 고 `ref` 매개 변수는 잘 알려져 있지 않습니다.

 참조 형식 참조""로 전달 되 면 메서드는 개체의 다른 인스턴스를 반환 하려면 매개 변수를 사용 하는입니다. (참조 형식을 참조로 전달 됩니다 라고도 double 포인터를 포인터 또는 이중 간접 참조에 대 한 포인터를 사용 하 여 합니다.) 호출 규칙, "값으로"를 전달 하는 기본값을 사용 하 여 이미 참조 형식을 사용 하는 매개 변수 개체에 대 한 포인터를 받습니다. 포인터에서 가리키는 개체가 아닌 값으로 전달 됩니다. 포인터를 참조의 새 인스턴스를 가리키도록 변경할 수 있다는 것을 의미 하지만 가리키는 개체의 콘텐츠를 변경할 수 값으로 전달 합니다. 대부분의 응용 프로그램에 대 한 충분이 고 원하는 동작을 생성 합니다.

 메서드는 다른 인스턴스로 반환 해야 하는 경우 이렇게 하려면 메서드의 반환 값을 사용 합니다. 참조 된 <xref:System.String?displayProperty=fullName> 다양 한 문자열에서 작동 하 고 문자열의 새 인스턴스를 반환 하는 방법에 대 한 클래스입니다. 이 모델을 사용 하면 원래 개체의 유지 여부를 결정 하기 위해 호출자에 중단 됩니다.

 반환 값은 일반적 이며의 올바른 응용 프로그램을 많이 사용 되지만 `out` 고 `ref` 중간 디자인 및 코딩 기술을 매개 변수가 필요 합니다. 일반 사용자를 대상에는 마스터 작업에 사용자를 사용 해야 합니다.에 대 한 디자인 하는 라이브러리 설계자 `out` 또는 `ref` 매개 변수입니다.

> [!NOTE]
> 매개 변수를 큰 구조를 사용 하 여 작업할 때 이러한 구조를 복사 하는 데 필요한 추가 리소스를 값으로 전달 하는 경우 성능에 영향을 발생할 수 있습니다. 이러한 경우에 사용해 보십시오 `ref` 또는 `out` 매개 변수입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 값 형식에서 발생 하는이 규칙 위반 문제를 해결 하려면 메서드 반환 값으로 개체를 반환 해야 합니다. 메서드가 여러 값을 반환 해야 하는 경우 값을 포함 하는 개체의 단일 인스턴스를 반환 하도록 다시 설계 합니다.

 참조 형식에 의해 발생 하는이 규칙 위반 문제를 해결 하려면 참조의 새 인스턴스를 반환 하는 동작을 인지를 확인 합니다. 이 경우 메서드 이렇게 하려면 해당 반환 값을 사용 해야 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙;에서 경고를 표시 하지 않아도 안전 합니다. 그러나이 디자인은 사용 편의성 문제를 발생할 수 있습니다.

## <a name="example"></a>예제
 다음 라이브러리에는 사용자의 피드백에 대 한 응답을 생성 하는 클래스의 두 가지 구현을 보여 줍니다. 첫 번째 구현 (`BadRefAndOut`) 라이브러리 사용자가 세 개의 반환 값을 관리 합니다. 두 번째 구현 (`RedesignedRefAndOut`)는 컨테이너 클래스의 인스턴스를 반환 하 여 사용자 환경을 단순화 (`ReplyData`) 단일 단위로 데이터를 관리 하는 합니다.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램은 사용자의 경험을 보여 줍니다. 새로 디자인 된 라이브러리에 대 한 호출 (`UseTheSimplifiedClass` 메서드)는 더 간단 합니다 메서드에 의해 반환 되는 정보를 쉽게 관리 되 고 있습니다. 두 방법 중에서 출력은 동일 합니다.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>예제
 다음 예제 라이브러리를 보여 줍니다 어떻게 `ref` 참조 형식에 대 한 매개 변수를 사용 하 고이 기능을 구현 하는 더 나은 방법을 보여 줍니다.

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
## <a name="related-rules"></a>관련된 규칙
 [CA1021: Out 매개 변수를 방지](../code-quality/ca1021-avoid-out-parameters.md)
