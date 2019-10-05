---
title: 'CA1403: 자동 레이아웃 형식은 COM 노출이면 안 됩니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef7b693a881aaa1457004c84968ebc80936fc2b2
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714856"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: 자동 레이아웃 형식은 COM 노출이면 안 됩니다.

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인

구성 요소 개체 모델 (COM) 표시 값 형식으로 표시 됩니다는 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 특성이 설정 <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명

<xref:System.Runtime.InteropServices.LayoutKind> 레이아웃 형식은 공용 언어 런타임에 의해 관리 됩니다. 이러한 형식의 레이아웃 버전의.NET 특정 레이아웃이 필요한 COM 클라이언트는 달라질 수 있습니다. 경우는 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 특성을 지정 하지 않으면 합니다 C#, Visual Basic의 경우 및 C++ 컴파일러 지정 [LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) 값 형식에 대 한 합니다.

그렇지 않은 경우에 표시 하지 않는 한 모든 public, 제네릭이 아닌 형식은 COM에 노출 하 고 모든 public이 아닌 제네릭 형식과 COM에 표시 되지 않습니다. 그러나 가양성을 줄이기 위해이 규칙에 명시적으로 지정할 형식의 COM 표시를 해야 합니다. 포함 하는 어셈블리 표시 되어야 합니다는 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 로 설정 `false` 형식으로 표시 되어야 합니다 및는 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 로 설정 `true`.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면의 값을 변경 합니다 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 특성을 [LayoutKind.Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) 하거나 [LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), com 형식 숨기기 또는

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우

이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제

다음 예제에서는 규칙을 위반 하는 형식을 규칙을 충족 하는 형식을 보여 줍니다.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>관련된 규칙

[CA1408: AutoDual ClassInterfaceType을 사용 하지 마십시오](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>참고자료

- [상호 운용할.NET 형식의 정규화](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [관리 되지 않는 코드 상호 운용](/dotnet/framework/interop/index)