---
title: 'CA1413: COM 노출 값 형식에 public이 아닌 필드 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 59ca3c5f53dee43bdd73eb706f03792458e71698
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691131"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: COM 노출 값 형식에 public이 아닌 필드를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 표시 구성 요소 개체 모델 (COM)에 표시 되는 값 형식에 public이 아닌 인스턴스 필드를 선언 합니다.

## <a name="rule-description"></a>규칙 설명
 public이 아니며 값 형식이 COM에 노출되는 인스턴스 필드는 COM 클라이언트에서 볼 수 있습니다. 노출 되지 않아야 합니다 또는 의도 하지 않은 디자인 또는 보안 영향을 줄 수 있는 정보에 대 한 필드의 내용을 검토 합니다.

 기본적으로 모든 공용 값 형식은 COM에 표시 됩니다. 그러나 가양성을 줄이기 위해이 규칙에 명시적으로 지정할 형식의 COM 표시를 해야 합니다. 포함 하는 어셈블리 표시 되어야 합니다는 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 로 설정 `false` 형식으로 표시 되어야 합니다 및는 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 로 설정 `true`.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하 고 숨겨진 필드를 유지 하려면 참조 형식으로 값 형식을 변경 하거나 제거 합니다 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 형식 특성입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 노출 된 필드의 허용 되는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1407: COM 노출 형식에 정적 멤버를 방지 합니다.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: ComVisibleAttribute로 어셈블리 표시](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>참고 항목
 [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [상호 운용할.NET 형식의 정규화](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
