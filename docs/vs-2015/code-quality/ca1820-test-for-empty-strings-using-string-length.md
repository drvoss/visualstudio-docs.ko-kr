---
title: 'CA1820: 문자열 길이를 사용 하 여 빈 문자열을 테스트 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6711dac907de2777cf892b20269fec7e99d3bd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657498"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: 문자열 길이를 사용하여 문자열이 비었는지 테스트하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|범주|Microsoft 성능|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 @No__t_0를 사용 하 여 문자열을 빈 문자열과 비교 합니다.

## <a name="rule-description"></a>규칙 설명
 @No__t_0 속성이 나 <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> 메서드를 사용 하 여 문자열을 비교 하는 것이 <xref:System.Object.Equals%2A>를 사용 하는 것 보다 훨씬 빠릅니다. 이는 <xref:System.Object.Equals%2A> <xref:System.String.IsNullOrEmpty%2A> 또는 <xref:System.String.Length%2A> 속성 값을 검색 하 고 0과 비교 하기 위해 실행 되는 명령 수보다 훨씬 더 많은 MSIL 명령을 실행 하기 때문입니다.

 @No__t_0 및 <xref:System.String.Length%2A> = = 0은 null 문자열에 대해 다르게 동작 함을 인식 해야 합니다. Null 문자열에 대 한 <xref:System.String.Length%2A> 속성 값을 가져오려고 하면 공용 언어 런타임에서 <xref:System.NullReferenceException?displayProperty=fullName>을 throw 합니다. Null 문자열과 빈 문자열을 비교 하는 경우 공용 언어 런타임에서는 예외를 throw 하지 않습니다. 비교는 `false`을 반환 합니다. Null에 대 한 테스트는 이러한 두 방법의 상대적 성능에 크게 영향을 주지 않습니다. @No__t_0를 대상으로 지정 하는 경우 <xref:System.String.IsNullOrEmpty%2A> 메서드를 사용 합니다. 그렇지 않으면 가능 하면 항상 <xref:System.String.Length%2A> = = 비교를 사용 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.String.Length%2A> 속성을 사용 하 여 비교를 변경 하 고 null 문자열을 테스트 합니다. @No__t_0를 대상으로 하는 경우 <xref:System.String.IsNullOrEmpty%2A> 메서드를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 성능이 문제가 아니면이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예에서는 빈 문자열을 검색 하는 데 사용 되는 다양 한 기술을 보여 줍니다.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
