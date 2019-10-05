---
title: 'CA1406: Visual Basic 6 클라이언트에서 Int64 인수를 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7cf2fc4e9160f44f51ac565619bd8d52bff8b22b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705714"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Visual Basic 6 클라이언트에서는 Int64 인수를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 특히 표시 구성 요소 개체 모델 (COM)에 표시 되는 형식 멤버를 해당는 선언 된 <xref:System.Int64?displayProperty=fullName> 인수.

## <a name="rule-description"></a>규칙 설명
 Visual Basic 6 COM 클라이언트는 64 비트 정수를 액세스할 수 없습니다.

 기본적으로 다음은 COM에 표시: 어셈블리, public 형식, 공용 인스턴스 멤버를 공용 형식 및 공개 값 형식의 모든 멤버입니다. 그러나 가양성을 줄이기 위해이 규칙 하려면 명시적으로 지정 되어야; 형식의 COM 노출 여부 포함 하는 어셈블리 표시 되어야 합니다는 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 로 설정 `false` 형식으로 표시 되어야 합니다 및는 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 로 설정 `true`.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 매개 변수 값을 항상 32 비트 정수 계열로 표현할 수에 대 한이 규칙 위반 문제를 해결 하려면 매개 변수 유형을 변경 하 여 <xref:System.Int32?displayProperty=fullName>입니다. 매개 변수의 값을 32 비트 정수 표현 될 수 있습니다 보다 큰 경우 매개 변수 유형을 변경 하 여 <xref:System.Decimal?displayProperty=fullName>입니다. 둘 다 <xref:System.Single?displayProperty=fullName> 하 고 <xref:System.Double?displayProperty=fullName> 상위 범위에서 정밀도 떨어질는 <xref:System.Int64> 데이터 형식입니다. COM에 표시 되도록 멤버를 사용 하는 것이 아닙니다를 표시 하는 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 로 `false`합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 Visual Basic 6 COM 클라이언트 형식 액세스 하지 않음을 특정 경우에이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1413: COM 노출 값 형식에 public이 아닌 필드를 방지 합니다.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: COM 노출 형식에 정적 멤버를 방지 합니다.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: ComVisibleAttribute로 어셈블리 표시](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>참고 항목
 [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long 데이터 형식](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)
