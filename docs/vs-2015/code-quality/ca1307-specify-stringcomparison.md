---
title: 'CA1307: StringComparison 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 292e174feeb123c640306bc8ef3ffedd7e8847f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200345"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison 지정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 문자열 비교 작업을 설정 하지 않는 메서드 오버 로드를 사용 하는 <xref:System.StringComparison> 매개 변수입니다.

## <a name="rule-description"></a>규칙 설명
 대부분의 문자열 작업에 가장 중요 한는 <xref:System.String.Compare%2A> 및 <xref:System.String.Equals%2A> 받아들이는 오버 로드를 제공 하는 메서드를 <xref:System.StringComparison> 열거형 값을 매개 변수로 합니다.

 때마다는 오버 로드가 있으면 해당 사용을 <xref:System.StringComparison> 매개 변수를이 매개 변수를 사용 하지 않는 오버 로드 하는 대신 사용 해야 합니다. 이 매개 변수를 명시적으로 설정 하 여 코드 경우가 보다 명확 해지고 더 쉬워진 유지 관리 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 오버 로드를 문자열 비교 메서드를 변경 합니다 <xref:System.StringComparison> 열거형을 매개 변수로 합니다. 예를 들어: 변경 `String.Compare(str1, str2)` 에 `String.Compare(str1, str2, StringComparison.Ordinal)`입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 라이브러리 또는 응용 프로그램은 제한 된 로컬 사용자 이며 따라서 지역화 되지 않을 때이 규칙에서 경고를 표시 하지 않으려면 안전 합니다.

## <a name="see-also"></a>관련 항목
 [전역화 경고](../code-quality/globalization-warnings.md) [CA1309: 서 수 StringComparison 사용](../code-quality/ca1309-use-ordinal-stringcomparison.md)
