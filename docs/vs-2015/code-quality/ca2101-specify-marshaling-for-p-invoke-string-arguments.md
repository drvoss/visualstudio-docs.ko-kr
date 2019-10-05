---
title: 'CA2101: P / Invoke 문자열 인수에 대해 마샬링을 지정 하십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 11916609f2efa9c0b6e208548ba51795bd276015
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154397"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 플랫폼 호출 멤버가 부분적으로 신뢰할 수 있는 호출자에 대 한 문자열 매개 변수가 있으며 문자열을 명시적으로 마샬링하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 유니코드에서 ANSI로 변환 하는 경우 가능성이 일부 유니코드 문자를 특정 ANSI 코드 페이지로 나타낼 수 있습니다. *최적된 매핑을* 표현할 수 없는 문자에 대 한 문자를 대체 하 여이 문제를 해결 하려고 합니다. 선택 되는 문자를 제어할 수 없으므로이 기능을 사용할 잠재적인 보안 취약점을 발생할 수 있습니다. 예를 들어, 악성 코드가 의도적으로 발생할 같은 파일 시스템에 대 한 특수 문자를 변환 하는 특정 코드 페이지에서 찾을 수 없는 문자를 포함 하는 유니코드 문자열 '..' 또는 '/'. 또한 특수 문자에 대 한 보안 검사 사용 문자열을 ANSI로 변환 되기 전에 발생 빈도 note 합니다.

 최적 매핑은 WChar 공간 (mb) 관리 되지 않는 변환에 대 한 기본값입니다. 가장 적합된 한 매핑, 명시적으로 해제 하지 않은 코드는이 문제로 인해를 악용할 수 있는 보안 취약점으로 인 한을 포함할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 명시적으로 문자열 데이터 형식을 맞게 마샬링하십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 위반을 해결 하는 방법을 보여 주는 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
