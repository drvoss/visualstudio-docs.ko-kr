---
title: 'CA1600: 유휴 프로세스 우선 순위를 사용하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 686929471ee8b6b5d1896f61bcbcd97a59135462
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234375"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: 유휴 프로세스 우선 순위를 사용하지 마세요.

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|범주|Microsoft.Mobility|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
이 규칙은 프로세스가로 설정 된 경우 `ProcessPriorityClass.Idle`에 발생 합니다.

## <a name="rule-description"></a>규칙 설명
프로세스 우선 순위를 유휴 상태로 설정하지 마십시오. 가 `System.Diagnostics.ProcessPriorityClass.Idle` 있는 프로세스는 유휴 상태가 될 때 CPU를 차지 하므로 대기를 차단 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
프로세스를로 `ProcessPriorityClass.BelowNormal`설정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
이 규칙은 유휴 프로세스 우선 순위가 필요한 경우에만 억제 해야 하며 이동성 고려 사항은 안전 하 게 무시할 수 있습니다.