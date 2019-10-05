---
title: '방법: 확장 성능 진단 | Microsoft Docs'
ms.date: 11/08/2016
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 3d8fb5de23cbc4664ea322a9149653598956aed7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863337"
---
# <a name="measuring-extension-impact-in-startup"></a>시작에서 확장 영향 측정

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Visual Studio 2017의 확장 성능에 집중

고객 피드백에 따라 Visual Studio 2017 릴리스에 대 한 주요 영역 중 하나 였습니다 시작 및 솔루션 로드 성능. Visual Studio 플랫폼 팀으로 작업을 시작 및 솔루션 로드 성능 개선. 일반적으로 측정 제안 설치 된 확장이 이러한 시나리오에 상당한 영향을 줄 수도 있습니다.

이 영향을 이해 하는 사용자를 위해 느린 확장의 사용자에 게 알리는 Visual Studio의 새로운 기능을 추가 했습니다. 경우에 따라 Visual Studio 솔루션 로드 또는 시작을 저하 하는 새 확장을 검색 합니다. 속도가 느려지는 감지 되 면 사용자가 새 "Visual Studio 성능 관리" 대화 상자를 가리키도록 IDE에서 알림이 표시 됩니다. 이 대화 상자는 항상 이전에 검색된 확장을 이동 하려면 도움말 메뉴에서 액세스할 수 있습니다.

![Visual Studio 성능 관리](media/manage-performance.png)

이 문서는 확장 영향을 계산 하는 방식을 설명 하 여 확장을 쉽게 하려고 합니다. 이 문서에는 확장 영향을 로컬로 분석 될 수 있습니다 하는 방법을 설명 합니다. 로컬로 확장 영향 분석 확장인 경우 확장에 영향을 주는 성능으로 표시 될 수 있습니다 결정 됩니다.

> [!NOTE]
> 이 문서는 시작 및 솔루션 로드 시 확장의 영향에 중점을 둡니다. 또한 확장 하면 UI가 응답 하지 않을 때 Visual Studio 성능에 영향입니다. 대 한 자세한 내용은이 항목을 참조 하세요. [방법: 진단 UI 확장 프로그램에서 발생 하는 지연](how-to-diagnose-ui-delays-caused-by-extensions.md)합니다.

## <a name="how-extensions-can-impact-startup"></a>확장 시작에 미칠 수 있습니다

시작 성능에 영향을 줄에 대 한 확장에 대 한 가장 일반적인 방법 중 하나는 자동 로드할 NoSolutionExists 등 ShellInitialized 알려진된 시작 UI 컨텍스트 중 하나를 선택 하 여 것입니다. 이러한 UI 컨텍스트 가져오기 시작 하는 동안 활성화 됩니다. 포함 된 모든 패키지는 `ProvideAutoLoad` 특성 해당 컨텍스트를 사용 하 여 해당 정의에서 로드 되 고 해당 시점에 초기화 합니다.

확장의 영향을 측정 하는 경우 주로 집중 위의 컨텍스트에서 자동 로드를 선택 하는 해당 확장 프로그램에서 소요 된 시간입니다. 측정 한 시간은 포함 하지만에 제한 되지는지 않습니다.

* 동기 패키지에 대 한 확장 프로그램 어셈블리 로드
* 동기 패키지에 대 한 패키지 클래스 생성자에 소요 된 시간
* 초기화 (또는 SetSite) 메서드를 동기 패키지에 대 한 패키지에 소요 된 시간
* 비동기 패키지에 대 한 위의 작업을 백그라운드 스레드에서 실행합니다.  따라서 작업 모니터링에서 제외 됩니다.
* 패키지 초기화 하는 동안 주 스레드에서 실행 되도록 예약 하는 모든 비동기 작업에 소요 된 시간
* 이벤트 처리기를 특히 초기화 셸 상황에 맞는 정품 인증 또는 셸 좀비 상태 변경에 소요 된 시간
* Visual Studio 2017 업데이트 3에서 시작 하며, 또한 먼저 셸 초기화 되기 전에 유휴 호출에 걸린 시간을 모니터링 합니다. 또한 유휴 처리기에서 장기 작업 응답 하지 않는 IDE 발생 하 고 사용자 체감된 시작 시간에 영향을 합니다.

