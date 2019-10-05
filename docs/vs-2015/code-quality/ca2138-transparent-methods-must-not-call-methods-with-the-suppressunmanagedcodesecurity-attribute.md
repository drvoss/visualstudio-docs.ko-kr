---
title: 'CA2138: 투명 한 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용 하 여 메서드를 호출 해서는 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4e9a9e10f928efe6bcff6fb3d49c1b1cd7b1bd1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154288"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: 투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 로 표시 된 메서드를 호출 하는 보안 투명 메서드는 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 특성입니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 사용 하 여 예를 들어 네이티브 코드를 직접 호출 하는 모든 투명 메서드에 P/Invoke를 통해 (플랫폼 호출)를 호출 합니다. 표시 된 P/Invoke와 COM interop 메서드는 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 호출 메서드에 대해 수행 되는 LinkDemand에서 결과 특성입니다. 보안 투명 코드는 LinkDemands를 충족할 수 없는, 때문에 코드도 호출할 수 없습니다는 SuppressUnmanagedCodeSecurity 특성을 사용 하 여 표시 된 메서드나 SuppressUnmanagedCodeSecurity 특성을 사용 하 여 표시 된 클래스의 메서드. 메서드는 실패 하거나 요청 전체 요청으로 변환 됩니다.

 이 규칙 위반을 <xref:System.MethodAccessException> 수준 2 보안 투명성 모델에 대 한 완전 요청이 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 수준 1 투명성 모델에서.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 제거 합니다 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 특성 및 메서드를 사용 하 여 표시 합니다 <xref:System.Security.SecurityCriticalAttribute> 또는 <xref:System.Security.SecuritySafeCriticalAttribute> 특성입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
