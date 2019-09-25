---
title: 'CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2700dc2ade7ba901f15f67045e3170e2bbb40ff8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235109"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|범주|Microsoft.Globalization|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

메서드는 문자열 리터럴을 .NET 생성자 또는 메서드에 대 한 매개 변수로 전달 합니다 .이 문자열은 지역화 가능 해야 합니다.

이 경고는 리터럴 문자열이 매개 변수 또는 속성에 값으로 전달 되 고 다음 중 하나 이상이 true 인 경우에 발생 합니다.

- 매개 변수 또는 속성의 특성이true로설정되어있습니다.<xref:System.ComponentModel.LocalizableAttribute>

- 매개 변수 또는 속성 이름에 "Text", "Message" 또는 "Caption"이 포함 되어 있습니다.

- 콘솔에 전달 되는 문자열 매개 변수의 이름입니다. Write 또는 Console. WriteLine 메서드는 "value" 또는 "format"입니다.

## <a name="rule-description"></a>규칙 설명

소스 코드에 포함 된 문자열 리터럴은 지역화 하기 어렵습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 문자열 리터럴을 <xref:System.Resources.ResourceManager> 클래스의 인스턴스를 통해 검색 된 문자열로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

코드 라이브러리가 지역화 되지 않거나 최종 사용자 또는 코드 라이브러리를 사용 하는 개발자에 게 문자열이 노출 되지 않은 경우에는이 규칙에서 경고를 표시 하지 않아도 됩니다.

사용자는 매개 변수 또는 속성의 이름을 변경 하거나 이러한 항목을 조건으로 표시 하 여 지역화 된 문자열을 전달 하면 안 되는 메서드에 대해 노이즈를 제거할 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 두 인수 중 하나가 범위를 벗어나는 경우 예외를 throw 하는 메서드를 보여 줍니다. 첫 번째 인수에 대해 예외 생성자는이 규칙을 위반 하는 리터럴 문자열로 전달 됩니다. 두 번째 인수의 경우 생성자는를 <xref:System.Resources.ResourceManager>통해 검색 된 문자열을 올바르게 전달 합니다.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>참고 항목

- [데스크톱 앱의 리소스](/dotnet/framework/resources/index)