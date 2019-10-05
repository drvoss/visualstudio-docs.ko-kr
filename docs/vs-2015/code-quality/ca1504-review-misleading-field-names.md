---
title: 'CA1504: 필드 이름에 잘못 된 검토 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2203e99974e5f232e8c90badef7c28921b971cdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191208"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: 잘못된 필드 이름을 검토하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|범주|Microsoft.Maintainability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 인스턴스 필드의 이름이 "s_" 또는 이름으로 시작 된 `static` (`Shared` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 필드 "m_"로 시작 합니다.

## <a name="rule-description"></a>규칙 설명
 필드 이름은 "s_"로 시작 하는 많은 사용자가 정적 데이터를 사용 하 여 연결 됩니다. 마찬가지로, "m_"로 시작 하는 필드 이름은 (멤버) 인스턴스 데이터와 연결 됩니다. 쉽고 유지 관리 코드에 대 한 이름을 일반적으로 사용 되는 규칙을 따라야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 적절 한 접두사를 사용 하 여 필드를 이름을 바꿉니다. 또는 추가 하거나 제거 하 여 현재 접미사를 사용 하 여 필드를 확인 합니다 `static` 한정자입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.
