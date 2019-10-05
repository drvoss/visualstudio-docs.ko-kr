---
title: 자동 기능 일시 중단
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe86e085e50dc0e72c00b7bbe7a313e689e0ee5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62571535"
---
# <a name="automatic-feature-suspension"></a>자동 기능 일시 중단

사용 가능한 시스템 메모리 200MB 이하로 떨어지면 Visual Studio 코드 편집기에서 다음과 같은 메시지가 표시 됩니다.

![전체 솔루션 분석을 일시 중단 하는 경고 텍스트](../code-quality/media/fsa_alert.png)

Visual Studio에서 메모리 부족 상태를 감지 하면 자동으로 안정적인 상태를 유지 해야 하는 데 특정 고급 기능을 중단 합니다. Visual Studio 계속 이전 처럼 작동 하지만 해당 성능이 저하 됩니다.

메모리 부족 조건에는 다음 작업이 수행:

- Visual C# 및 Visual Basic에 대 한 전체 솔루션 분석 사용 되지 않습니다.

- [가비지 수집](/dotnet/standard/garbage-collection/index) 시각적 개체에 대해 짧은 대기 시간 모드 (GC) C# 및 Visual Basic을 사용할 수 없습니다.

- Visual Studio 캐시가 플러시됩니다.

## <a name="improve-visual-studio-performance"></a>Visual Studio 성능 향상

팁과 요령 대형 솔루션 또는 메모리 부족 상태를 처리할 때 Visual Studio 성능을 개선 하는 방법에 대해서 [대형 솔루션에 대 한 성능 고려 사항](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)합니다.

## <a name="full-solution-analysis-suspended"></a>일시 중단 하는 전체 솔루션 분석

기본적으로 전체 솔루션 분석 Visual Basic의 경우 사용 하도록 설정 되어 Visual C#을 사용할 수 없습니다. 그러나 메모리 부족 상태에서 전체 솔루션 분석 자동으로 비활성화 됩니다 Visual Basic 및 Visual C#, 옵션 대화 상자에서 해당 설정에 관계 없이 합니다. 선택 하 여 전체 솔루션 분석 다시 활성화할 수 있지만 합니다 **다시 사용 하도록 설정** 표시 되 면을 선택 하 여 표시줄 정보 단추를 **전체 솔루션 분석 사용** 옵션 대화 상자에서 확인란 Visual Studio를 다시 시작 합니다. 옵션 대화 상자는 항상 현재 전체 솔루션 분석 설정을 표시합니다. 자세한 내용은 [방법: 전체 솔루션 분석 활성화 및 비활성화](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)합니다.

## <a name="gc-low-latency-disabled"></a>GC 지연율이 낮은 사용 하지 않도록 설정

GC 짧은 대기 시간 모드를 다시 사용 하려면 Visual Studio를 다시 시작 합니다. 기본적으로 Visual Studio 입력 내용을 GC 작업 차단 하지 않는지 확인 하려면 텍스트를 입력할 때마다 GC 짧은 대기 시간 모드를 사용 합니다. 그러나 메모리 부족 상태로 인해 자동 일시 중단 경고를 표시 하려면 Visual Studio, GC 지연율이 낮은 모드는 해당 세션에 대 한 비활성화 됩니다. Visual Studio를 다시 시작 하면 기본 GC 동작에 다시 사용 하도록 설정 합니다. 자세한 내용은 <xref:System.Runtime.GCLatencyMode>을 참조하세요.

## <a name="visual-studio-caches-flushed"></a>Visual Studio 캐시 플러시

현재 개발 세션을 계속 하거나 Visual Studio를 다시 시작, 모든 Visual Studio 캐시를 비울 바로, 있지만 다시 채워야 시작 합니다. 다음 기능에 대 한 캐시를 포함 하는 캐시 플러시:

- 모든 참조 찾기

- 탐색

- 사용 하 여 추가

또한 Visual Studio의 내부 작업에 사용 되는 캐시도 지워집니다.

> [!NOTE]
> 자동 기능 일시 중단 경고를 세션별 기반이 아니라 솔루션 당 기준으로 한 번만 발생합니다. 이 Visual Basic에서 Visual C# (또는 반대로)로 전환 하 고 다른 메모리 부족 상태를 가져올 수 있습니다 가능한 자동 기능 일시 중단 경고를 다른 것을 의미 합니다.

## <a name="see-also"></a>참고자료

- [방법: 전체 솔루션 분석 활성화 및 비활성화](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [가비지 수집 기본 사항](/dotnet/standard/garbage-collection/fundamentals)
- [대규모 솔루션에 대 한 성능 고려 사항](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)