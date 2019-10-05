---
title: 메모리 사용량 분석
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 124b792e134b31a5964c8f202c7870a58bc0878b
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128245"
---
# <a name="analyze-memory-usage"></a>메모리 사용량 분석
디버거 통합 **메모리 사용량** 진단 도구를 사용하여 메모리 누수 및 비효율적인 메모리를 찾습니다. 메모리 사용량 도구를 통해 관리되는 메모리 및 네이티브 메모리 힙의 *스냅샷* 을 하나 이상 만들 수 있습니다. .NET, ASP.NET, 네이티브 또는 혼합 모드(.NET 및 네이티브) 앱의 스냅샷을 수집할 수 있습니다.

- 단일 스냅샷을 분석하여 메모리 사용에 대한 개체 형식의 상대적 영향을 파악하고 앱에서 메모리를 비효율적으로 사용하는 코드를 찾을 수 있습니다.

- 또한 앱의 스냅샷 두 개를 비교(diff)하여 코드에서 시간에 따라 메모리 사용이 늘어나는 영역을 찾을 수 있습니다.

자세한 내용은 [메모리 사용 분석](../profiling/memory-usage.md) 자습서를 참조하세요.  현재 .NET Core 앱의 메모리 사용량을 측정하려면 디버거를 연결해서 도구를 사용해야 합니다. 다른 관리되는 앱과 네이티브 앱의 경우 디버거를 연결하거나 연결하지 않고 도구를 사용할 수 있습니다.

Windows 7 이상에서 디버거 없이 프로파일링 도구를 사용할 수 있습니다. Windows 8 이상에서는 디버거(**진단 도구** 창)를 포함한 프로파일링 도구를 실행해야 합니다.

## <a name="blogs-and-videos"></a>블로그 및 동영상

[디버그하는 동안 CPU와 메모리 분석](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ 블로그: Visual C++ 2015의 메모리 프로파일링](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>참고 항목

- [Visual Studio의 프로파일링](../profiling/index.yml)
- [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)