---
title: 'CA1601: 전원 상태 변경을 방해 하는 타이머를 사용 하지 않는 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 228c95a8f0c3e1b9b1643e529e78f52f1e059bc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189258"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: 전원 상태 변경을 방해하는 타이머를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|범주|Microsoft.Mobility|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 타이머를 초당 여러 번 발생 하도록 설정 하는 간격을 있습니다.

## <a name="rule-description"></a>규칙 설명
 한 번 또는 1 보다 더 자주 발생 하는 타이머를 사용 하 여 보다 더 자주 폴링 되지 않습니다 초당 시간입니다. 정기적인 작업의 실행 빈도가 높아지면 CPU 사용률도 높아져 디스플레이 및 하드 디스크를 끄는 절전 유휴 타이머에 방해가 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 초당 1 개 미만의 번 발생 하도록 타이머 간격을 설정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 타이머를 초당 여러 번 발생 하는 것은 필수 및 이동성 고려 사항을 무시할 수는 경우에이 규칙을 표시 하지 않습니다.
