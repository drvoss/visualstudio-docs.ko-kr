---
title: 'CA1600: 유휴 프로세스 우선 순위를 사용 하지 않는 | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4002e17e3988ca3b449e141394ce762f95ffc78b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189305"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: 유휴 프로세스 우선 순위를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|범주|Microsoft.Mobility|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 이 규칙은 프로세스 설정 된 경우 `ProcessPriorityClass.Idle`합니다.

## <a name="rule-description"></a>규칙 설명
 프로세스 우선 순위를 유휴 상태로 설정하지 마십시오. 프로세스를 `System.Diagnostics.ProcessPriorityClass.Idle` 유휴, 고 블록이 대기 하는 경우에 CPU를 차지 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 프로세스로 `ProcessPriorityClass.BelowNormal`합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 유휴 프로세스 우선 순위 필수 항목이 며 이동성 고려 사항을 안전 하 게 무시할 수 있습니다 하는 경우에이 규칙을 표시 하지 않습니다.
