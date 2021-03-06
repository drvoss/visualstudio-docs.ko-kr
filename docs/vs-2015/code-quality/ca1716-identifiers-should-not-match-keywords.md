---
title: ': 식별자 ca1716 키워드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 000e28642a10c565e525b2714eed0d7abaca9340
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858877"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: 식별자는 키워드와 달라야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|범주|Microsoft.Naming|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 네임 스페이스, 형식 또는 가상 또는 인터페이스 멤버의 이름에는 프로그래밍 언어로 예약된 된 키워드와 일치합니다.

## <a name="rule-description"></a>규칙 설명
 네임 스페이스, 형식에 대 한 식별자 및 가상 인터페이스 멤버는 공용 언어 런타임을 대상으로 하는 언어에서 정의 된 키워드와 일치 하 고 있습니다. 사용 되는 언어 및 키워드에 따라 컴파일러 오류와 모호성이 라이브러리를 사용 하 여 어려워질 수 있습니다.

 이 규칙은 다음 언어의 키워드를 확인합니다.

- Visual Basic

- C#

- C++/CLI

  대/소문자 구분 비교는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 키워드 및 대/소문자 구분 비교는 다른 언어에 사용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 키워드 목록에 나타나지 않는 이름을 선택 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 식별자는 API의 사용자를 혼동 하지는 및에서 사용 가능한 모든 언어에서 사용 가능한 라이브러리는 확신 하는 경우이 규칙에서 경고를 표시 하지 않을 수는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]합니다.



