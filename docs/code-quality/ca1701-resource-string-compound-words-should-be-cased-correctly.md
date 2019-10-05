---
title: 'CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed5ae8c0845755fe626e7e801f500389f9263cf5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234358"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|범주|Microsoft.Naming|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

리소스 문자열에는 대/소문자를 올바르게 표시 하지 않는 복합 단어가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명

리소스 문자열의 각 단어는 대/소문자를 기반으로 하는 토큰으로 분할 됩니다. Microsoft 맞춤법 검사 라이브러리에서는 연속된 각 두 토큰의 조합을 검사합니다. 규칙 위반이 인식되면 단어에서 규칙 위반을 작성합니다. 위반을 야기 하는 복합 단어의 예로는 "CheckSum" 및 "MultiPart"가 있으며, 각각 "Checksum" 및 "Multipart"의 대/소문자를 지정 해야 합니다. 이전의 일반적인 사용으로 인해 몇 가지 예외가 규칙에 기본 제공 되 고, "도구 모음" 및 "파일 이름"과 같이 여러 개의 단어에 플래그가 지정 되며,이는 서로 다른 두 단어로만 대/소문자를 지정 해야 합니다. 이 예제에서는 "도구 모음" 및 "파일 이름"에 플래그가 지정 됩니다.

명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

단어의 대/소문자를 정확 하 게 변경 합니다.

## <a name="change-the-dictionary-language"></a>사전 언어 변경

기본적으로 영어 (en) 버전의 맞춤법 검사기가 사용 됩니다. 맞춤법 검사기의 언어를 변경 하려는 경우 *AssemblyInfo.cs* 또는 *AssemblyInfo* 파일에 다음 특성 중 하나를 추가 하 여이 작업을 수행할 수 있습니다.

- 리소스가 <xref:System.Reflection.AssemblyCultureAttribute> 위성 어셈블리에 있는 경우를 사용 하 여 문화권을 지정 합니다.
- 리소스가 <xref:System.Resources.NeutralResourcesLanguageAttribute> 코드와 동일한 어셈블리에 있는 경우를 사용 하 여 어셈블리의 *중립 문화권* 을 지정 합니다.

> [!IMPORTANT]
> 문화권을 영어 기반 문화권 이외의 값으로 설정 하면이 코드 분석 규칙이 자동으로 사용 되지 않습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

복합 단어의 두 부분을 맞춤법 사전에서 인식 하 고 의도는 두 개의 단어를 사용 하는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

맞춤법 검사기의 사용자 지정 사전에 복합 단어를 추가할 수도 있습니다. 사용자 지정 사전의 단어는 위반을 발생 시 키 지 않습니다. 자세한 내용은 [방법: 코드 분석 사전을](../code-quality/how-to-customize-the-code-analysis-dictionary.md)사용자 지정 합니다.

## <a name="related-rules"></a>관련 규칙

- [CA1702: 복합 단어는 대/소문자를 올바르게 지정 해야 합니다.](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: 식별자의 대/소문자를 올바르게 지정 해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: 식별자는 대/소문자가 달라 야 합니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>참고 항목

- [대/소문자 표기법](/dotnet/standard/design-guidelines/capitalization-conventions)
- [명명 지침](/dotnet/standard/design-guidelines/naming-guidelines)