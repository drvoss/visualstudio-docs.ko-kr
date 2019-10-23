---
title: 'CA1403: 자동 레이아웃 형식은 COM 노출 이어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5f39540cb23d86dda4244604da8a9ff764594e11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661331"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: 자동 레이아웃 형식은 COM 노출이면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 COM (구성 요소 개체 모델)에 표시 되는 값 형식은 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 특성이 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>로 설정 된 상태로 표시 됩니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Runtime.InteropServices.LayoutKind> 레이아웃 형식은 공용 언어 런타임에 의해 관리 됩니다. 이러한 형식의 레이아웃은 특정 레이아웃이 요구 되는 COM 클라이언트를 중단 하는 .NET Framework 버전 간에 변경 될 수 있습니다. @No__t_0 특성을 지정 하지 않으면, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 및 C# C++ 컴파일러는 값 형식에 대 한 <xref:System.Runtime.InteropServices.LayoutKind> 레이아웃을 지정 합니다.

 달리 표시 되지 않는 한 모든 public 제네릭이 아닌 형식이 COM에 표시 됩니다. public이 아닌 모든 및 제네릭 형식은 COM에 표시 되지 않습니다. 그러나 가양성을 줄이기 위해이 규칙을 사용 하려면 형식에 대 한 COM 표시 여부를 명시적으로 명시 해야 합니다. 포함 하는 어셈블리는 `false`로 설정 된 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>로 표시 되어야 하 고 <xref:System.Runtime.InteropServices.ComVisibleAttribute> `true`로 설정 된 형식으로 표시 되어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 특성의 값을 <xref:System.Runtime.InteropServices.LayoutKind> 또는 <xref:System.Runtime.InteropServices.LayoutKind>로 변경 하거나 COM에 형식을 표시 하지 않도록 설정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식 및 규칙을 충족 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1408: AutoDual Classinterfacetype.none ](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) 사용 안 함

## <a name="see-also"></a>관련 항목:
 [비관리 코드와](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) 상호 운용 하기 위해 [클래스 인터페이스의](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [정규화 된 .net 형식](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) 소개
