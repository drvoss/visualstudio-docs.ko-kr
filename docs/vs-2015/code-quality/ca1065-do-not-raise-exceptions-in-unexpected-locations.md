---
title: 'CA1065: 예기치 않은 위치에서 예외를 발생 하지 않습니다 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6c5a393c32d7f7182fc3226689e24d20a4cae1ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200399"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: 예기치 않은 위치에서 예외를 발생시키지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 예외를 throw하지 않아야 하는 메서드가 예외를 throw했습니다.

## <a name="rule-description"></a>규칙 설명
 예외를 throw 되지 않는 메서드를 다음과 같이 분류할 수 있습니다.

- 속성 Get 메서드

- 이벤트 접근자 메서드

- Equals 메서드

- GetHashCode 메서드

- ToString 메서드

- 정적 생성자

- 종료자

- Dispose 메서드

- 같음 연산자

- 암시적 캐스트 연산자

  다음 섹션에서는 이러한 메서드 형식에 설명 합니다.

### <a name="property-get-methods"></a>속성 Get 메서드
 속성은 기본적으로 스마트 필드입니다. 따라서은 최대한 필드 처럼 동작 해야 합니다. 예외를 throw 하지 않습니다 필드와 속성. 예외를 throw 하는 속성에 있는 경우에 메서드를 수행 하는 것이 좋습니다.

 다음 예외는 속성 get 메서드에서 throw 될 수 있습니다.

- <xref:System.InvalidOperationException?displayProperty=fullName> 및 모든 파생 버전 (포함 하 여 <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> 및 모든 파생 항목

- <xref:System.ArgumentException?displayProperty=fullName> (에서만 get 인덱싱됨)

- <xref:System.Collections.Generic.KeyNotFoundException> (에서만 get 인덱싱됨)

### <a name="event-accessor-methods"></a>이벤트 접근자 메서드
 이벤트 접근자에는 예외를 throw 하지 않는 간단한 작업 이어야 합니다. 이벤트 추가 또는 이벤트 처리기를 제거 하려고 할 때 예외를 throw 하지 해야 합니다.

 다음 예외는 이벤트 접근자에서는에서 throw 될 수 있습니다.

- <xref:System.InvalidOperationException?displayProperty=fullName> 및 모든 파생 버전 (포함 하 여 <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> 및 모든 파생 항목

- <xref:System.ArgumentException> 와 파생 클래스

### <a name="equals-methods"></a>Equals 메서드
 다음 **Equals** 메서드는 예외를 throw 하지 않아야 합니다.

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)

  **Equals** 메서드를 반환할지 `true` 또는 `false` 예외를 throw 하는 대신 합니다. 예를 들어, Equals 두 유형을 가지 므로 전달 되는 경우만 반환할 `false` throw 하는 대신는 <xref:System.ArgumentException>합니다.

### <a name="gethashcode-methods"></a>GetHashCode 메서드
 다음 **GetHashCode** 메서드 일반적으로 예외 throw 하지 않아야 합니다.

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** 항상 값을 반환 해야 합니다. 그렇지 않으면 해시 테이블에서 항목을 잃을 수 있습니다.

  버전의 **GetHashCode** 사용 하는 인수를 throw 할 수는 <xref:System.ArgumentException>합니다. 그러나 **Object.GetHashCode** 예외가 throw 되지 않습니다.

### <a name="tostring-methods"></a>ToString 메서드
 디버거를 사용 하 여 <xref:System.Object.ToString%2A?displayProperty=fullName> 문자열 형식의 개체에 대 한 정보를 표시 하는 데 있습니다. 따라서 **ToString** 개체의 상태를 변경 하지 않아야 하 고 예외를 throw 하지 않아야 합니다.

### <a name="static-constructors"></a>정적 생성자
 정적 생성자에서 예외를 throw 하면 형식을 현재 응용 프로그램 도메인에서 사용할 수 없게 됩니다. 정적 생성자에서 예외를 throw 하는 것에 대 한 좋은 이유 (예: 보안 문제) 해야 합니다.

### <a name="finalizers"></a>종료자
 하면 프로세스를 중지 하는 페일 패스트, CLR이 종료자에서 예외를 throw 합니다. 따라서 종료자에서 예외를 throw 항상 피해 야 합니다.

### <a name="dispose-methods"></a>Dispose 메서드
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 메서드는 예외를 throw 하지 해야 합니다. 정리 논리의 일부로 삭제 라고는 `finally` 절. 따라서 내에서 예외 처리에 추가할 사용자를 강제로 명시적으로 Dispose의 예외를 throw 합니다 `finally` 절.

 합니다 **dispose (false)** 코드 경로 거의 항상 종료자에서 호출 되어이 때문에 예외를 throw 하지 않아야 합니다.

### <a name="equality-operators--"></a>같음 연산자 (= =,! =)
 Equals 메서드 같은 같음 연산자는 반환 `true` 또는 `false` 하며 예외를 throw 하지 않아야 합니다.

### <a name="implicit-cast-operators"></a>암시적 캐스트 연산자
 사용자 종종 암시적 캐스트 연산자가 호출 된 인식 되지 않으면 암시적 캐스트 연산자에서 throw 된 예외가 완전히 예상 하지 않습니다. 따라서 예외가 암시적 캐스트 연산자에서 throw 되어야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 속성 getter에 대 한 논리를 변경 하거나 더 이상 예외를 throw 하거나 메서드로 속성 변경에 포함 되도록 합니다.

 모든 형식에 대해 다른 메서드 앞에 나열 된,이 더 이상 예외를 throw 해야 하는 논리를 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 위반 throw 된 예외 대신 예외 선언으로 인해 발생 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA2219: Exception 절에서 예외를 발생 하지 않습니다](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>참고 항목
 [디자인 경고](../code-quality/design-warnings.md)
