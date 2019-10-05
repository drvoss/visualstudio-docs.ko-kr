---
title: 'CA2230: 가변 인수로 params를 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b833f520c574c32f90ff1ec5e20a9671184b78a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685106"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: 가변 인수로 params를 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|범주|Microsoft.Usage|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 public 또는 protected 메서드를 사용 하는 포함 된 `VarArgs` 호출 규칙입니다.

## <a name="rule-description"></a>규칙 설명
 `VarArgs` 가변 개수의 매개 변수를 사용 하는 특정 메서드 정의 사용 하 여 호출 규칙이 사용 됩니다. 사용 하는 메서드는 `VarArgs` 공용 언어 사양 (CLS) 규격이 아닙니다 호출 규칙 및 프로그래밍 언어에서 액세스할 수 없습니다.

 C#에서는 합니다 `VarArgs` 메서드의 매개 변수 목록을 사용 하 여 종료 될 때 호출 규칙이 사용 됩니다는 `__arglist` 키워드입니다. Visual Basic을 지원 하지 않습니다 합니다 `VarArgs` 호출 규칙 및 시각적 개체 C++ 타원을 사용 하는 관리 되지 않는 코드 에서만에서 사용할 수 있습니다 `...` 표기법입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 C#에서이 규칙 위반을 해결 하려면 사용 합니다 [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) 키워드 대신 `__arglist`합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 두 가지 방법, 규칙을 위반 하는 하나 및 규칙을 충족 하는 것을 보여 줍니다.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [언어 독립성 및 언어 독립적 구성 요소](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
