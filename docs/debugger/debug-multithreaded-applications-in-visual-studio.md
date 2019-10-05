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
ms.openlocfilehash: b3f2fc8b6acd38393cf9fefb1c5581ab4d1a0712
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852933"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio에서 다중 스레드 애플리케이션 디버그
스레드는 운영 체제가 프로세서 시간 권한을 부여 하는 명령 시퀀스입니다. 운영 체제에서 실행되는 모든 프로세스는 최소한 하나의 스레드로 구성됩니다. 프로세스에 스레드가 둘 이상인 경우를 다중 스레드라고 합니다.

다중 프로세서, 다중 코어 프로세서 또는 하이퍼스레드 프로세스를 사용 하 여 컴퓨터에는 여러 동시 스레드가 실행할 수 있습니다. 병렬 처리를 여러 스레드를 사용 하 여 프로그램 성능을 크게 향상할 수 있지만 될 수 있습니다도 디버깅 더 어려워질 스레드 수를 추적 하 고 있으므로.

다중 스레딩에는 새로운 유형의 잠재적인 버그 발생할 수 있습니다. 예를 들어 두 개 이상의 스레드가 동일한 리소스에 액세스 해야 할 수도 있지만 한 번에 하나의 스레드만 리소스에 안전 하 게 액세스할 수 있습니다. 특정 형태의 상호 제외는 하나의 스레드만 액세스 하는 리소스를 언제 든 지 있는지 확인 하는 데 필요한 경우 상호 제외가 잘못 구현 될 경우 만들 수는 *교착 상태* 어떠한 스레드도 실행 하는 조건입니다. 교착 상태는 대개 디버그 하기 어려운 문제입니다.

## <a name="tools-for-debugging-multithreaded-apps"></a>다중 스레드 응용된 프로그램 디버깅을 위한 도구

Visual Studio는 다중 스레드 응용된 프로그램 디버깅에 사용할 다양 한 도구를 제공 합니다.

- 스레드를 스레드 디버깅을 위한 기본 도구는 합니다 **스레드** 창, 소스 창의 스레드 마커를 **병렬 스택** 창 합니다 **병렬 조사식** 창 및 **디버그 위치** 도구 모음입니다. 에 대해 자세히 알아보려면 합니다 **스레드** 창 및 **디버그 위치** 도구 모음에서 참조 [연습: 스레드 창을 사용하여 디버그](../debugger/how-to-use-the-threads-window.md). 사용 하는 방법을 알아보려면 합니다 **병렬 스택** 및 **병렬 조사식** windows 참조 [다중 스레드 응용 프로그램 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)합니다. 두 항목에는 스레드 마커를 사용 하는 방법을 보여 줍니다.

- 사용 하는 코드에 대 한 합니다 [TPL 작업 병렬 라이브러리 ()](/dotnet/standard/parallel-programming/task-parallel-library-tpl) 또는 [동시성 런타임](/cpp/parallel/concrt/concurrency-runtime/), 디버깅을 위한 기본 도구를 **병렬 스택** 창, 합니다 **병렬 조사식** 창 및 **태스크** 창도 JavaScript를 지원 합니다. 시작 하려면 참조 [연습: 병렬 응용 프로그램 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md) 고 [연습: 디버깅을 C++ AMP 응용 프로그램](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)합니다.

- GPU 스레드 디버깅을 위한 기본 도구는 합니다 **GPU 스레드** 창입니다. [방법: GPU 스레드 창 사용](../debugger/how-to-use-the-gpu-threads-window.md)을 참조하세요.

- 기본 도구는 프로세스에 대 한 합니다 **프로세스에 연결** 대화 상자를 **프로세스** 창 및 **디버그 위치** 도구 모음입니다.

Visual Studio에서 제공 하는 강력한 중단점 및 추적점 다중 스레드 응용 프로그램을 디버깅할 때 유용할 수 있습니다. 중단점 조건 및 필터를 사용 하 여 개별 스레드에 중단점을 설정 합니다. 추적점 교착 상태와 같은 문제를 연구를 중단 하지 않고 프로그램의 실행을 추적 사용 하도록 설정 합니다. 자세한 내용은 [중단점 작업 및 추적점](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)합니다.

사용자 인터페이스가 있는 다중 스레드 애플리케이션은 특히 디버깅하기 어려울 수 있습니다. 두 번째 컴퓨터에 응용 프로그램을 실행 하 고 원격 디버깅 사용을 고려할 수 있습니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)합니다.

## <a name="articles-about-debugging-multithreaded-apps"></a>다중 스레드 응용된 프로그램을 디버깅 하는 방법에 대 한 문서

 [다중 스레드 응용 프로그램 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)

스레드 디버깅 기능을 강조 하는 기능을 살펴보고 합니다 **병렬 스택** 창 및 **병렬 조사식** 창입니다.

 [스레드 및 프로세스 디버깅을 위한 도구](../debugger/debug-threads-and-processes.md)

스레드 및 프로세스 디버깅에 대 한 도구의 기능을 나열 합니다.

 [여러 프로세스 디버그](../debugger/debug-multiple-processes.md)

여러 프로세스 디버깅 방법에 대해 설명합니다.

 [연습: 스레드 창을 사용하여 디버그](../debugger/how-to-use-the-threads-window.md).

사용 하는 방법을 보여 주는 연습 합니다 **스레드** 창 및 **디버그 위치** 도구 모음입니다.

 [연습: 병렬 애플리케이션 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)

사용 하는 방법을 보여 주는 연습 합니다 **병렬 스택** 하 고 **작업** windows.

 [방법: 디버그 중 다른 스레드로 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md)

여러가지 방법으로 디버깅 컨텍스트를 다른 스레드로 전환 합니다.

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

## <a name="see-also"></a>참고자료

- [중단점 사용](../debugger/using-breakpoints.md)
- [스레딩](/dotnet/standard/threading/index)
- [구성 요소에서 다중 스레딩](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [이전 코드를 위한 다중 스레드 지원(Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [스레드 및 프로세스 디버그](../debugger/debug-threads-and-processes.md)
- [원격 디버깅](../debugger/remote-debugging.md)