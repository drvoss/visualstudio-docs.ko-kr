---
title: 'CA1724: 형식 이름은 네임 스페이스와 일치 하지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671591"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: 형식 이름은 네임스페이스와 달라야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식 이름은 대/소문자를 구분 하지 않는 비교에서 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 네임 스페이스 이름과 일치 합니다.

## <a name="rule-description"></a>규칙 설명
 형식 이름은 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 라이브러리에 정의된 네임스페이스의 이름과 같아서는 안 됩니다. 이 규칙을 위반하면 라이브러리의 유용성이 저하될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 @No__t_0 클래스 라이브러리 네임 스페이스의 이름과 일치 하지 않는 형식 이름을 선택 하십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 새 개발을 위해이 규칙에서 경고를 표시 하지 않아야 하는 알려진 시나리오가 발생 하지 않습니다. 경고를 표시 하지 않으려면 라이브러리의 사용자가 일치 하는 이름으로 혼동 될 수 있는 방법을 신중 하 게 고려해 야 합니다. 배송 라이브러리의 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.
