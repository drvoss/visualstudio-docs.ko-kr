---
title: 'CA2004: GC.KeepAlive에 대한 호출을 제거하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c495357b837c4ae10d4dfe1e25237d6caaefcc4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233107"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: GC.KeepAlive에 대한 호출을 제거하세요.

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|범주|Microsoft.Reliability|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
클래스는 `SafeHandle` 를 사용 하지만 여전히에 `GC.KeepAlive`대 한 호출을 포함 합니다.

## <a name="rule-description"></a>규칙 설명
사용으로 `SafeHandle` 변환 하는 경우 (개체)에 대 `GC.KeepAlive` 한 모든 호출을 제거 합니다. 이 경우 클래스는 종료 자가 없지만이에 대 `GC.KeepAlive`한 OS 핸들을 완료 `SafeHandle` 하기 위해를 사용 한다고 가정 하 여를 호출할 필요가 없습니다.  에 대 `GC.KeepAlive` 한 호출을 종료 하는 비용은 성능으로 측정 되는 것 보다 무시할 수 있지만,에 대 `GC.KeepAlive` 한 호출이 더 이상 존재 하지 않을 수 있는 수명 문제를 해결 하는 데 필요 하거나 더 이상 존재 하지 않는 것으로 인식 됩니다. 관리.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
에 대 한 `GC.KeepAlive`호출을 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
클래스에서 사용으로 `SafeHandle` 변환 하기 위해 기술적으로 정확 하지 않은 경우에만이 경고를 표시 하지 않을 수 있습니다.