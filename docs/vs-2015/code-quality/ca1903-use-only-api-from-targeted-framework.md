---
title: 'CA1903: 대상된 프레임 워크에서 API만 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 146563dfa358367e7c22f8ad37564b85d64eaf1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189087"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: 대상 프레임워크의 API만 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 최신 설명서를 참조 하세요. [CA1903: 대상된 프레임 워크에서 API만 사용 하 여](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework)입니다.  
  
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|범주|Microsoft.Portability|  
|변경 수준|주요-외부에서 표시 되는 멤버 또는 형식의 서명에 대해 발생 한 경우입니다.<br /><br /> 주요 변경 아님-메서드 본문에서 발생 한 경우|  
  
## <a name="cause"></a>원인  
 멤버 또는 형식이 프로젝트의 대상된 프레임 워크를 사용 하 여 포함 되지 않은 서비스 팩에 도입 된 멤버 또는 형식이 사용 됩니다.  
  
## <a name="rule-description"></a>규칙 설명  
 새 멤버 및 유형이.NET Framework 2.0 서비스 팩 1 및 2,.NET Framework 3.0 서비스 팩 1 및 2 및.NET Framework 3.5 서비스 팩 1에 포함 되었습니다. .NET Framework의 주 버전을 대상으로 하는 프로젝트에서 이러한 종속성 새 Api 걸릴 실수로 수 있습니다. 이 종속성을 방지 하려면이 규칙은 프로젝트의 대상 프레임 워크를 사용 하 여 기본적으로 포함 되지 않은 형식과 모든 새 멤버를 사용할 경우 발생 합니다.  
  
 **대상 프레임 워크 및 서비스 팩 종속성**  
  
|||  
|-|-|  
|대상 프레임 워크|에 도입 된 멤버를 사용할 경우 발생|  
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|해당 사항 없음|  
  
 프로젝트의 대상 프레임 워크를 변경 하려면을 참조 하세요 [특정.NET Framework 버전 대상 지정](../ide/targeting-a-specific-dotnet-framework-version.md)합니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 서비스 팩에 대 한 종속성을 제거 하려면 새 멤버 또는 형식의 모든 사용을 제거 합니다. 의도적인 종속성 인 경우 경고를 억제 또는이 규칙을 해제 합니다.  
  
## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우  
 지정 된 서비스 팩에 대 한 정밀한 종속성이 없는 경우에이 규칙에서 경고를 표시 하지 마십시오. 이런 경우 응용 프로그램은이 서비스 팩이 설치 되지 않은 시스템에서 실행에 실패할 수 있습니다. 경고를 억제 하거나 의도적인 종속성 인 경우이 규칙을 해제 합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 DateTimeOffset 에서만.NET 2.0 서비스 팩 1에서 사용할 수 있는 형식을 사용 하는 클래스를 보여 줍니다. 이 예제에서는.NET Framework 2.0가 프로젝트 속성의 대상 프레임 워크 드롭다운 목록에서 선택 되어 있는지 필요 합니다.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>예제  
 다음 예제에서는 날짜/시간 형식을 사용 하 여 DateTimeOffset 형식의 사용을 대체 하 여 앞에서 설명한 위반 문제를 해결 합니다.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>관련 항목  
 [이식성 경고](../code-quality/portability-warnings.md)   
 [특정 대상 .NET Framework 버전 지정](../ide/targeting-a-specific-dotnet-framework-version.md)