Visual Studio 2015에서 시작 하는 많은 기능을 추가 했습니다. 이러한 기능은 자동 로드 패키지에 대 한 필요성을 제거 하는 데 합니다. 또한 기능 보다 구체적인 경우에 로드 하는 패키지에 대 한 필요성을 연기 합니다. 이러한 경우에는 사용자 수 없는 확장을 사용 하 여 자동으로 로드 하는 경우는 확장의 영향을 줄이는 보다 특정 예제가 포함 되어 있습니다.

이러한 기능에 대 한 자세한 내용은 다음 문서에서 찾을 수 있습니다.

[규칙 기반 UI 컨텍스트](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): UI 컨텍스트를 구축 하는 다양 한 규칙 기반 엔진을 사용 하면 프로젝트 형식, 버전, 및 특성에 따라 사용자 지정 컨텍스트를 만들 수 있습니다. 보다 구체적인 시나리오 중 패키지를 로드 하려면 사용자 지정 컨텍스트를 사용할 수 있습니다. 이러한 특정 시나리오에는 시작 하는 대신 특정 기능을 사용 하 여 프로젝트의 현재 상태 포함 됩니다. 사용자 지정 컨텍스트 뿐만 [사용자 지정 컨텍스트 연결에 대 한 가시성을 명령을](visibilityconstraints-element.md) 프로젝트 구성 요소 또는 다른 사용 가능한 조건에 따라 합니다. 이 기능은 상태 쿼리 명령 처리기를 등록 하는 패키지를 로드할 필요가 없습니다.

