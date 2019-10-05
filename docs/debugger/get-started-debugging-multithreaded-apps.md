---
title: 다중 스레드 응용 프로그램을 디버그 하는 방법을 알아봅니다
description: Visual Studio에서 병렬 스택 및 병렬 조사식 창을 사용 하 여 디버깅
ms.custom: ''
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f07791a02c5e84722e8193f21b7ed2fe37bdd7f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849574"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>다중 스레드 응용 프로그램 디버깅 시작 (C#, Visual Basic의 경우 C++)

Visual Studio는 여러 도구와 다중 스레드 응용 프로그램을 디버깅할 수 있도록 사용자 인터페이스 요소를 제공 합니다. 이 자습서에서는 스레드 마커를 사용 하는 방법을 보여 줍니다.는 **병렬 스택** 창에는 **병렬 조사식** 창과 조건부 중단점, 중단점 필터. 이 자습서를 완료 다중 스레드 응용 프로그램 디버깅에 Visual Studio 기능을 숙지 합니다.

이러한 두 항목 다른 다중 스레드 디버깅 도구를 사용 하 여 추가 정보를 제공 합니다.

- 사용 하 여 **디버그 위치** 도구 모음 및 **스레드** 창 참조 [연습: 다중 스레드 응용 프로그램을 디버그](../debugger/how-to-use-the-threads-window.md)합니다.

- 사용 하는 샘플에 대 한 <xref:System.Threading.Tasks.Task> (관리 코드) 및 동시성 런타임 (C++)를 참조 하십시오 [연습: 병렬 응용 프로그램을 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)합니다. 대부분의 다중 스레드 응용 프로그램 형식에 적용 되는 일반적인 디버깅 팁, 해당 항목 및이 참조 하세요.

다중 스레드 응용 프로그램 프로젝트를 먼저 해야 합니다. 예를 들면 다음과 같습니다.

## <a name="create-a-multithreaded-app-project"></a>다중 스레드 앱 프로젝트 만들기

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. 형식 **Ctrl + Q** 입력 검색 상자를 열려면 **콘솔** (또는 **c + +** ), 선택 **템플릿**, 차례로:

    - 에 대 한 C# 또는 Visual Basic의 경우 선택 **새 콘솔 앱 (.NET Framework) 프로젝트 만들기** 에 대 한 C# 또는 Visual Basic입니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.
    - 에 대 한 C++을 선택 **새 콘솔 앱 프로젝트 만들기** 에 대 한 C++합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.

    그런 다음 같은 이름을 입력 **MyThreadWalkthroughApp** 클릭 **만들기**합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례로 선택합니다. 왼쪽된 창에는 **새 프로젝트** 대화 상자에서 다음을 선택 합니다.

    - 에 대 한는 C# 앱 아래에 있는 **Visual C#** 를 선택 **Windows 데스크톱**를 선택한 다음 가운데 창에서 **콘솔 앱 (.NET Framework)** .
    - Visual Basic 앱의 경우 아래 **Visual Basic**, 선택 **Windows Desktop**를 선택한 다음 가운데 창에서 **콘솔 앱 (.NET Framework)** 합니다.
    - 에 대 한는 C++ 앱 아래에 있는 **Visual C++** 를 선택 **Windows 데스크톱**,를 선택한 후 **Windows 콘솔 응용 프로그램**.

    그런 다음 같은 이름을 입력 **MyThreadWalkthroughApp** 누릅니다 **확인**합니다.
    ::: moniker-end

    **콘솔 앱** 프로젝트 템플릿이 표시되지 않는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **.NET 데스크톱 개발*** 또는 **C++를 사용한 데스크톱 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

1. **확인**을 선택합니다.

    새 콘솔 프로젝트가 나타납니다. 프로젝트가 만들어지면 소스 파일이 나타납니다. 선택한 언어에 따라 소스 파일을 호출할 수 있습니다 *Program.cs*하십시오 *MyThreadWalkthroughApp.cpp*, 또는 *Module1.vb*합니다.

