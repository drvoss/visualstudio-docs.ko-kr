---
title: 'CA1600: 유휴 상태 프로세스 우선 순위를 사용 하지 마십시오. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669290"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: 유휴 상태 프로세스 우선 순위를 사용하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|범주|Microsoft Mobility|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 이 규칙은 프로세스가 `ProcessPriorityClass.Idle`로 설정 된 경우에 발생 합니다.

## <a name="rule-description"></a>규칙 설명
 프로세스 우선 순위를 유휴 상태로 설정하지 마십시오. @No__t_0 있는 프로세스는 유휴 상태가 될 때 CPU를 차지 하므로 대기를 차단 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 프로세스를 `ProcessPriorityClass.BelowNormal` 설정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙은 유휴 프로세스 우선 순위가 필요한 경우에만 억제 해야 하며 이동성 고려 사항은 안전 하 게 무시할 수 있습니다.
