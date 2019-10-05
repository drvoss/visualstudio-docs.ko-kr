---
title: 'CA1302: 로캘별 문자열을 하드 코딩 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d52489ba25fe2c541d2d0329fcad61aef75350e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200418"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: 로캘별 문자열을 하드코드하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드는 특정 시스템 폴더의 경로 부분을 나타내는 문자열 리터럴을 사용 합니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> 특수 시스템 폴더를 참조 하는 멤버를 포함 하는 열거형입니다. 이러한 폴더의 위치는 다른 운영 체제에서 다른 값을 가질 수, 사용자 위치 중 일부를 변경할 수 및 위치는 지역화 합니다. 특수 폴더의 예로 "C:\WINDOWS\system32"는 시스템 폴더에 [!INCLUDE[winxp](../includes/winxp-md.md)] 있지만 "C:\WINNT\system32"에서 [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]합니다. 합니다 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> 연관 된 위치를 반환 하는 메서드를 <xref:System.Environment.SpecialFolder> 열거형입니다. 반환 되는 위치 <xref:System.Environment.GetFolderPath%2A> 지역화 되어 있고 현재 실행 중인 컴퓨터에 적합 합니다.

 이 규칙에서는 사용 하 여 검색 되는 폴더 경로 토큰화 합니다 <xref:System.Environment.GetFolderPath%2A> 별도 디렉터리 수준으로 메서드. 각 문자열 리터럴 토큰 비교 됩니다. 일치 하는 항목이 있으면 메서드 토큰을 사용 하 여 연결 된 시스템 위치를 가리키는 문자열을 구성 하 고 있는지 간주 됩니다. 이식성과 지역화를 사용 하 여는 <xref:System.Environment.GetFolderPath%2A> 문자열 리터럴을 사용 하는 대신 특수 시스템 폴더의 위치를 검색 하는 방법입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 사용 하 여 위치를 검색 합니다 <xref:System.Environment.GetFolderPath%2A> 메서드.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 연결 된 시스템 위치 중 하나를 참조 하려면 리터럴 문자열을 사용 하지 않는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다는 <xref:System.Environment.SpecialFolder> 열거형입니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙에서 세 개의 경고를 생성 하는 일반적인 응용 프로그램 데이터 폴더의 경로 빌드합니다. 예제를 사용 하 여 경로 검색 하는 다음으로 <xref:System.Environment.GetFolderPath%2A> 메서드.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1303: 리터럴을 지역화 된 매개 변수로 전달 하지 마십시오](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
