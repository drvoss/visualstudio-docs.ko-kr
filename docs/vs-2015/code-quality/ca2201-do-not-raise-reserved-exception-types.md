---
title: 'CA2201: 예약 된 예외 형식을 발생 시 키 지 않는 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 580a021a85d1211932c248ddc925a49e95e1cf13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142565"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: 예약된 예외 형식을 발생시키지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|범주|Microsoft.Usage|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 메서드는 너무 일반적 또는 런타임에서 예약 된 예외 형식을 발생 시킵니다.

## <a name="rule-description"></a>규칙 설명
 사용자에 게 충분 한 정보를 제공 하는 일반 너무 다음 예외 형식은 다음과 같습니다.

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  예외 유형은 예약 되어 있으므로 공용 언어 런타임만에서 throw 되어야 합니다.

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **일반 예외를 Throw 하지 않습니다**

  와 같은 일반 예외 유형을 throw 하는 경우 <xref:System.Exception> 또는 <xref:System.SystemException> 소비자를 강제로 라이브러리 또는 프레임 워크에서 예외를 처리 하는 방법을 알지는 알 수 없는 예외를 포함 합니다.

  대신 framework에서는 이미 존재 하는 많은 파생된 형식을 throw 또는에서 파생 되는 고유한 형식을 만들 <xref:System.Exception>합니다.

  **특정 예외를 throw 합니다.**

  다음 표에서 매개 변수 및 매개 변수를 값 매개 변수를 포함 하 여 속성의 set 접근자의 유효성을 검사할 때 throw 하는 예외:

|매개 변수 설명|예외|
|---------------------------|---------------|
|`null` 참조|<xref:System.ArgumentNullException?displayProperty=fullName>|
|값 (예: 컬렉션 또는 목록의 인덱스)의 허용된 범위를 벗어납니다|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|잘못 된 `enum` 값|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|메서드의 매개 변수 사양에 맞지 않는 형식이 포함 되어 있습니다 (형식 문자열과 같은 `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|유효 하지 않음|<xref:System.ArgumentException?displayProperty=fullName>|

 작업을 개체 throw의 현재 상태에 대 한 유효하지 없는 경우 <xref:System.InvalidOperationException?displayProperty=fullName>

 삭제 된 개체에서 작업을 수행 하면 throw <xref:System.ObjectDisposedException?displayProperty=fullName>

 작업은 지원 되지 않는 경우 (예: 재정의 된 **Stream.Write** 읽기용으로 열을 Stream에서) throw <xref:System.NotSupportedException?displayProperty=fullName>

 (예: 명시적 캐스트 연산자 오버 로드) 오버플로가 변환으로 인해 throw <xref:System.OverflowException?displayProperty=fullName>

 다른 모든 상황에서 파생 되는 고유한 형식을 만드는 것이 좋습니다. <xref:System.Exception> 해당 예외를 throw 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 예약 된 형식 중 하나가 아닌 특정 형식으로 throw 된 예외 유형의 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1031: 일반적인 예외 형식을 catch 하지 마십시오.](../code-quality/ca1031-do-not-catch-general-exception-types.md)