1. 소스 파일에 표시 되는 코드를 삭제 하 고 아래 나열 된 적절 한 예제 코드로 바꿉니다.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "pch.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. **파일** 메뉴에서 **모두 저장**을 선택합니다.

1. (Visual Basic만 해당) 솔루션 탐색기 (오른쪽 창)에서 프로젝트 노드를 마우스 오른쪽 단추로 차례로 **속성**합니다. 아래는 **응용 프로그램** 탭으로 변경 합니다 **시작 개체** 에 **간단한**.

## <a name="debug-the-multithreaded-app"></a>다중 스레드 앱 디버깅

1. 소스 코드 편집기에서 다음 코드 조각 중 하나를 찾습니다.

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. 왼쪽된 여백에서 마우스 왼쪽 단추로 클릭 합니다 `Thread.Sleep` 또는 `std::this_thread::sleep_for` 문을 새 중단점을 삽입 합니다.

    여백에 빨간색 원이이 위치에 중단점 설정 되어 있는지 나타냅니다.

2. 에 **디버그** 메뉴에서 **디버깅 시작** (**F5**).

    Visual Studio 솔루션을 빌드합니다, 그리고 앱, 연결 된 디버거와 함께 실행을 시작 및 앱 중단점에서 멈춥니다.

3. 소스 코드 편집기에서 해당 중단점이 있는 줄을 찾습니다.

### <a name="ShowThreadsInSource"></a>스레드 마커를 검색 합니다.  

