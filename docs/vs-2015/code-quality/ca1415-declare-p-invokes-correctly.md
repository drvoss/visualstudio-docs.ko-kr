---
title: 'CA1415: P-invoke를 올바르게 선언 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 57482b720b1a7801fc75e06a5eb5d05d3b1a1417
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691853"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invoke를 올바르게 선언하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경 아님-매개 변수를 선언 하는 P/Invoke 어셈블리 외부에 노출 되지 않는 경우 주요-매개 변수를 선언 하는 P/Invoke 어셈블리 외부에서 볼 수 있는 경우입니다.|

## <a name="cause"></a>원인
 플랫폼 호출 메서드 잘못 선언 되었습니다.

## <a name="rule-description"></a>규칙 설명
 플랫폼 메서드가 관리 되지 않는 코드에 액세스를 호출 하 고 사용 하 여 정의 되는 `Declare` 키워드 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 또는 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. 플랫폼 호출 메서드 선언을 OVERLAPPED 구조체 매개 변수에 대 한 포인터가 있는 Win32 함수를 대상으로 하는 아니며 해당 관리 되는 매개 변수에 대 한 포인터에 대 한이 규칙의에서는 현재는 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 구조입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 플랫폼 제대로 선언 메서드를 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 플랫폼 규칙을 위반 하 고 규칙을 충족 하는 메서드를 호출 합니다.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>참고 항목
 [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
