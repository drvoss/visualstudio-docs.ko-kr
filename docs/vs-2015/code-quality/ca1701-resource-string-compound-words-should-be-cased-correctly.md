---
title: 'CA1701: 리소스 문자열 복합 단어는 대/소문자 올바르게 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38d8195baa540c2c212c71938b6266e28df49101
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683063"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|범주|Microsoft.Naming|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 리소스 문자열을 올바르게 대/소문자 표시 되지 않는 복합 단어를 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 리소스 문자열의 각 단어는 대/소문자를 기반으로 하는 토큰으로 분할 됩니다. Microsoft 맞춤법 검사 라이브러리에서는 연속된 각 두 토큰의 조합을 검사합니다. 규칙 위반이 인식되면 단어에서 규칙 위반을 작성합니다. 위반이 발생 하는 복합 단어의 예로 "CheckSum" 및 "MultiPart"는 대/소문자 "Checksum" 및 "Multipart"로 각각를 들 수 있습니다. 이전 일반적인 사용량으로 인해 몇 가지 예외는 규칙으로 빌드되고 몇 가지 단어에 플래그가 지정 됩니다 "Toolbar" 및 "Filename" 두 개의 고유 단어가으로 대/소문자는. 이 예제에서는 "ToolBar" 및 "FileName" 플래그가 지정 됩니다.

 명명 규칙은 공통 된 모양을 라이브러리에 대 한 해당 공용 언어 런타임을 대상으로 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 대 한 필수 항목이 며 관리 코드 개발의 전문 지식을 가진 사람이 라이브러리를 개발 하는 고객 신뢰도 증가 하는 학습 곡선을 줄어듭니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 올바르게 소문자 단어를 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 복합 단어의 두 파트 맞춤법 사전에서 인식 되 고 두 단어를 사용 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

 맞춤법 검사기에 대 한 사용자 지정 사전에 복합 단어를 추가할 수도 있습니다. 사용자 지정 사전에서 단어 위반이 발생 하지 않습니다. 자세한 내용은 [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md)합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1702: 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: 식별자에는 올바르게 표기를 사용 해야](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 식별자 대/소문자만 달라 야 합니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>참고 항목
 [대/소문자 표기법](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [명명 지침](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
