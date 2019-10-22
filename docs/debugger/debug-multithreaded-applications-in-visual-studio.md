---
title: 다중 스레드 응용 프로그램 디버그 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 668e95c340348eeb1fa509622aa44d99b65b6efc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431812"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio에서 다중 스레드 애플리케이션 디버그
스레드는 운영 체제에서 프로세서 시간을 부여 하는 일련의 지침입니다. 운영 체제에서 실행되는 모든 프로세스는 최소한 하나의 스레드로 구성됩니다. 프로세스에 스레드가 둘 이상인 경우를 다중 스레드라고 합니다.

다중 프로세서, 다중 코어 프로세서 또는 하이퍼스레딩 프로세스를 사용 하는 컴퓨터는 여러 개의 동시 스레드를 실행할 수 있습니다. 많은 스레드를 사용 하 여 병렬 처리를 수행 하면 프로그램 성능이 크게 향상 될 수 있지만 많은 스레드를 추적 하기 때문에 디버깅을 더 어렵게 만들 수도 있습니다.

다중 스레딩을 통해 새로운 유형의 잠재적 버그를 도입할 수 있습니다. 예를 들어 둘 이상의 스레드에서 같은 리소스에 액세스 해야 하지만 한 번에 한 스레드만 리소스에 안전 하 게 액세스할 수 있습니다. 한 번에 한 스레드만 리소스에 액세스할 수 있도록 하기 위해 일부 형태의 상호 제외가 필요 합니다. 상호 제외가 잘못 구현 된 경우 스레드가 실행 되지 않는 *교착 상태* 조건을 만들 수 있습니다. 교착 상태는 종종 디버그 하는 어려운 문제입니다.

## <a name="tools-for-debugging-multithreaded-apps"></a>다중 스레드 응용 프로그램 디버깅 도구

Visual Studio는 다중 스레드 응용 프로그램 디버깅에 사용할 다양 한 도구를 제공 합니다.

- 스레드의 **경우 스레드 디버깅** 을 위한 기본 도구는 스레드 창, 소스 창의 스레드 마커, **병렬 스택** 창, **병렬 조사식** 창 및 **디버그 위치** 도구 모음입니다. 에 대해 자세히 알아보려면 합니다 **스레드** 창 및 **디버그 위치** 도구 모음에서 참조 [연습: 스레드 창을 사용하여 디버그](../debugger/how-to-use-the-threads-window.md). **병렬 스택** 및 **병렬 조사식** 창을 사용 하는 방법에 대 한 자세한 내용은 [다중 스레드 응용 프로그램 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)을 참조 하세요. 두 항목 모두 스레드 마커를 사용 하는 방법을 보여 줍니다.

- [TPL (작업 병렬 라이브러리)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) 또는 [동시성 런타임](/cpp/parallel/concrt/concurrency-runtime/)를 사용 하는 코드의 경우 디버깅을 위한 기본 도구는 **병렬 스택** 창, **병렬 조사식** 창 및 **작업** 창 (도 지원 됨)입니다. JavaScript. 시작 하려면 [연습: 병렬 응용 프로그램 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md) 및 [연습: C++ AMP 응용 프로그램 디버깅](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)을 참조 하세요.

- GPU에서 스레드를 디버깅 하는 경우 기본 도구는 **Gpu 스레드** 창입니다. [방법: GPU 스레드 창 사용을](../debugger/how-to-use-the-gpu-threads-window.md)참조 하세요.

- 프로세스의 경우 기본 도구는 **프로세스에 연결** 대화 상자, **프로세스** 창 및 **디버그 위치** 도구 모음입니다.

Visual Studio는 또한 다중 스레드 응용 프로그램을 디버깅할 때 유용할 수 있는 강력한 중단점과 추적점을 제공 합니다. 중단점 조건 및 필터를 사용 하 여 개별 스레드에 중단점을 추가 합니다. 추적점을 사용 하면 중단 없이 프로그램 실행을 추적 하 여 교착 상태와 같은 문제를 연구할 수 있습니다. 자세한 내용은 [중단점 작업 및 추적점](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)을 참조 하세요.

사용자 인터페이스가 있는 다중 스레드 애플리케이션은 특히 디버깅하기 어려울 수 있습니다. 두 번째 컴퓨터에서 응용 프로그램을 실행 하 고 원격 디버깅을 사용 하는 것을 고려할 수 있습니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조 하세요.

## <a name="articles-about-debugging-multithreaded-apps"></a>다중 스레드 앱 디버깅에 대 한 문서

 [다중 스레드 응용 프로그램 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)

**병렬 스택** 창 및 **병렬 조사식** 창에서 기능을 강조 하는 스레드 디버깅 기능 둘러보기

 [스레드 및 프로세스 디버깅 도구](../debugger/debug-threads-and-processes.md)

스레드 및 프로세스 디버깅 도구에 대 한 기능을 나열 합니다.

 [여러 프로세스 디버그](../debugger/debug-multiple-processes.md)

여러 프로세스 디버깅 방법에 대해 설명합니다.

 [연습: 스레드 창을 사용하여 디버그](../debugger/how-to-use-the-threads-window.md)

**스레드** 창 및 **디버그 위치** 도구 모음을 사용 하는 방법을 보여 주는 연습입니다.

 [연습: 병렬 애플리케이션 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)

**병렬 스택** 및 **작업** 창을 사용 하는 방법을 보여 주는 연습입니다.

 [방법: 디버그 중 다른 스레드로 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md)

디버깅 컨텍스트를 다른 스레드로 전환 하는 여러 가지 방법

 [방법: 스레드에 플래그 지정 및 스레드의 플래그 해제](../debugger/how-to-flag-and-unflag-threads.md)

디버깅 도중 특별히 주의하려는 스레드를 표시하거나 플래그를 지정합니다.

 [방법: 고성능 클러스터에서 디버그](../debugger/how-to-debug-on-a-high-performance-cluster.md)

고성능 클러스터에서 실행되는 애플리케이션을 디버깅하는 방법을 보여 줍니다.

 [네이티브 코드의 스레드 디버깅 팁](../debugger/tips-for-debugging-threads-in-native-code.md)

네이티브 스레드를 디버깅하는 단순하지만 유용한 방법을 보여 줍니다.

 [방법: 네이티브 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-native-code.md)

**스레드** 창에 표시되는 스레드에 이름을 지정합니다.

 [방법: 관리 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-managed-code.md)

**스레드** 창에 표시되는 스레드에 이름을 지정합니다.

## <a name="see-also"></a>참조

- [중단점 사용](../debugger/using-breakpoints.md)
- [스레딩](/dotnet/standard/threading/index)
- [구성 요소에서 다중 스레딩](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [이전 코드에 대 한 다중 스레딩 지원](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [스레드 및 프로세스 디버그](../debugger/debug-threads-and-processes.md)
- [원격 디버깅](../debugger/remote-debugging.md)