1. 디버그 도구 모음에서 선택 합니다 **소스의 스레드 표시** 단추 ![소스의 스레드 표시](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")합니다.

2. 키를 눌러 **F11** 디버거를 한 줄 코드를 한 번입니다.

3. 창 왼쪽의 여백을 확인합니다. 이 줄에 표시 됩니다는 *스레드 마커* 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker") 트위스트 스레드가 각각 두와 유사한 합니다. 스레드 마커는 이 위치에서 스레드가 중지되었음을 나타냅니다.

    중단점에서 스레드 마커를 부분적으로 숨겨진 수 있습니다.

4. 스레드 마커에 포인터를 올려 놓습니다. 중지 된 각 스레드의 이름과 스레드 ID 번호를 알리는 DataTip이 나타납니다. 이 경우 이름의 되었을 `<noname>`합니다.

5. 바로 가기 메뉴에서 사용할 수 있는 옵션을 보려면 스레드 마커를 선택 합니다.

### <a name="ParallelStacks"></a>스레드 위치를 보려면

에 **병렬 스택** 전환할 수 있습니다 창 작업 보기 및 있습니다 각 스레드에 대 한 호출 스택 정보를 볼 수 있습니다 (작업 기반 프로그래밍)에 대 한 스레드 뷰 사이입니다. 이 앱의 경우 스레드 뷰에 사용할 수 있습니다.

1. 엽니다는 **병렬 스택** 를 선택 하 여 창 **디버그** > **Windows** > **병렬 스택**합니다. 다음과 유사한 항목이 표시 됩니다. 정확한 정보는 각 스레드, 하드웨어 및 프로그래밍 언어의 현재 위치에 따라 달라 집니다.

    ![병렬 스택 창](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    이 예제에서는 왼쪽에서 오른쪽 알 관리 코드에 대 한이 정보:

    - 주 스레드 (왼쪽)에서 중지 되었습니다. `Thread.Start`, 여기서 중지 지점 나타난 스레드 마커 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")합니다.
    - 입력 한 두 개의 스레드를 `ServerClass.InstanceMethod`, 그 중 하나는 현재 스레드 (노란색 화살표)을에서 다른 스레드를 중지 하는 동안 `Thread.Sleep`합니다.
    - (오른쪽) 새 스레드 시작 수도 있지만에서 중지 되었습니다 `ThreadHelper.ThreadStart`합니다.

2. 항목을 마우스 오른쪽 단추로 클릭 합니다 **병렬 스택** 창 바로 가기 메뉴에서 사용할 수 있는 옵션을 확인 합니다.

    이러한 오른쪽 클릭 메뉴에서 다양 한 조치를 취할 수 있지만이 자습서에서 이러한 세부 사항을 자세히 표시 됩니다 것를 **병렬 조사식** 창 (다음 섹션).

    > [!NOTE]
    > 목록 보기 각 스레드에 대 한 정보를 보려면 사용 합니다 **스레드** 창 대신 합니다. [연습: 다중 스레드 응용 프로그램을 디버그](../debugger/how-to-use-the-threads-window.md)합니다.

### <a name="set-a-watch-on-a-variable"></a>변수에 조사식 설정

1. 엽니다는 **병렬 조사식** 를 선택 하 여 창 **디버그** > **Windows** > **병렬 조사식**  >  **병렬 조사식 1**합니다.

2. 표시 되는 셀을 선택 합니다 `<Add Watch>` 텍스트 (또는 네 번째 열에서 빈 머리글 셀) enter `data`합니다.

    각 스레드에 대 한 데이터 변수 값 창에 나타납니다.

3. 표시 되는 셀을 선택 합니다 `<Add Watch>` 텍스트 (또는 다섯 번째 열에서 빈 머리글 셀) enter `count`합니다.

    에 대 한 값을 `count` 각 스레드에 대 한 변수 창에 나타납니다. 많은 정보를 아직 보이지 않으면 시도 키를 눌러 **F11** 에 여러 번 디버거에서 스레드의 실행을 진행 합니다.

    ![병렬 조사식 창](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 사용 가능한 옵션을 표시 하려면 창의 행 중 하나를 오른쪽 단추로 클릭 합니다.

### <a name="flag-and-unflag-threads"></a>스레드에 플래그 지정 및 스레드의 플래그 해제
스레드 중 중요 한 스레드를 추적 하 고 다른 스레드를 무시 플래그를 지정할 수 있습니다.

1. 에 **병렬 조사식** 누른 창 합니다 **Shift** 키 및 여러 행을 선택 합니다.

2. 마우스 오른쪽 단추로 클릭 **플래그**합니다.

    선택한 모든 스레드에 플래그가 지정 됩니다. 이제 플래그가 지정 된 스레드만 표시 하도록 필터링 할 수 있습니다.

3. 에 **병렬 조사식** 창에서 합니다 **플래그가 지정 된 스레드만 표시** 단추 ![플래그가 지정 된 스레드 표시](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")합니다.

    플래그가 지정 된 스레드만 목록에 표시 합니다.

    > [!TIP]
    > 일부 스레드를 플래그를 지정한 후 코드 편집기에서 코드 줄을 마우스 오른쪽 단추로 클릭 하 고 선택할 수 **커서 플래그가 지정 된 스레드가 실행**합니다. 코드는 모든 플래그가 지정 된 스레드만 도달 선택 해야 합니다. Visual Studio는 스레드를 일시 중지 선택한 코드 줄에서의 실행 순서를 제어 하려면 쉽게 [스레드 중지 및 재개](#bkmk_freeze)합니다.

4. 선택 된 **플래그가 지정 된 스레드만 표시** 단추를 다시 설정/해제를 다시 **모든 스레드 표시** 모드입니다.

5. 하나 이상의 플래그가 지정 된 스레드를 마우스 오른쪽 단추로 클릭 스레드의 플래그를 해제 하는 **병렬 조사식** 창과 선택 **플래그 해제**합니다.

### <a name="bkmk_freeze"></a> 중지 하 고 스레드 실행을 재개

> [!TIP]
> 고정 및 고정 해제 수 있습니다 (일시 중단 및 다시 시작) 스레드를 스레드 작업을 수행 하는 순서를 제어 합니다. 이 교착 상태 같은 동시성 문제를 해결 하 고 경합 조건을 수 있습니다.

1. 에 **병렬 조사식** 창에 선택 된 모든 행을 마우스 오른쪽 단추로 **Freeze**합니다.

    두 번째 열에서 각 행에 대 한 일시 중지 아이콘이 나타납니다. 일시 중지 아이콘은 스레드를 고정 하는 것을 나타냅니다.

2. 하나의 행만 선택 하 여 다른 모든 행을 선택 취소 합니다.

3. 선택한 행을 마우스 오른쪽 단추로 클릭 **재개**합니다.

    일시 중지 아이콘 스레드를 더 이상 고정 나타내는이 행에서 사라집니다.

4. 코드 편집기 및 키를 눌러 전환할 **F11**합니다. 고정 되지 않은 스레드만 실행 됩니다.

    앱 몇 가지 새 스레드를 인스턴스화할 수도 수 있습니다. 새 스레드 플래그를 지정 하지 않으며 고정 되지 않은 합니다.

### <a name="bkmk_follow_a_thread"></a> 조건부 중단점을 사용 하 여 단일 스레드를 수행 합니다.

디버거에서 단일 스레드로 실행 상태를 추적할 수 있습니다. 작업을 수행 하는 한 가지 방법은 관심이 없는 스레드를 고정 하면 됩니다. 일부 시나리오에서는 특정 버그를 재현 하는 예제에 대 한 다른 스레드를 고정 하지 않고 단일 스레드를 수행 해야 합니다. 다른 스레드를 고정 하지 않고 스레드를 수행 하려면 관심 있는 스레드에서 제외 하 고 코드를 중단 하면 하면 안 됩니다. 설정 하 여이 수행할 수는 [조건부 중단점](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)합니다.

스레드 이름 또는 스레드 ID와 같은 다양 한 조건에 중단점을 설정할 수 있습니다. 것이 유용한 방법은 각 스레드에 고유 사용자가 알고 있는 데이터에 조건을 설정 합니다. 특정 스레드에 보다 몇 가지 특정 데이터 값에 더 관심이 되는 일반적인 디버깅 시나리오입니다.

1. 이전에 만든 중단점을 마우스 오른쪽 단추로 클릭 **조건을**합니다.

2. 에 **중단점 설정** 창에서 입력 `data == 5` 조건 식에 대 한 합니다.

    ![조건부 중단점](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 특정 스레드에 더 많은 관심 인 경우 스레드 이름이 나 스레드 ID 조건에 사용 합니다. 이를 수행 하는 **중단점 설정** 창에서 **필터** 대신 **조건식**, 필터 팁을 따릅니다. 하려는 앱 코드에서 스레드 이름을 디버거를 다시 시작할 때 스레드 Id를 변경 합니다.

3. 닫기 합니다 **중단점 설정** 창입니다.

4. 다시 시작 선택 ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 디버깅 세션을 다시 시작 하는 단추입니다.

    데이터 변수를 5 스레드에서 코드로 중단 됩니다. 에 **병렬 조사식** 창에서 현재 디버거 컨텍스트를 나타내는 노란색 화살표에 대 한 합니다.

5. 이제 코드에 대해 실행할 수 있습니다 (**F10**) 및 한 단계씩 코드 실행 (**F11**)는 단일 스레드 실행을 따릅니다.

    중단점 조건은 스레드로 고유 있으며 디버거 (비활성화 해야 할) 다른 스레드에서 다른 중단점을 적중 하지 않습니다, 코드 수 있으며 다른 스레드를 전환 하지 않고 코드를 한 단계씩 수 있습니다.

    > [!NOTE]
    > 디버거를 진행 하면 모든 스레드가 실행 됩니다. 그러나 다른 스레드 중 하나는 중단점에 도달 하지 않는 한 다른 스레드에서 코드에 디버거를 중단 하지 않습니다.

## <a name="see-also"></a>참고자료

- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [방법: 디버그 중 다른 스레드로 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [방법: 병렬 스택 창 사용](../debugger/using-the-parallel-stacks-window.md)
- [방법: 병렬 조사식 창 사용](../debugger/how-to-use-the-parallel-watch-window.md)