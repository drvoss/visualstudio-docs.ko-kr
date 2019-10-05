---
title: 'CA1501: 상속성을 너무 많이 사용하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 88464effce80b6957dc8945ad17f5a39b4f449c8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234511"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: 상속성을 너무 많이 사용하지 마세요.

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|범주|Microsoft.Maintainability|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인

형식이 상속 계층 구조에서 네 단계보다 아래에 있습니다.

## <a name="rule-description"></a>규칙 설명

여러 번 중첩된 형식 계층 구조는 추적하고, 이해하고, 유지 관리하기가 어렵습니다. 이 규칙은 동일한 모듈의 계층에 대 한 분석을 제한 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 상속 계층 구조에서 더 작은 기본 형식에서 형식을 파생 시키거나 중간 기본 형식 중 일부를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이 규칙에서는 경고를 표시 하지 않는 것이 안전 합니다. 그러나 코드를 유지 관리 하기가 더 어려울 수 있습니다. 기본 형식의 표시 여부에 따라이 규칙 위반을 해결 하는 것은 주요 변경 내용을 만들 수 있습니다. 예를 들어 공용 기본 형식을 제거 하는 것은 주요 변경 사항입니다.

## <a name="example"></a>예제

다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]