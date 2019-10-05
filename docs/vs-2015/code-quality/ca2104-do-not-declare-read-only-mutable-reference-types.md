---
title: 'CA2104: 읽기 전용 참조 형식을 선언 하지 마십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a4c6619bc5803c1b44e1c6b0516987c3110bbd30
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687412"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: 변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식에 변경 가능한 참조 형식인, 외부에서 볼 수 있는 읽기 전용 필드가 포함되었습니다.

## <a name="rule-description"></a>규칙 설명
 변경 가능한 형식은 해당 인스턴스 데이터를 수정할 수 있는 형식을 말합니다. <xref:System.Text.StringBuilder?displayProperty=fullName> 클래스는 변경 가능한 참조 형식의 예입니다. 클래스의 인스턴스 값을 변경할 수 있는 멤버가 포함 됩니다. 변경할 수 없는 참조 형식의 예로 <xref:System.String?displayProperty=fullName> 클래스입니다. 시작 된 후 해당 값 변경할 수 없습니다.

 읽기 전용 한정자 ([읽기 전용](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) 에서 C#, [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], 및 [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) 에서 C++) 참조 형식 필드 (포인터 C++) 필드 참조 형식의 다른 인스턴스에 의해 바꾸지 못하도록 방지 합니다. 그러나 한정자는 참조 형식을 통해 수정 되지 않도록 필드의 인스턴스 데이터를 방지 하지 않습니다.

 읽기 전용 배열 필드는이 규칙에서 제외 됩니다. 하지만 대신 위반 하는 [CA2105: 배열 필드는 읽기 전용 이면 안](../code-quality/ca2105-array-fields-should-not-be-read-only.md) 규칙입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 읽기 전용 한정자를 제거 하거나 주요 변경 내용 허용 되는 경우 필드를 변경할 수 없는 형식으로 대체 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 필드 형식을 변경할 수 없는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙 위반을 발생 시키는 필드 선언을 보여 줍니다.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
