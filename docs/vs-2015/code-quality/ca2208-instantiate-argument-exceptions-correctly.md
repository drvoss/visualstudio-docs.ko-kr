---
title: 'CA2208: 인수 예외를 올바르게 인스턴스화 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d7020563d7bcbc794a0d2980a8dcc77c0d98d0b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142540"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: 인수 예외를 올바르게 인스턴스화하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 가능한 원인은 다음과 같습니다.

- 즉, 또는 [System.ArgumentException] (에서 파생 된 예외 형식의 기본 (매개 변수가 없는) 생성자 호출<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->)를 선택합니다.

- 즉, 또는 [System.ArgumentException.]에서 파생 된 예외 형식의 매개 변수가 있는 생성자에 잘못 된 문자열 인수가 전달 (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>규칙 설명
 기본 생성자를 호출 하는 대신 더 의미 있는 예외 메시지를 제공할 수 있도록 생성자 오버 로드 중 하나를 호출 합니다. 예외 메시지는 개발자를 대상으로 하 고 수정 하거나 예외를 방지 하는 방법과 오류 조건을 명확 하 게 설명 해야 합니다.

 하나 및 두 개의 문자열 생성자의 시그니처에 <xref:System.ArgumentException> 파생된 형식을 기준으로 일치 하지 않습니다 하 고는 `message` 및 `paramName` 매개 변수입니다. 올바른 문자열 인수를 사용 하 여 이러한 생성자가 호출 했는지 확인 합니다. 시그니처는 다음과 같습니다.

 <xref:System.ArgumentException>(문자열 `message`)

 <xref:System.ArgumentException>(string `message`, 문자열 `paramName`)

 <xref:System.ArgumentNullException>(문자열 `paramName`)

 <xref:System.ArgumentNullException>(string `paramName`, 문자열 `message`)

 <xref:System.ArgumentOutOfRangeException>(문자열 `paramName`)

 <xref:System.ArgumentOutOfRangeException>(string `paramName`, 문자열 `message`)

 <xref:System.DuplicateWaitObjectException>(문자열 `parameterName`)

 <xref:System.DuplicateWaitObjectException>(string `parameterName`, 문자열 `message`)

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메시지, 매개 변수 이름, 또는 둘 다 사용 하는 생성자를 호출 하 고 인수는 형식에 대해 적절 한 있는지 <xref:System.ArgumentException> 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 올바른 문자열 인수를 사용 하 여 매개 변수화 된 생성자를 호출 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에는 ArgumentNullException 형식의 인스턴스를 올바르게 인스턴스화하는 생성자를 보여 줍니다.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>예제
 다음 예제에서는 생성자 인수를 전환 하 여 위의 위반 문제를 해결 합니다.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
