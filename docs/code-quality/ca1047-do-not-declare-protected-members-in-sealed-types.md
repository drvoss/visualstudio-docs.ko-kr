---
title: 'CA1047: protected 멤버를 sealed 형식으로 선언하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3114ea004c425567ae479343e0449d2cbc3aa669
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235697"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: protected 멤버를 sealed 형식으로 선언하지 마세요.

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|범주|Microsoft.Design|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
Public 형식은 `sealed` (`NotInheritable` Visual basic의 경우) 이며 protected 멤버나 protected 중첩 형식을 선언 합니다. 이 규칙은이 패턴을 따라야 <xref:System.Object.Finalize%2A> 하는 메서드에 대 한 위반을 보고 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
형식에서는 상속하는 형식에서 멤버에 액세스하거나 멤버를 재정의할 수 있도록 하기 위해 protected 멤버를 선언합니다. 정의에 따라 sealed 형식에서 상속할 수 없습니다 .이는 sealed 형식의 protected 메서드를 호출할 수 없음을 의미 합니다.

컴파일러 C# 에서이 오류에 대 한 경고를 발생 시킵니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 멤버의 액세스 수준을 private으로 변경 하거나 형식을 상속 가능 하 게 설정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다. 현재 상태를 유지 하면 유지 관리 문제가 발생할 수 있으며 어떤 이점도 제공 하지 않습니다.

## <a name="example"></a>예제
다음 예제에서는이 규칙을 위반 하는 형식을 보여 줍니다.

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]