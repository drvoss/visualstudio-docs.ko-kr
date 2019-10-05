---
title: 'CA1800: 불필요 하 게 캐스팅 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 49ffc66b1b7047c7b88664ac0c5198fbd51c51c6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682068"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: 불필요하게 캐스트하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 인수 또는 지역 변수 중 하나에서 중복 캐스팅을 수행합니다. 이 규칙에 의해 완벽 하 게 분석에 대 한 디버깅 정보를 사용 하 여 테스트 어셈블리를 작성 해야 하 고 연결된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
 중복 캐스팅을 수행하면 성능이 저하됩니다. 특히 간단한 반복 문에서 캐스팅이 수행될 때 더욱 그러합니다. 중복 된 명시적 캐스트 작업을 지역 변수에 캐스팅의 결과 저장 하 고 중복 캐스팅 작업 대신 지역 변수를 사용 합니다.

 하는 경우 C# `is` 연산자 실제 캐스팅을 수행 하려면 먼저 캐스트의 성공 여부를 테스트 하는 결과 테스트 하는 것이 좋습니다는 `as` 연산자 대신 합니다. 수행 되는 암시적 캐스트 작업 하지 않고 동일한 기능을 제공 합니다 `is` 연산자입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 캐스트 연산 수를 최소화 하는 메서드 구현을 수정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 성능이 중요 하지 않은 경우이 규칙에서 경고를 표시 하거나 규칙을 완전히 무시 해도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 C#을 사용 하 여 규칙을 위반 하는 메서드를 보여 줍니다. `is` 연산자입니다. 대체 하 여 규칙을 충족 하는 두 번째 메서드는 `is` 연산자의 결과 대 한 테스트를 사용 하 여는 `as` 두 반복 당 캐스트 작업 수가 감소 하는 연산자가 있습니다.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 메서드를 보여 줍니다 `start_Click`, 여러 중복 된 명시적 캐스팅을 설정 하는, 규칙을 위반 하는 메서드는이 있는 `reset_Click`, 캐스팅을 지역 변수에 저장 하 여 규칙을 충족 하는 합니다.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>참고 항목
 [as](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
