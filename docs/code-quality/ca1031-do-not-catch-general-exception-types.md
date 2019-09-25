---
title: 'CA1031: 일반적인 예외 형식을 catch하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236060"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: 일반적인 예외 형식을 catch하지 마세요.

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|범주|Microsoft.Design|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
또는 <xref:System.Exception?displayProperty=fullName> `catch` `catch()` 와 같은 일반 예외는 문에 catch 되거나와 같은 일반 catch 절이 사용 됩니다. <xref:System.SystemException?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
일반 예외는 catch하면 안 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 보다 구체적인 예외를 catch 하거나 일반 예외를 `catch` 블록의 마지막 문으로 다시 throw 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙에서는 경고를 표시해야 합니다. 일반적인 예외 형식을 catch 하면 라이브러리 사용자의 런타임 문제를 숨기고 디버깅을 더 어렵게 만들 수 있습니다.

> [!NOTE]
> .NET Framework 4부터 CLR (공용 언어 런타임)은 관리 코드에서 처리 하기 위해의 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]액세스 위반과 같은 운영 체제 및 관리 코드에서 발생 하는 손상 된 상태 예외를 더 이상 제공 하지 않습니다. .NET Framework 4 이상 버전에서 응용 프로그램을 컴파일하고 손상 된 상태 예외 처리를 유지 하려는 경우 손상 된 상태 예외를 처리 하는 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 메서드에 특성을 적용할 수 있습니다.

## <a name="example"></a>예제
다음 예제에서는이 규칙을 위반 하는 형식과 `catch` 블록을 올바르게 구현 하는 형식을 보여 줍니다.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>관련 규칙
[CA2200: 스택 정보를 유지 하도록 다시 throw](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)