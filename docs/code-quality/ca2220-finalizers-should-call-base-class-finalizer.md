---
title: 'CA2220: 종료자는 기본 클래스 종료자를 호출해야 합니다.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c814324ac21017acf6a0182f7807b0a0878c8aca
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551209"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: 종료자는 기본 클래스 종료자를 호출해야 합니다.

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인

재정의 하는 형식을 <xref:System.Object.Finalize%2A?displayProperty=fullName> 호출 하지 않습니다는 <xref:System.Object.Finalize%2A> 해당 기본 클래스의 메서드.

## <a name="rule-description"></a>규칙 설명

종료는 상속 계층을 통해 전파되어야 합니다. 이 위해 형식은 해당 기본 클래스를 호출 해야 합니다 <xref:System.Object.Finalize%2A> 자체 내에서 메서드 <xref:System.Object.Finalize%2A> 메서드. C# 컴파일러는 기본 클래스 종료자에 대 한 호출을 자동으로 추가합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하는 기본 유형의 호출 <xref:System.Object.Finalize%2A> 메서드에서 사용자 <xref:System.Object.Finalize%2A> 메서드.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우

이 규칙에서는 경고를 표시해야 합니다. 공용 언어 런타임을 대상으로 하는 일부 컴파일러는 MSIL (Microsoft intermediate language)에 기본 유형의 종료자에 대 한 호출을 삽입 합니다. 이 규칙에서 경고를 보고 되 면 컴파일러 호출을 삽입 하지 않습니다 하 고 코드를 추가 해야 합니다.

## <a name="example"></a>예제

다음 Visual Basic 예제에서는 형식을 보여 줍니다 `TypeB` 올바르게 호출 하는 <xref:System.Object.Finalize%2A> 해당 기본 클래스의 메서드.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>참고자료

- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)