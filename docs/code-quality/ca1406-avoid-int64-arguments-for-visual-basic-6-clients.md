---
title: 'CA1406: Visual Basic 6 클라이언트에서는 Int64 인수를 사용하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a8b1ea389c37dc63a9fe7366208a2a3028efb8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234807"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Visual Basic 6 클라이언트에서는 Int64 인수를 사용하지 마세요.

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|범주|Microsoft.Interoperability|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
COM (구성 요소 개체 모델)에 표시 되도록 특별히 표시 된 형식은 <xref:System.Int64?displayProperty=fullName> 인수를 사용 하는 멤버를 선언 합니다.

## <a name="rule-description"></a>규칙 설명
Visual Basic 6 COM 클라이언트는 64 비트 정수를 액세스할 수 없습니다.

기본적으로 다음은 COM에 표시 됩니다. 어셈블리, public 형식, public 형식의 공용 인스턴스 멤버 및 public 값 형식의 모든 멤버입니다. 그러나 가양성을 줄이기 위해이 규칙을 사용 하려면 형식에 대 한 COM 표시 여부를 명시적으로 명시 해야 합니다. 포함 하 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 는 어셈블리는로 `false` 설정 된로 표시 되어야 하 고 형식은로 <xref:System.Runtime.InteropServices.ComVisibleAttribute> `true`설정 된로 표시 되어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
값이 항상 32 비트 정수 계열로 표현 될 수 있는 매개 변수에 대 한이 규칙 위반 문제를 해결 하려면 매개 변수 형식을로 <xref:System.Int32?displayProperty=fullName>변경 합니다. 매개 변수 값이 32 비트 정수 계열로 표현할 수 있는 것 보다 클 수 있는 경우 매개 변수 형식을로 <xref:System.Decimal?displayProperty=fullName>변경 합니다. <xref:System.Int64> 및 <xref:System.Single?displayProperty=fullName> 는모두데이터형식의상위범위에서전체자릿수를잃게됩니다.<xref:System.Double?displayProperty=fullName> 멤버가 COM에 표시 되지 않는 경우를로 <xref:System.Runtime.InteropServices.ComVisibleAttribute> `false`설정 하 여 표시 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
Visual Basic 6 COM 클라이언트에서 형식에 액세스 하지 않는 것이 확실 한 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>관련 규칙
[CA1413: COM 노출 값 형식에 public이 아닌 필드를 사용 하지 마십시오.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: COM 노출 형식에 정적 멤버를 사용 하지 마십시오.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: ComVisibleAttribute로 어셈블리 표시](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>참고 항목

- [비관리 코드와의 상호 운용](/dotnet/framework/interop/index)
- [Long 데이터 형식](/dotnet/visual-basic/language-reference/data-types/long-data-type)