---
title: 'CA1303: 리터럴을 지역화 된 매개 변수를 전달 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fafcf113f5f40da3bcc4666778330865dcdfb84c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686804"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 문자열 리터럴을 전달 매개 변수로 생성자 또는 메서드에서 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 라이브러리 및는 문자열은 지역화 될 수 있어야 합니다.

 이 경고는 리터럴 문자열 매개 변수 또는 속성 값으로 전달 되 고 다음 경우 중 하나 이상의 참인 경우에 발생 합니다.

- <xref:System.ComponentModel.LocalizableAttribute> 매개 변수 또는 속성의 특성은 설정을 true로 합니다.

- "Text", "Message" 또는 "캡션"를 포함 하는 매개 변수 또는 속성 이름입니다.

- Console.Write 또는 Console.WriteLine 메서드에 전달 되는 문자열 매개 변수의 이름이 "value" 또는 "format"입니다.

## <a name="rule-description"></a>규칙 설명
 소스 코드에 포함 된 문자열 리터럴을 지역화 하기 어렵습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 리터럴 문자열의 인스턴스를 통해 검색 하는 문자열을 사용 하 여 대체 된 <xref:System.Resources.ResourceManager> 클래스입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 코드 라이브러리를 지역화 하지 않는 경우 또는 최종 사용자 또는 코드 라이브러리를 사용 하는 개발자는 문자열이 노출 되지 않는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

 사용자가 전달 되지 않아야 지역화 된 문자열 매개 변수 또는 라는 속성의 이름을 바꾸거나 또는 이러한 항목을 조건부로 표시 되는 메서드에 노이즈를 제거할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 범위를 벗어났습니다. 해당 두 인수 중 하나의 경우 예외가 throw 되는 메서드를 보여 줍니다. 첫 번째 인수에 대 한 예외 생성자에는이 규칙을 위반 하는 리터럴 문자열로 전달 됩니다. 두 번째 인수에 대 한 생성자를 제대로 전달 됩니다 검색할 문자열을 <xref:System.Resources.ResourceManager>입니다.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>참고 항목
 [데스크톱 앱의 리소스](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