[비동기 패키지 지원](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Visual Studio 2015에서 새 AsyncPackage 기본 클래스에는 로드할 백그라운드에서 비동기적으로 자동 부하 특성 또는 비동기 서비스 쿼리를 패키지 로드를 요청한 경우 Visual Studio 패키지가 있습니다. 이 백그라운드 로드가 응답성을 유지 하기 위해 IDE를 허용 합니다. IDE는 응답도 확장은 백그라운드에서 초기화 되 고 시작 및 솔루션 로드와 같은 중요 한 시나리오를 받지 않습니다.

[비동기 서비스](how-to-provide-an-asynchronous-visual-studio-service.md): 비동기 패키지 지원과 서비스를 비동기적으로 쿼리하고 비동기 서비스를 등록할 수에 대 한 지원을 추가 했습니다. 무엇 보다도 노력에 비동기 쿼리 작업은 대부분 백그라운드 스레드에서 발생 되도록 비동기 쿼리를 지원 하기 위해 핵심 Visual Studio 서비스를 변환 합니다. SComponentModel (Visual Studio MEF 호스트)는 이제 완전히 비동기 로드를 지원 하도록 확장을 허용 하도록 비동기 쿼리를 지 원하는 주요 서비스 중 하나입니다.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>확장을 로드 자동 미치는 영향을 줄이기

패키지를 자동으로 시작 시 로드 되도록 해야 하는 경우 패키지 초기화 하는 동안 수행 된 작업을 최소화 하기 위해 중요 한 것입니다. 시작에 영향을 주는 확장 가능성을 줄이기 패키지 초기화 작업을 최소화 합니다.

비용이 많이 드는 되도록 패키지 초기화 될 수 있는 몇 가지 예는:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>비동기 패키지 로드 하는 대신 동기 패키지 로드 사용

기본적으로 주 스레드에서 동기 패키지는 로드 때문에 앞에서 설명한 대로 대신 비동기 패키지 기본 클래스를 사용 하도록 자동으로 로드 패키지에 있는 확장 소유자를 좋습니다. 비동기 로딩을 지원 하도록 자동 로드 패키지를 변경 됩니다도 쉽게 아래 다른 문제를 해결 합니다.

### <a name="synchronous-filenetwork-io-requests"></a>동기 파일/네트워크 IO 요청

이상적으로 주 스레드에서 모든 동기 파일 또는 네트워크 IO 요청을 피해 야 합니다. 영향력은 컴퓨터 상태에 따라 달라 집니다 및 일부 경우에는 장기간에 대 한 차단할 수 있습니다.

비동기 패키지 로드 및 비동기 IO Api를 사용 하 여 해당 패키지 초기화 이러한 경우 주 스레드를 차단 하지 않는지 확인 해야 합니다. 또한 사용자는 I/O 요청 백그라운드에서 발생 하는 동안 Visual Studio를 사용 하 여 상호 작용할 수 계속 수 있습니다.

### <a name="early-initialization-of-services-components"></a>구성 요소 서비스의 초기 초기화

패키지 초기화에서 일반적인 패턴 중 하나에서 사용 하거나 패키지에 해당 패키지에서 제공 서비스를 초기화 하는 것 `constructor` 또는 `initialize` 메서드. 이렇게 하면 서비스를 사용 하도록 준비를 하는 동안 해당 서비스 즉시 사용 되지 않는 경우 로드 패키지에 불필요 한 비용을 추가할 수도 있습니다. 대신 패키지 초기화에서 수행 된 작업을 최소화 하기 위해 필요에 따라 이러한 서비스를 초기화 합니다.

패키지에서 제공 하는 글로벌 서비스를 사용할 수 있습니다 `AddService` 지연 구성 요소에 의해 요청 될 경우에 서비스를 초기화 하는 함수를 사용 하는 방법입니다. 패키지 내에서 사용 되는 서비스에 대 한 지연을 사용할 수 있습니다\<T > 또는 AsyncLazy\<T > 서비스는 처음 사용할 때 초기화/쿼리 되도록 합니다.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>활동 로그를 사용 하 여 확장을 로드 자동의 영향을 측정 합니다.

Visual Studio 2017 업데이트 3부터 Visual Studio 활동 로그는 시작 및 솔루션 로드 하는 동안 패키지의 성능 영향에 대 한 항목을 이제 포함 됩니다. /Log 스위치를 사용 하 여 Visual Studio를 열고 엽니다 해야 이러한 측정값을 보려면 *ActivityLog.xml* 파일입니다.

활동 로그에 항목 아래에 "Visual Studio 성능 관리" 원본 및 다음과 같이 표시 됩니다.

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

이 예제에서는 "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" GUID 사용 하 여 패키지의 Visual Studio 2008 ms 시작에서 소비를 보여 줍니다. 절감 사용자 참조는 해당 패키지에 대 한 확장을 사용 하지 않도록 설정 하는 것 처럼 패키지의 영향을 계산할 때 Visual Studio의 기본 개수로 최상위 비용 고려는 note 합니다.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>PerfView를 사용 하 여 확장을 로드 자동의 영향을 측정 합니다.

코드 분석 패키지 초기화를 저하 시킬 수 있는 코드 경로 식별할 수, 하는 동안 Visual Studio 시작에서 패키지 로드의 영향을 이해 하려면 PerfView와 같은 응용 프로그램을 사용 하 여 추적을 활용할 수도 있습니다.

PerfView는 시스템 차원 추적 도구입니다. 이 도구는 응용 프로그램 CPU 사용량 또는 시스템 호출을 차단 때문에 실행 부하 과다 경로 이해 하는 데 도움이 됩니다. 다음은 분석에서 사용할 수 있는 PerfView를 사용 하는 샘플 확장 빠른 예제는 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=28567)합니다.

**예제 코드:**

이 예제는 샘플을 기반으로 코드 아래에 표시 하도록 설계 된 경우 몇 가지 일반적인 지연 원인:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**PerfView 사용 하 여 추적을 기록 합니다.**

설치 된 확장을 통해 Visual Studio 환경을 설정한 PerfView를 열고 열기 시작 추적을 기록할 수 있습니다는 **수집** 대화 상자를 **수집** 메뉴.

![perfview 수집 메뉴](media/perfview-collect-menu.png)

기본 옵션은 CPU 사용량에 대 한 호출 스택을 제공 되지만 차단 시간에 관심이 있으므로 활성화 해야 **스레드 시간** 스택. 설정 준비 되 면 클릭할 수 있습니다 **수집 시작** 한 다음 시작을 기록한 후 Visual Studio를 엽니다.

