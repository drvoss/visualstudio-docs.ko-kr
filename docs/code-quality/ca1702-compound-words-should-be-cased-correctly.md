---
title: 'CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5480d3dde926dfe31b018a5cd0b1ea6a5813063b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234330"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|범주|Microsoft.Naming|
|주요 변경 내용|중단-어셈블리에서 발생 한 경우<br /><br /> 형식 매개 변수에 대해 발생 하는 경우에는 중단 되지 않습니다.|

## <a name="cause"></a>원인

식별자 이름에 여러 개의 단어가 포함되어 있으며 이 중 적어도 하나의 단어가 대/소문자를 정확하게 사용하지 않은 복합 단어인 것 같습니다.

## <a name="rule-description"></a>규칙 설명

식별자의 이름은 대/소문자를 기준으로 하는 단어로 분할 됩니다. Microsoft 맞춤법 검사 라이브러리에서 연속 된 두 단어 조합을 확인 합니다. 인식 되는 경우 식별자는 규칙 위반을 생성 합니다. 위반을 야기 하는 복합 단어의 예로는 "CheckSum" 및 "MultiPart"가 있으며, 각각 "Checksum" 및 "Multipart"의 대/소문자를 지정 해야 합니다. 이전의 일반적인 사용으로 인해 규칙에 몇 가지 예외가 기본적으로 제공 되며, "도구 모음" 및 "파일 이름"과 같이 여러 개의 단일 단어가 플래그 지정 됩니다 (이 경우 "도구 모음" 및 "파일 이름").

명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

대/소문자를 올바르게 변경 하려면 이름을 변경 합니다.

## <a name="language"></a>언어

맞춤법 검사기는 현재 영어 기반 문화권 사전에 대해서만 확인 합니다. **CodeAnalysisCulture** 요소를 추가 하 여 프로젝트 파일에서 프로젝트의 문화권을 변경할 수 있습니다.

예:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 문화권을 영어 기반 문화권 이외의 값으로 설정 하면이 코드 분석 규칙이 자동으로 사용 되지 않습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

복합 단어의 두 부분을 맞춤법 사전에서 인식 하 고 두 단어를 사용 하는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙

- [CA1701: 리소스 문자열 복합 단어는 대/소문자를 올바르게 지정 해야 합니다.](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: 식별자의 대/소문자를 올바르게 지정 해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: 식별자는 대/소문자가 달라 야 합니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>참고 항목

- [명명 지침](/dotnet/standard/design-guidelines/naming-guidelines)
- [대/소문자 표기법](/dotnet/standard/design-guidelines/capitalization-conventions)