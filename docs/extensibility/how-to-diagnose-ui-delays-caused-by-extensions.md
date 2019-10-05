---
title: Visual Studio에서 지연 진단 UI 확장 | Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: 00266fd8fbc881707652247e08b093ca4b15a88d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912080"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>방법: 확장으로 인해 발생한 진단 UI 지연

UI가 응답 하지 않음, 리프로 시작 하 고 기본 노력 하 고 Visual Studio UI 스레드의 호출 스택을 검사 합니다. Visual Studio 호출 스택 프레임을 설치 하 고 설정 된 확장의 일부인 모듈에 속해 있는지를 결정 하는 경우 알림을 표시 합니다.

![UI 지연 (무응답) 알림](media/ui-delay-notification-in-vs.png)

알림을 UI 지연 (즉, ui에서 무응답) 되었을 확장에서 코드의 결과 사용자에 게 알립니다. 또한 확장 또는 해당 확장명에 대 한 향후 알림을 사용 하지 않도록 설정 하는 옵션을 사용 하 여 사용자를 제공 합니다.

이 문서에서는 확장 프로그램 코드에서 원인을 UI 지연 알림 진단할 수 있습니다 하는 방법을 설명 합니다.

> [!NOTE]
> 진단 UI 지연 하는 Visual Studio 실험적 인스턴스를 사용 하지 마세요. 필요한 UI 지연 알림에 대 한 호출 스택이 분석의 일부 UI 지연 알림 표시 될 수 있습니다 즉 실험적 인스턴스를 사용 하는 경우 해제 됩니다.

진단 프로세스의 개요는 다음과 같습니다.
1. 트리거 시나리오를 식별 합니다.
2. 로그온 활동을 사용 하 여 VS를 다시 시작 합니다.
3. ETW 추적을 시작 합니다.
4. 다시 표시 하려면 알림을 트리거하십시오.
5. ETW 추적을 중지 합니다.
6. 활동 로그 지연 ID를 가져옵니다.
7. 6 단계에서 지연 ID를 사용 하 여 ETW 추적을 분석 합니다.

다음 섹션에서는 이러한 단계를 자세히 살펴보겠습니다.

## <a name="identify-the-trigger-scenario"></a>트리거 시나리오를 식별합니다

진단 UI 지연 수행 하려면 먼저 어떤 (작업 시퀀스) 하면 Visual Studio 알림 표시를 식별 해야 합니다. 로깅을 켠 나중 알림을 트리거할 수를 제공 하기 위해입니다.

## <a name="restart-vs-with-activity-logging-on"></a>로그온 활동을 사용 하 여 VS를 다시 시작

Visual Studio "활동 로그"를 생성할 수 있습니다 문제를 디버깅 하는 경우 유용한 정보를 제공 합니다. Visual Studio에 로그인 하는 작업을 설정 하려면 사용 하 여 Visual Studio를 열고는 `/log` 명령줄 옵션입니다. Visual Studio가 시작 된 후 활동 로그는 다음 위치에 저장 됩니다.

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

인스턴스 ID에 VS를 찾는 방법에 대 한 자세한 내용은 참조 하십시오 [Tools for Visual Studio 인스턴스 검색 및 관리](../install/tools-for-managing-visual-studio-instances.md)합니다. 이 활동 로그 UI가 지연 및 관련된 알림에 대 한 자세한 정보를 확인 하려면 나중에 사용 됩니다.

## <a name="starting-etw-tracing"></a>ETW 추적 시작

