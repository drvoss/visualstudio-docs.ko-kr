---
title: '방법: 관리 코드에서 다중 스레드 관리 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 307ee61380b137cc7426c641a85844934ff0377a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340586"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>방법: 관리 코드에서 다중 스레드 관리
비동기 메서드를 호출 하거나 Visual Studio UI 스레드가 아닌 스레드에서 실행 되는 작업에는 관리 되는 VSPackage 확장에 있는 경우 아래 제공 된 지침을 따라야 합니다. 작업에 대 한 다른 스레드가 완료 되기를 대기할 필요가 없기 때문에 UI 스레드를 반응 형 유지할 수 있습니다. 코드를 효율적으로 수행할 수 스택 공간을 차지 하는 추가 스레드 필요가 없기 때문에 있고 더 안정적이 고 교착 상태 및 중지 문제를 방지 하기 때문에 디버그 하는 일을 쉽게 만들 수 있습니다.

 일반적으로 전환할 수 UI 스레드에서 다른 스레드 또는 그 반대의 경우도 마찬가지입니다. 메서드는 반환 될 때 현재 스레드를 원래 호출한 스레드가 됩니다.

> [!IMPORTANT]
> 다음 지침의 Api를 사용 합니다 <xref:Microsoft.VisualStudio.Threading> 네임 스페이스, 특히는 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 클래스입니다. 이 네임 스페이스의 Api에 새로 추가 된 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]합니다. 인스턴스를 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 에서 합니다 <xref:Microsoft.VisualStudio.Shell.ThreadHelper> 속성 `ThreadHelper.JoinableTaskFactory`합니다.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>UI 스레드에서 백그라운드 스레드로 전환

1. UI 스레드에서 및 사용 하 여 백그라운드 스레드에서 비동기 작업을 수행 하려는 경우 `Task.Run()`:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. UI 스레드에서 사용 하 여 백그라운드 스레드에서 작업을 수행 하는 동안 동기적으로 차단 하려는 경우는 <xref:System.Threading.Tasks.TaskScheduler> 속성 `TaskScheduler.Default` 내에서 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>백그라운드 스레드에서 UI 스레드로 전환

1. 백그라운드 스레드에서 및 사용 하 여 UI 스레드에서 작업을 수행 하려는 경우 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     사용할 수는 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> UI 스레드로 전환 하는 방법입니다. 이 메서드는 현재 비동기 메서드의 연속을 사용 하 여 UI 스레드에서에 메시지를 게시 하 고 올바른 우선 순위를 설정 하 고 교착 상태를 방지 하기 위해 스레딩 프레임 워크의 나머지와도 통신.

     백그라운드 스레드 메서드 비동기 아니며 시청이 비동기, 하는 경우 계속 사용할 수 있습니다 합니다 `await` 구문을 사용 하 여 회사를 래핑하여 UI 스레드로 전환 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>이 예제와 같이:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```