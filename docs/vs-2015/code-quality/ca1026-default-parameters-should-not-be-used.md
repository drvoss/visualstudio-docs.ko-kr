---
title: 'CA1026: 기본 매개 변수를 사용 하지 않아야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7c20bfce7dd7fe3b2e116b982408afa813ebab25
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704192"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: 기본 매개 변수를 사용하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식이 기본 매개 변수를 사용 하는 외부에 표시 되는 메서드를 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 기본 매개 변수를 사용 하는 메서드를 사용할 수에서 CLS 공용 언어 사양 (); 그러나 CLS 컴파일러를 이러한 매개 변수에 할당 된 값을 무시할 수 있습니다. 기본 매개 변수 값을 무시 하는 컴파일러에 대 한 작성 된 코드는 각 기본 매개 변수에 대해 인수를 명시적으로 제공 해야 합니다. 프로그래밍 언어에서 원하는 동작을 유지 하려면 기본 매개 변수를 사용 하는 메서드는 기본 매개 변수를 제공 하는 메서드 오버 로드로 대체 되어야 합니다.

 컴파일러에 대 한 관리 되는 확장에 대 한 기본 매개 변수 값을 무시 C++ 관리 코드에 액세스 합니다. Visual Basic 컴파일러를 사용 하는 기본 매개 변수가 있는 메서드를 지원 합니다 [선택 사항](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) 키워드입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 기본 매개 변수를 제공 하는 메서드 오버 로드를 사용 하 여 기본 매개 변수를 사용 하는 메서드를 대체 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 기본 매개 변수를 사용 하는 메서드 및 해당 기능을 제공 하는 오버 로드 된 메서드를 보여 줍니다.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1025: 반복 인수를 배열로 바꾸십시오.](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>참고 항목
 [언어 독립성 및 언어 독립적 구성 요소](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
