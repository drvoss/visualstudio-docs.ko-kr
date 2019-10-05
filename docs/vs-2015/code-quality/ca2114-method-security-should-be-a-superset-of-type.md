---
title: 'CA2114: 메서드 보안은 형식의 상위 집합 이어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b1a360ee4ad35fd48a46f6d866912a05a584a54c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687310"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: 메서드 보안은 형식의 상위 집합이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식에 선언적 보안 및 해당 메서드 중 하나에 동일한 보안 작업에 대 한 선언적 보안 및 보안 작업은 없습니다 [링크 요구가](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) 하거나 [상속 요청](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), 권한과 메서드에서 검사 권한 하위 집합이 없는 형식으로 선택 합니다.

## <a name="rule-description"></a>규칙 설명
 메서드 모두 동일한 동작에 대해 메서드 수준과 형식 수준의 선언적 보안 없어야 합니다. 두 개의 검사 결합 되지 않습니다. 메서드 수준 요청에만 적용 됩니다. 예를 들어 권한을 요구 하는 형식을 `X`, 및 권한을 요구 하는 방법 중 하나 `Y`, 코드 권한이 없는 `X` 메서드를 실행 하 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 두 작업이 필요한 지 확인 하도록 코드를 검토 합니다. 두 작업이 필요한 경우 메서드 수준 동작 형식 수준에서 지정 된 보안 포함 되는지 확인 합니다. 예를 들어 권한을 요구 하는 형식을 `X`, 및 권한을 요청 해야 `Y`, 메서드를 명시적으로 요청 해야 `X` 및 `Y`합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 메서드는 형식에서 지정한 보안 필요가 없는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다. 그러나이 일반적인 시나리오가 되지 않으며 신중 하 게 설계 검토에 대 한 필요성을 나타낼 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반의 위험을 보여 주기 위해 환경 권한을 사용 합니다. 이 예제에서는 응용 프로그램 코드는 형식에 필요한 사용 권한 거부 하기 전에 보안 된 형식의 인스턴스를 만듭니다. 위협 현실적인 시나리오에서는 응용 프로그램에는 개체의 인스턴스를 가져올 다른 방법이 필요 합니다.

 다음 예에서 라이브러리 요구 사항 형식에 대 한 권한을 읽고 쓰는 메서드에 대 한 사용 권한.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램 코드를 사용 하는 형식 수준 보안 요구 사항을 충족 하지도 메서드를 호출 하 여 라이브러리의 취약점으로 인 한을 보여줍니다.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **[모든 권한] 개인 정보: 6/16/1964 오전 12시: 00**
 **[(유형별 요구) 쓰기 권한이 없음] 개인 정보: 6/16/1964 오전 12시: 00**
 **[읽기 권한 (메서드에서 요구) 없음] 개인 정보에 액세스할 수 없습니다. 요청이 실패 했습니다.**
## <a name="see-also"></a>참고 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [상속 요청이](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
