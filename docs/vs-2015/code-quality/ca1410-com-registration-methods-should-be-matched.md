---
title: 'CA1410: COM 등록 메서드는 일치 해야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dd47aa57d128ec5f88f77036546476128aae39f5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692068"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: COM 등록 메서드는 일치해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 형식으로 표시 되는 메서드를 선언 합니다 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 특성으로 표시 되는 메서드를 선언 하지 않습니다 하지만 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 특성 또는 그 반대로 합니다.

## <a name="rule-description"></a>규칙 설명
 만들려는 구성 요소 개체 모델 (COM) 클라이언트용를 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식 형식을 먼저 등록 해야 합니다. 사용 가능한 경우로 표시 된 메서드는 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 특성 사용자 지정 코드를 실행 하는 등록 프로세스 동안 호출 됩니다. 로 표시 된 해당 메서드는 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 등록 메서드 작업을 되돌리기 위해 등록 프로세스 동안 특성 이라고 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 해당 등록 또는 등록 취소 메서드를 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다. 코드를 주석 처리 된 위반에 대 한 수정 프로그램을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1411: COM 등록 메서드를 표시 해야 합니다.](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [COM에 어셈블리를 등록](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (어셈블리 등록 도구)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