컬렉션을 중지 하기 전에 Visual Studio는 완전히 초기화, 주 창 완전히 표시 되 고 확장 프로그램에 자동으로 표시 하는 UI 부분이 있으면 해당도 표시 되도록 하려고 합니다. Visual Studio는 완전히 로드 되 고 확장 프로그램은 초기화 하는 경우 기록 분석 추적을 중지할 수 있습니다.

**PerfView 사용 하 여 추적을 분석 합니다.**

기록이 완료 되 면 PerfView는 자동으로 추적을 열고 옵션을 확장 합니다.

이 예제에서는 주로에 관심이 합니다 **스레드 시간 스택** 아래에서 찾을 수 있는 보기 **고급 그룹**합니다. 이 보기에는 CPU 시간과 등 디스크 IO 대기 핸들에서 차단 된 시간을 포함 하 여 메서드에서 스레드에서 소요 된 총 시간이 표시 됩니다.

 ![스레드 시간 스택](media/perfview-thread-time-stacks.png)

 여는 동안 **스레드 시간 스택** 보기를 선택 해야 합니다 **devenv** 분석을 시작 하는 프로세스입니다.

PerfView 자세한 분석을 위해 자체 도움말 메뉴에서 시간 스택 스레드를 읽는 방법에 대 한 지침을 자세히가 있습니다. 이 예제의 목적에만 패키지 모듈 이름과 시작 스레드를 사용 하 여 스택을 포함 하 여이 보기를 추가로 필터링 하려고 합니다.

1. 설정할 **GroupPats** 기본적으로 추가 하는 모든 그룹화 제거 하려면 빈 텍스트입니다.
2. 설정할 **IncPats** 부분 어셈블리 이름 및 스레드 시작의 기존 프로세스 필터 외에도 포함 합니다. 이 예에서 것 **devenv; 스레드 시작 MakeVsSlowExtension**합니다.

이제 뷰 확장 관련 어셈블리와 연결 된 비용을 표시 됩니다. 이 보기에서 든 지 아래에 나열 된 **Inc (포괄 비용)** 시작 스레드의 열 필터링 된 확장 관련 되어 있고은 시작에 영향을 줄 수입니다.

몇 가지 흥미로운 호출 위의 예제에 대 한 스택 것입니다.

1. IO를 사용 하 여 `System.IO` 클래스: 이러한 프레임 포괄 비용 추적에 많은 비용이 소요 되지 않을 수 있습니다 하는 동안 파일 IO 속도 차이 컴퓨터에서 달라질 수 있으므로 문제의 원인이 됩니다.

   ![시스템 io 프레임](media/perfview-system-io-frames.png)

2. 다른 비동기 작업에서 대기 하는 호출을 차단 합니다. 이 경우 포괄 시간을 비동기 작업 완료 시 주 스레드는 차단에 나타냅니다.

   ![차단 호출 프레임](media/perfview-blocking-call-frames.png)

영향을 확인 하는 데 도움이 됩니다 추적의 다른 보기 중 하나는 **이미지 로드 스택**합니다. 에 적용 될 때 동일한 필터를 적용할 수 있습니다 **스레드 시간 스택** 자동 로드 패키지에서 실행 되는 코드 때문에 로드 된 모든 어셈블리를 찾아 보고 합니다.

각 추가 어셈블리는 상당히 느린 컴퓨터에서 시작 속도가 느려질 수 있습니다 하는 추가 디스크 I/O를 포함 하는 대로 패키지 초기화 루틴 내에서 로드 된 어셈블리 수를 최소화 하는 것이 반드시 합니다.

## <a name="summary"></a>요약

Visual Studio를 시작 했습니다 지속적으로 피드백을 받습니다 영역 중 하나가 되었습니다. 앞에서 설명한 대로 우리의 목표는 모든 사용자가 구성 요소 및 설치한 확장에 관계 없이 환경을 일관 된 시작입니다. 이러한 목표를 달성 하는 데 도움이 하는 데 확장 소유자를 사용 하 여 작업 하고자 합니다. 위의 지침 시작 시 확장 영향을 이해 하 고 하거나 부하를 자동 또는 사용자 생산성에 미치는 영향을 최소화 하기 위해 비동기적으로 로드할 필요가 없도록 유용 합니다.
