---
title: 'CA1404: P / Invoke 후에 바로 GetLastError를 호출 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e33c724d2cebb9423f2e475d95bf42ac5e2cc966
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200310"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: P/Invoke 다음에 바로 GetLastError를 호출하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 호출 합니다 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> 메서드 또는 해당 Win32 `GetLastError` 함수 및 호출 바로 앞에 오는 플랫폼 아닙니다 메서드를 호출 합니다.

## <a name="rule-description"></a>규칙 설명
 플랫폼 메서드가 관리 되지 않는 코드에 액세스를 호출 하 고 사용 하 여 정의 되는 `Declare` 키워드 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 또는 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 특성. 일반적으로 실패 하면 관리 되지 않는 함수 호출을 Win32 `SetLastError` 오류와 관련 된 오류 코드를 설정 하는 함수입니다. 실패 한 함수의 호출자가 호출 Win32 `GetLastError` 오류 코드를 검색 하 여 오류의 원인을 확인 하는 함수입니다. 오류 코드는 스레드별 기준 유지 관리 되며 다음 호출 하 여 덮어씁니다 `SetLastError`합니다. 관리 코드 오류 코드를 호출 하 여 검색할 수 후 실패 한 플랫폼 호출 메서드를 호출 합니다 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 메서드. 오류 코드를 다른 관리 되는 클래스 라이브러리 메서드에서 내부 호출을 통해 덮어쓸 수 있으므로 합니다 `GetLastError` 또는 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 플랫폼 호출 메서드 호출 후에 즉시 메서드를 호출 해야 합니다.

 다음에 대 한 호출을 무시 하는 규칙 플랫폼에 대 한 호출 간에 발생 하는 경우 관리 되는 멤버 메서드 및 호출 호출 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>합니다. 이러한 멤버 오류를 변경 하지 마십시오 메서드 호출을 호출 코드 및 일부 플랫폼의 성공 여부를 결정 하는 데 유용 합니다.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면에 대 한 호출을 이동 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 플랫폼에 대 한 호출 바로 뒤에 오도록 메서드를 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 플랫폼 간에 코드에 메서드 호출 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다 및 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 메서드 호출 명시적 또는 암시적으로 인해 오류 코드를 변경 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 메서드 및 규칙을 충족 하는 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1060: P/Invoke를 NativeMethods 클래스로 이동](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke 진입점 있어야 합니다.](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke을 표시 해야 합니다.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: 관리 되는 Win32 api를 사용 합니다.](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
