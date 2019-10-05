---
title: 'CA1411: COM 등록 메서드는 나타나지 않아야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2d7bcaf5637be70174a3a337343d92b7b3705b46
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692036"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: COM 등록 메서드는 노출되면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 로 표시 된 메서드를 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 또는 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 특성은 외부에서 볼 수 있습니다.

## <a name="rule-description"></a>규칙 설명
 어셈블리 구성 요소 개체 모델 (COM)를 사용 하 여 등록 되 면 어셈블리에 각 COM 노출 형식에 대 한 레지스트리 항목이 추가 됩니다. 로 표시 되는 메서드를 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 및 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 특성 이라고 등록 및 등록 취소 프로세스 중 각각 이러한 형식의 등록 또는 등록 취소에 관련 된 사용자 코드를 실행 합니다. 이 코드를 이러한 프로세스가 외부 호출 되어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드의 접근성을 변경 `private` 나 `internal` (`Friend` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 두 가지 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1410: COM 등록 메서드는 일치 해야 합니다.](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [COM에 어셈블리를 등록](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (어셈블리 등록 도구)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
