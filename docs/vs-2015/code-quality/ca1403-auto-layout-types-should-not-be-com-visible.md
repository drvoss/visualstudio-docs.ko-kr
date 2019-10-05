---
title: 'CA1403: 자동 레이아웃 형식은 com 노출 이면 안 | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2420582ab342948d7774e1bb9e4b5947f44f8d2b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695436"
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
 구성 요소 개체 모델 (COM) 표시 값 형식으로 표시 됩니다는 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 특성이 설정 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Runtime.InteropServices.LayoutKind> 레이아웃 형식은 공용 언어 런타임에 의해 관리 됩니다. 이러한 형식의 레이아웃은 특정 레이아웃이 필요한 COM 클라이언트는.NET Framework의 버전 간에 변경 수 있습니다. 경우는 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 특성을 지정 하지 않으면를 C#, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], 및 C++ 컴파일러를 지정 합니다 <xref:System.Runtime.InteropServices.LayoutKind> 값 형식에 대 한 레이아웃 합니다.

 그렇지 않은 경우에 표시 하지 않는 한 모든 공용 제네릭이 아닌 형식은 COM에 표시 되지만; 모든 public이 아닌 형식과 일반 COM에 표시 되지 않습니다. 그러나 가양성을 줄이기 위해이 규칙 하려면 명시적으로 지정 되어야; 형식의 COM 노출 여부 포함 하는 어셈블리 표시 되어야 합니다는 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 로 설정 `false` 형식으로 표시 되어야 합니다 및는 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 로 설정 `true`.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면의 값을 변경 합니다 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 특성을 <xref:System.Runtime.InteropServices.LayoutKind> 또는 <xref:System.Runtime.InteropServices.LayoutKind>, com 형식 숨기기 또는

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 규칙을 충족 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1408: AutoDual ClassInterfaceType을 사용 하지 마십시오](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>참고 항목
 [클래스 인터페이스 소개](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [상호 운용할.NET 형식의 정규화](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
