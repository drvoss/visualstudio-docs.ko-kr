---
title: 'CA2119: Private 인터페이스를 만족 하는 메서드를 봉인 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 56b08d1b842e65e1c1c29a7409813c314cbf014d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687271"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: private 인터페이스를 만족하는 메서드를 봉인하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 상속할 수 있는 공용 형식의 재정의 가능한 메서드 구현을 제공 된 `internal` (`Friend` Visual basic에서) 인터페이스입니다.

## <a name="rule-description"></a>규칙 설명
 인터페이스 메서드를 구현 하는 형식으로 변경할 수 없는 public 접근성이 있어야 합니다. 내부 인터페이스에는 인터페이스를 정의 하는 어셈블리 외부에 구현 되도록 디자인 되지 않은 계약을 만듭니다. 사용 하 여 내부 인터페이스 메서드를 구현 하는 공용 형식 합니다 `virtual` (`Overridable` Visual basic에서) 한정자 메서드를 어셈블리 외부에 있는 파생된 된 형식에서 재정의할 수 있습니다. 정의 하는 어셈블리의 두 번째 형식 메서드를 호출 하는 내부 전용 계약 예상 하는 경우에 외부 어셈블리에서 재정의 된 메서드를 실행 하는 대신 하는 경우 동작 손상 될 수 있습니다. 이 보안 취약점을 만듭니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 다음 중 하나를 사용 하 여 어셈블리 외부에서 재정의 되지 않도록:

- 선언 형식을 `sealed` (`NotInheritable` Visual basic에서).

- 선언 형식의 액세스 가능성을 변경할 `internal` (`Friend` Visual basic에서).

- 선언 형식에서 모든 public 생성자를 제거 합니다.

- 사용 하지 않고 메서드를 구현 합니다 `virtual` 한정자입니다.

- 메서드를 명시적으로 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 경고를 표시 하지 않아도 안전 합니다 신중 하 게 검토 한 후 보안 문제가 있는 경우에 규칙 어셈블리 외부에서 메서드가 재정의 된 경우에 악용 될 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 형식 `BaseImplementation`,이 규칙을 위반 하 합니다.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>예제
 다음 예제에서는 이전 예제의 가상 메서드 구현을 이용합니다.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>참고 항목
 [인터페이스](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [인터페이스](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
