---
title: 'CA2204: 리터럴 철자가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a08cb7cee2af51ade4b94dbf675ff83d7da456e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142513"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: 리터럴의 맞춤법이 정확해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 매개 변수 또는 지역화 된 문자열 및 리터럴 문자열을 필요로 하는 속성에는 리터럴 문자열을 사용 하는 메서드가 전달에 Microsoft 맞춤법 검사 라이브러리에서 인식 하지 못하는 단어가 하나 이상 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 매개 변수 또는 경우에 속성 값으로 전달 되는 리터럴 문자열을 검사 하는이 규칙 또는 다음 경우 중 더 그렇습니다.

- <xref:System.ComponentModel.LocalizableAttribute> 매개 변수 또는 속성의 특성은 설정을 true로 합니다.

- "Text", "Message" 또는 "캡션"를 포함 하는 매개 변수 또는 속성 이름입니다.

- Console.Write 또는 Console.WriteLine 메서드에 전달 되는 문자열 매개 변수의 이름이 "value" 또는 "format"입니다.

  이 규칙 복합 단어를 토큰화 리터럴 문자열을 구문 분석 하 고 각 단어/토큰의 맞춤법을 검사 합니다. 구문 분석 알고리즘에 대 한 자세한 내용은 [CA1704: 식별자에는 정확한 철자를 사용 해야](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)합니다.

  기본적으로 영어 (en) 버전의 맞춤법 검사기 사용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 단어의 철자를 수정 하거나 사용자 지정 사전에 단어를 추가 합니다. 사용자 지정 사전을 사용 하는 방법에 대 한 정보를 참조 하세요. [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md)합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 올바르게 맞춤법이 단어는 새 소프트웨어 라이브러리에 필요한 학습 곡선을 줄어듭니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1704: 식별자에는 정확한 철자를 사용 해야](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: 리소스 문자열에는 정확한 철자를 사용 해야](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
