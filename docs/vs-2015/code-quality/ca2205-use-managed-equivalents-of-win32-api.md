---
title: 'CA2205: 관리 되는 Win32 api를 사용 하 여 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2da7faabb05d2f6eaf2ec345f9bae19401953093
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142553"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Win32 API의 동일한 관리형 기능을 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 플랫폼 호출 메서드가 정의 되었고 이와 동일한 기능을 사용 하 여 메서드를 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 라이브러리입니다.

## <a name="rule-description"></a>규칙 설명
 플랫폼 호출 메서드는 관리 되지 않는 DLL 함수를 호출 하는 데 사용 되 고 사용 하 여 정의 됩니다는 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 특성 또는 `Declare` Visual basic에서 키워드입니다. 잘못 정의 된 플랫폼 호출 메서드 이름이 잘못 지정 된 함수에 잘못 된 매개 변수 및 반환 값 데이터 형식 및 호출 규칙 및 문자 등 잘못 된 필드 사양 매핑 같은 문제로 인해 런타임 예외가 발생할 수 있습니다 이 옵션을 설정 합니다. 사용 가능한 경우 것이 일반적으로 간단 하 고 적은 오류를 정의 하 고 관리 되지 않는 메서드를 직접 호출 보다 해당 관리 되는 메서드를 호출 하기 쉽습니다. 메서드를 호출 하는 플랫폼 호출 해결 해야 하는 추가적인 보안 문제가 발생할 수도 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 관리 되지 않는 함수에 대 한 호출을을 관리 되는 해당 호출으로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 제안된 된 대체 메서드가 필요한 기능을 제공 하지 않는 경우이 규칙에서 경고를 표시 합니다.

## <a name="example"></a>예제
 다음 예제에서는 플랫폼에 규칙을 위반 하는 메서드 정의 호출 합니다. 또한 플랫폼 호출 메서드를 호출 하 고 해당 하는 관리 되는 메서드 표시 됩니다.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1404: P/Invoke 다음에 바로 GetLastError를 호출 합니다.](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: P/Invoke를 NativeMethods 클래스로 이동](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke 진입점 있어야 합니다.](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke을 표시 해야 합니다.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