사용할 수 있습니다 [PerfView](https://github.com/Microsoft/perfview/) ETW 추적을 수집 하도록 합니다. PerfView는 ETW 추적을 수집 및 분석에 대 한 사용 하기 쉬운 인터페이스를 제공 합니다. 다음 명령을 사용 하 여 추적을 수집 합니다.

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

이렇게 하면 UI 지연 알림 관련 된 이벤트에 대 한 Visual Studio에서는 공급자 인 "Microsoft VisualStudio" 공급자를 수 있습니다. PerfView를 생성 하는 데 사용할 수 있는 커널 공급자에 대 한 키워드를 지정 하는 **스레드 시간 스택** 보기.

## <a name="trigger-the-notification-to-appear-again"></a>트리거 다시 표시 하려면 알림

PerfView 추적 컬렉션 시작 된 후 다시 표시 하려면 알림에 대 한 트리거 작업 시퀀스 (1 단계)에서 사용할 수 있습니다. 알림이 표시 되 면 PerfView 처리 하 고 추적 출력 파일의 생성에 대 한 추적 수집을 중지할 수 있습니다.

## <a name="stop-etw-tracing"></a>ETW 추적을 중지

추적 컬렉션을 중지 하려면 사용 합니다 **컬렉션 중지** PerfView 창에서 단추입니다. 추적 컬렉션을 중지 하면 PerfView는 ETW 이벤트를 자동으로 처리 됩니다 하 고 추적 출력 파일을 생성 합니다.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>지연 ID를 가져오는 활동 로그를 검사 합니다.

앞에서 설명한 대로 위치의 활동 로그를 찾을 수 있습니다 *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*합니다. Visual Studio UI 지연 확장을 감지 될 때마다에 노드를 사용 하 여 활동 로그에 씁니다 `UIDelayNotifications` 원본으로 합니다. 이 노드에 4 가지 UI 지연에 대 한 정보를 포함:

- UI 지연 ID, UI 지연 VS 세션에서 고유 하 게 식별 하는 일련 번호
- Visual Studio 세션 닫기부터 고유 하 게 식별 하는 세션 ID
- UI 지연에 대 한 알림이 표시 된 여부
- UI 지연 때문에 발생 하는 확장

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> 일부 UI가 지연 알림이 발생합니다. 항상 확인 해야 하므로 합니다 **표시 알림?** 오른쪽 UI 지연 시간을 올바르게 식별 하는 값입니다.

올바른 UI 지연 활동 로그에서를 찾은 후 노드에 지정 된 UI 지연 ID를 적어둡니다. 다음 단계에서는 해당 ETW 이벤트를 검색할 ID를 사용 합니다.

## <a name="analyze-the-etw-trace"></a>ETW 추적 분석

다음으로, 추적 파일을 엽니다. PerfView 또는 새 인스턴스를 시작 하 고 왼쪽 위 창에 추적 파일의 위치에서 현재 폴더 경로 설정 하 여 동일한 인스턴스를 사용 하거나 수행할 수 있습니다.

![Perfview에서 폴더 경로 설정합니다.](media/perfview-set-path.png)

그런 다음 왼쪽된 창에서 추적 파일을 선택 하 고 선택 하 여 엽니다 **엽니다** 마우스 오른쪽 단추 메뉴나 상황에 맞는 메뉴에서.

> [!NOTE]
> 기본적으로 PerfView Zip 보관 파일을 출력합니다. 열면 *trace.zip*를 자동으로 보관 압축을 해제 하 고 추적을 엽니다. 선택을 취소 하 여이 건너뛸 수 있습니다 합니다 **Zip** 추적 수집 하는 동안 상자입니다. 그러나 전송 하 고 여러 컴퓨터에서 추적을 사용 하려는 경우 좋습니다 선택을 취소 합니다 **Zip** 상자입니다. 이 옵션이 없으면 Ngen 어셈블리에 대 한 필수 Pdb에는 추적와 함께 제공 됩니다 하 고 따라서 Ngen 어셈블리의 기호는 확인할 수 없는 대상 컴퓨터에서. (참조 [이 블로그 게시물](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) 어셈블리의 Ngen Pdb에 대 한 자세한 내용은 합니다.)

PerfView 처리 하 여 추적 열에 대 일 분 정도 걸릴 수 있습니다. 추적을 연 후 그 아래 다양 한 "보기"의 목록이 표시 됩니다.

![PerfView 추적에 대 한 요약 보기](media/perfview-summary-view-events-selected.png)

먼저 사용 합니다 **이벤트** UI 지연 시간 범위를 얻으려면 보기:

1. 엽니다는 **이벤트** 뷰를 선택 하 여 `Events` 추적 노드에서 선택한 **열기** 마우스 오른쪽 단추 메뉴나 상황에 맞는 메뉴에서.
2. 선택 "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" 왼쪽된 창에서.
3. Enter 키를 누릅니다.

선택 영역에 적용 됩니다 및 모든 `ExtensionUIUnresponsiveness` 오른쪽 창에서 이벤트가 표시 됩니다.

![이벤트 보기에서 이벤트를 선택합니다.](media/perfview-event-selection.png)

오른쪽 창에서 각 행 UI 지연에 해당합니다. 6 단계에서 활동 로그에서 지연 ID와 일치 해야 하는 "지연 ID" 값을 포함 하는 이벤트입니다. 이후 `ExtensionUIUnresponsiveness` 발생 UI 지연, 이벤트의 타임 스탬프의 끝 (거의) 표시 UI 지연의 종료 시간입니다. 또한 이벤트 지연 기간을 포함합니다. UI 지연 시작 될 때의 타임 스탬프를 가져오려면 종료 타임 스탬프에서 기간을 뺄 수 했습니다.

![UI 지연 시간 범위를 계산합니다.](media/ui-delay-time-range.png)

이전 스크린샷에서 예를 들어 이벤트의 타임 스탬프 12,125.679 이며 지연 시간은 6,143.085 (밀리초)입니다. 그러므로
* 지연 시작은 12,125.679 6,143.085 5,982.594 =.
* UI 지연 시간 범위를 12,125.679 5,982.594입니다.

개 닫을 수 시간 범위에 있으면 합니다 **이벤트** 를 열고 표시 합니다 **(StartStop 작업과) 시간 스레드 스택** 보기. 이 보기 UI 스레드를 차단 하는 확장 종종 다른 스레드는 I/o 바인딩된 작업에 단순히 기다리고 있으므로 특히 유용 합니다. 따라서 합니다 **CPU 스택** 보기 대부분의 경우에 대 한 옵션으로, 즉, 스레드가 있으므로 시간 동안 CPU 사용 하지 않는 차단 시간을 캡처하지 않습니다 수 있습니다. 합니다 **스레드 시간 스택** 제대로 표시 차단 시간을 기준으로이 문제를 해결 합니다.

![PerfView 요약 뷰에서 스레드 시간 (StartStop 작업과) 스택 노드](media/perfview-thread-time-with-startstop-activities-stacks.png)

여는 동안 **스레드 시간 스택** 보기를 선택 합니다 **devenv** 분석을 시작 하는 프로세스입니다.

![스레드 UI 지연 분석에 대 한 시간 스택 뷰](media/ui-delay-thread-time-stacks.png)

에 **스레드 시간 스택** 보기에서 페이지의 위쪽 왼쪽에 설정할 수 있습니다 시간 범위 값을 계산 하는 이전 단계에서 키를 누릅니다 **Enter** 스택을 시간 범위를 조정 하도록 합니다.

> [!NOTE]
> UI 스레드 결정 (시작) 스레드 추적 컬렉션이 이미 Visual Studio를 연 후 시작 된 경우에 예상치 않은 될 수 있습니다. 그러나 (시작) UI 스레드의 스택에 첫 번째 요소는 가장 가능성이 높은 항상 운영 체제 Dll (*ntdll.dll* 하 고 *kernel32.dll*) 뒤 `devenv!?` 차례로 `msenv!?` . 이 시퀀스를 UI 스레드를 식별할 수 있습니다.

 ![시작 스레드를 식별합니다.](media/ui-delay-startup-thread.png)

또한 패키지에서 모듈을 포함 하는 스택을 포함 하 여이 보기를 필터링 할 수 있습니다.

* 설정할 **GroupPats** 기본적으로 추가 하는 모든 그룹화 제거 하려면 빈 텍스트입니다.
* 설정할 **IncPats** 기존 프로세스 필터 외에도 어셈블리 이름의 일부를 포함 합니다. 이 예에서 것 **devenv; UIDelayR2**합니다.

![시간 스택 스레드 보기에서 GroupPath 및 IncPath 설정](media/perfview-tts-group-path-inc-path.png)

PerfView에서 자세하게에 **도움말** 코드에서 성능 병목 현상을 식별 하는 데 사용할 수 있는 메뉴. 또한 다음 링크는 스레딩 Api 코드를 최적화 하기 위해 Visual Studio를 활용 하는 방법에 자세한 정보를 제공 합니다.

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

확장에 대 한 새 Visual Studio 정적 분석기를 사용할 수도 있습니다 (NuGet 패키지 [여기](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers))을 효율적으로 확장을 작성 하기 위한 모범 사례 지침을 제공 하는 합니다. 목록을 보려면 [VS SDK 분석기](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) 하 고 [분석기 스레딩](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)합니다.

> [!NOTE]
> 종속성으로 인해 응답 하지 않는 문제를 해결할 수 없는 경우 없는 컨트롤을 통해 (예를 들어 경우 UI 스레드에서 동기 VS 서비스를 호출 하는 경우 확장 프로그램), 그에 관해 하고자 합니다. Visual Studio 파트너 프로그램의 구성원 인 경우 개발자 지원 요청을 제출 하 여 문의할 수 있습니다. 그렇지 않으면 '문제 보고' 도구를 사용 하 여 여러분의 의견을 제출 하 여 포함할 `"Extension UI Delay Notifications"` 제목에서입니다. 또한 분석에 대 한 자세한 설명을 포함 하세요.
