---
title: 다중 스레드 애플리케이션 디버깅
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691276"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio에서 다중 스레드 애플리케이션 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

스레드는 운영 체제에서 프로세서 시간을 할당받는 명령 시퀀스입니다. 운영 체제에서 실행되는 모든 프로세스는 최소한 하나의 스레드로 구성됩니다. 프로세스에 스레드가 둘 이상인 경우를 다중 스레드라고 합니다.

 다중 프로세서, 다중 코어 프로세서 또는 하이퍼스레드 프로세스를 갖춘 컴퓨터는 여러 스레드를 동시에 실행할 수 있습니다. 여러 스레드를 병렬 처리하면 프로그램 성능이 크게 향상되지만, 여러 스레드를 추적해야 하므로 디버깅이 어려워질 수도 있습니다.

 또한 다중 스레드로 인해 새로운 종류의 버그가 생길 수 있습니다. 예를 들어 둘 이상의 스레드에서 같은 리소스에 액세스해야 하지만 한 번에 스레드 중 하나만 리소스에 안전하게 액세스할 수 있는 경우가 많습니다. 한 번에 한 스레드만 리소스에 액세스할 수 있게 하려면 특정한 형태의 상호 제외가 필요합니다. 상호 제외가 올바르게 수행 되는 경우 만들 수는 *교착 상태* 스레드가 실행 될 수 있는 조건이 있습니다. 교착 상태 문제는 특히 디버깅하기 어려울 수 있습니다.

 Visual Studio에서 제공 된 **스레드** 창, GPU 스레드 창, 병렬 조사식 창 및 다중 스레드 디버깅을 쉽게 만들어 주는 기타 기능입니다. 스레딩 기능을 배우는 가장 좋은 방법은 연습을 수행하는 것입니다. [연습: 다중 스레드 응용 프로그램 디버깅](../debugger/walkthrough-debugging-a-multithreaded-application.md) 고 [연습: 디버깅을 C++ AMP 응용 프로그램](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)합니다.

 Visual Studio에서 제공하는 강력한 중단점 및 추적점은 다중 스레드 애플리케이션을 디버깅할 때 매우 유용할 수 있습니다. 중단점 필터를 사용하면 개별 스레드에 중단점을 배치할 수 있습니다. 참조 [중단점 사용](../debugger/using-breakpoints.md)

 사용자 인터페이스가 있는 다중 스레드 애플리케이션은 특히 디버깅하기 어려울 수 있습니다. 이러한 경우 애플리케이션을 다른 컴퓨터에서 실행하면서 원격 디버깅을 사용하는 것이 좋습니다. 정보를 참조 하세요 [원격 디버깅](../debugger/remote-debugging.md)합니다.

## <a name="in-this-section"></a>섹션 내용
 [스레드 및 프로세스 디버깅](../debugger/debug-threads-and-processes.md) 스레드 및 프로세스 디버깅의 기본 사항을 설명 합니다.

 [여러 프로세스 디버깅](../debugger/debug-multiple-processes.md) 여러 프로세스를 디버그 하는 방법에 설명 합니다.

 [방법: 스레드 창 사용](../debugger/how-to-use-the-threads-window.md) 유용한 절차를 사용 하 여 스레드를 디버깅 합니다 **스레드** 창입니다.

 [방법: 다른 스레드 디버그 하는 동안 전환할](../debugger/how-to-switch-to-another-thread-while-debugging.md) 디버깅 컨텍스트를 다른 스레드로 전환 하는 세 가지 방법입니다.

 [방법: 플래그 및 스레드의 플래그 해제](../debugger/how-to-flag-and-unflag-threads.md) 제공 디버깅 도중 특별히 주의 하려는 스레드를 표시 하거나 플래그입니다.

 [방법: 네이티브 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-native-code.md) 스레드에에서 볼 수 있는 이름을 지정 합니다 **스레드** 창입니다.

 [방법: 관리 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-managed-code.md) 스레드에에서 볼 수 있는 이름을 지정 합니다 **스레드** 창입니다.

 [연습: 다중 스레드 응용 프로그램을 디버깅](../debugger/walkthrough-debugging-a-multithreaded-application.md)합니다.
다양한 스레드 디버깅 기능을 안내하고, [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)]에서 기능을 사용하는 방법에 중점을 둡니다.

 [방법: 고성능 클러스터에서 디버그](../debugger/how-to-debug-on-a-high-performance-cluster.md) 고성능 클러스터에서 실행 되는 응용 프로그램을 디버깅 하는 것에 대 한 기술입니다.

 [네이티브 코드의 스레드 디버깅 팁](../debugger/tips-for-debugging-threads-in-native-code.md) 네이티브 스레드를 디버깅 하는 것에 대 한 유용할 수 있는 간단한 방법입니다.

 [작업 창 사용](../debugger/using-the-tasks-window.md) 상태 및 기타 유용한 정보를 비롯 한 모든 관리 되는 또는 네이티브 작업 개체의 목록을 보여 줍니다.

 [병렬 스택 창 사용](../debugger/using-the-parallel-stacks-window.md) 표시 호출 스택을 여러 스레드 (또는 작업)의 단일 보기에는 스레드 또는 작업 사이의 공통 스택 세그먼트를 병합 하기도 합니다.

 [연습: 병렬 응용 프로그램을 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md) 병렬 작업 및 병렬 스택 창을 사용 하는 방법을 보여 주는 연습입니다.

 [방법: 병렬 조사식 창을 사용 하 여](../debugger/how-to-use-the-parallel-watch-window.md) 여러 스레드에서 값과 식을 검사 합니다.

 [방법: GPU 스레드 창 사용](../debugger/how-to-use-the-gpu-threads-window.md) 검토 및 디버깅 중 GPU에서 실행 되는 스레드를 사용 하 여 작업 합니다.

## <a name="related-sections"></a>관련 단원

[중단점 사용](../debugger/using-breakpoints.md)
- 개별 스레드에 중단점을 배치하려는 경우 중단점 필터를 사용하는 방법을 보여 줍니다.

- 추적점을 통해 프로그램 실행을 중단 없이 추적할 수 있습니다. 이 기능은 교착 상태와 같은 문제를 파악할 때 유용합니다.

  [스레딩](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) 스레딩의 개념 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 예제 코드를 포함 하 여 프로그래밍 합니다.

  [구성 요소에서 다중 스레딩](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) 사용 하는 방법의 다중 스레딩 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 구성 요소입니다.

  [이전 코드를 위한 다중 스레드 지원 (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) 스레딩 개념 및 예제 코드에 대 한 C++ MFC를 사용 하는 프로그래머입니다.

## <a name="see-also"></a>참고 항목
 [스레드 및 프로세스 디버깅](../debugger/debug-threads-and-processes.md) [원격 디버깅](../debugger/remote-debugging.md)
