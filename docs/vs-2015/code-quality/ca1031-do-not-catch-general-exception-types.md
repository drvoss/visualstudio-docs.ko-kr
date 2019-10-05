---
title: 'CA1031: 일반적인 예외 형식을 catch 하지 마십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4588a949b4b6439c3f76270b0bcdab9cd52c23d9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431222"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: 일반적인 예외 형식을 catch하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 와 같은 일반 예외 <xref:System.Exception?displayProperty=fullName> 또는 <xref:System.SystemException?displayProperty=fullName> 에서 발견 되는 `catch` 문이나와 같은 일반 catch 절 `catch()` 사용 됩니다.

## <a name="rule-description"></a>규칙 설명
 일반 예외는 catch하면 안 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 보다 구체적인 예외를 catch 하거나의 마지막 문으로 일반 예외를 다시 throw 된 `catch` 블록입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 일반적인 예외 형식을 catch 할 라이브러리 사용자 로부터 런타임 문제를 숨길 수 있습니다 및 디버깅을 더 어렵게 만들 수 있습니다.

> [!NOTE]
> [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)]부터 시작해서, CLR(공용 언어 런타임)은 관리 코드에서 처리되어야 하는 [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]의 액세스 위반과 같이 운영 체제 및 관리 코드에서 발생하는 손상된 상태 예외를 더 이상 제공하지 않습니다. 응용 프로그램을 컴파일할 경우 합니다 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 이상 버전 및 유지 관리 손상 된 상태 예외 처리를 적용할 수 있습니다는 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 손상 된 상태 예외를 처리 하는 메서드 특성입니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 형식 및 올바르게 구현 하는 형식을 `catch` 블록입니다.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2200: 스택 정보를 유지 하도록 다시 throw](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
