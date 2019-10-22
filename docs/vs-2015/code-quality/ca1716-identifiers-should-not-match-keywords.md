---
title: 'CA1716: 식별자는 키워드와 일치 하지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f81aec5973d1915ba646c20c3b84186443678754
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669094"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: 식별자는 키워드와 달라야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 네임 스페이스, 형식 또는 viritual 또는 인터페이스 멤버의 이름이 프로그래밍 언어의 예약 키워드와 일치 합니다.

## <a name="rule-description"></a>규칙 설명
 네임 스페이스, 형식 및 가상 멤버와 인터페이스 멤버의 식별자는 공용 언어 런타임을 대상으로 하는 언어에서 정의 된 키워드와 일치 하면 안 됩니다. 사용 되는 언어 및 키워드에 따라 컴파일러 오류 및 모호성을 통해 라이브러리를 사용 하기 어려울 수 있습니다.

 이 규칙은 다음 언어로 된 키워드를 검사 합니다.

- Visual Basic

- C#

- C++/CLI

  대/소문자를 구분 하지 않는 비교는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 키워드에 사용 되 고 다른 언어에 대 한 대/소문자 구분 비교가 사용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 키워드 목록에 표시 되지 않는 이름을 선택 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 식별자가 API의 사용자를 혼동 하지 않고 라이브러리를 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 모든 사용 가능한 언어로 사용할 수 있다는 확신을 확신 하는 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.
