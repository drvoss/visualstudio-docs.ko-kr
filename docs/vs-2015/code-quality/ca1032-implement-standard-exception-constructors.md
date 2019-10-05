---
title: 'CA1032: 표준 예외 생성자를 구현 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c59da56304a5d1d8f2cca7eaf886fd5ebc37f8ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205845"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: 표준 예외 생성자를 구현하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 형식 확장 <xref:System.Exception?displayProperty=fullName> 및 모든 필수 생성자를 선언 하지는 않습니다.

## <a name="rule-description"></a>규칙 설명
 예외 형식에는 다음 생성자를 구현 해야 합니다.

- public NewException()

- 공용 NewException(string)

- 공용 NewException (문자열, 예외)

- protected 또는 private NewException (SerializationInfo, StreamingContext)

  이들 생성자 집합을 전부 제공하지 못하면 예외를 제대로 처리하기 어려울 수 있습니다. 예를 들어, 서명이 있는 생성자 `NewException(string, Exception)` 다른 예외에 의해 발생 하는 예외를 만드는 데 사용 됩니다. 만들고 인스턴스의 내부 (중첩 된) 예외를 포함 하는 사용자 지정 예외를 throw 할 수 없습니다.이 생성자가 없으면 관리 되는 코드는 이러한 상황에서 수행 해야 합니다. 세 가지 예외는 첫 번째 생성자는 규칙에 따라 공용입니다. 네 번째 생성자는 unsealed 클래스에서 보호 되어 봉인 된 클래스에서 private입니다. 자세한 내용은 참조 하세요. [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 예외에 누락 된 생성자를 추가 하 고 올바른 액세스 가능성을 갖는지 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 Public 생성자에 대 한 다른 액세스 수준을 사용 하 여 위반이 발생 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 예외 형식 및 올바르게 구현 되는 예외 형식을 포함 합니다.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
