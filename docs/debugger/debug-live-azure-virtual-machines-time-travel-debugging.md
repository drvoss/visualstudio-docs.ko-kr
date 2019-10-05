---
title: 시간 여행 디버깅 라이브 ASP.NET Azure virtual machines
description: 기록 스냅숏 디버거를 사용 하 여 Azure virtual machines에서 라이브 ASP.NET 앱을 재생 하는 방법을 알아봅니다.
ms.custom: ''
ms.date: 04/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 53dce8b6b468dd5754b5708afccdcbe6cb908d1d
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432221"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>스냅숏 디버거를 사용 하 여 Azure virtual machines의 기록 및 재생 라이브 ASP.NET 앱

Visual Studio Enterprise에서 시간 여행 디버깅 (TTD) 미리 보기는 Azure 가상 머신 (VM)에서 실행 하는 웹 앱을 기록 하는 기능을 제공 하 고 정확 하 게 재구성 하 고 재생 실행 경로입니다. TTD는 스냅숏 디버거를 사용 하 여 통합 및 격리 하 고 프로덕션 환경에만 발생할 수 있는 문제를 식별할 수 있도록 하려는 모든 횟수 되감고 각 코드 줄을 재생할 수 있습니다.

TTD 녹음/녹화를 캡처할 응용 프로그램이 중단 되지 됩니다. 그러나 TDD 기록 프로세스 크기 및 활성 스레드 수를 포함 하는 요인에 따라 낮춰 실행 중인 프로세스에 상당한 오버 헤드를 추가 합니다.

이 기능은 라이브 이동 라이선스를 사용 하 여 Visual Studio 2019 릴리스의 대 한 미리 보기로 제공 됩니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * 시간 여행 디버깅 하도록 설정한 스냅숏 디버거를 시작 합니다.
> * Snappoint를 설정 하 고 수집 시간 여행 기록
> * 한 번 디버깅을 시작 기록 이동

## <a name="prerequisites"></a>전제 조건

* Visual Studio 2019 Enterprise에 대 한 사용 가능한 이상만 시간 여행 디버깅에 대 한 Azure VM (Virtual Machines)의 **Azure 개발 워크 로드**합니다. (**개별 구성 요소** 탭의 **디버깅 및 테스트** > **스냅샷 디버거**에서 찾을 수 있습니다.)

    설치 되어 있지 않은 경우 설치할 [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)합니다.

* 시간 여행 디버깅 하는 것은 다음 Azure VM 웹 앱을 사용할 수 있습니다.
  * ASP.NET 응용 프로그램 (AMD64).NET Framework 4.8 이상을 실행 하 고 있습니다.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>시간 여행 디버깅 하도록 설정한 스냅숏 디버거를 시작 합니다.

1. 프로젝트를 열고 시간을 수집 하려는에 대 한 기록 이동 합니다.

    > [!IMPORTANT]
    > TTD를 시작 하려면 열기 해야 합니다 *동일한 버전의 소스 코드* Azure VM 서비스에 게시 된 합니다.

1. **디버그 > 스냅숏 디버거 연결...** 을 선택합니다. 웹 앱에 배포 된 Azure VM 및 Azure storage 계정을 선택 합니다. 선택 합니다 **시간 여행 디버깅을 활성화** 옵션 미리 보기 및 클릭 **연결**합니다.

      ![Azure 리소스 선택](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > 처음 VM의 **스냅샷 디버거 연결**을 선택하면 IIS가 자동으로 다시 시작됩니다.

    에 대 한 메타 데이터를 **모듈** 처음 활성화 되어 있지 않습니다. 웹 앱으로 이동 하며 **수집 시작** 단추가 다음 활성화 됩니다. Visual Studio가 이제 스냅샷 디버깅 모드입니다.

   ![스냅샷 디버깅 모드](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Insights 사이트 확장도 스냅샷 디버깅을 지원합니다. “사이트 확장이 최신 상태가 아님” 오류 메시지가 표시되면 [스냅숏 디버깅에 대한 문제 해결 팁 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md)에서 업그레이드 세부 정보를 참조하세요.

   합니다 **모듈** 창에 표시 되는 Azure VM에 대 한 모든 모듈 로드 되는 경우 (선택 **디버그 > Windows > 모듈** 이 창을 열려면).

   ![모듈 창 확인](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Snappoint를 설정 하 고 수집 시간 여행 기록

1. 코드 편집기에서 snappoint를 설정 하려면 원하는 메서드에서 왼쪽된 여백을 클릭 합니다. 실행 예정임을 알고 있는 코드인지 확인하세요.

   ![snappoint 설정](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Snappoint (속이 빈 공) 아이콘을 마우스 오른쪽 단추로 클릭 하 고 선택 **작업**합니다. 에 **스냅숏 설정을** 창 클릭 합니다 **작업** 확인란 합니다. 다음을 클릭 합니다 **이 메서드의 끝에 시간 여행 추적을 수집** 확인란 합니다.

   ![메서드의 끝에 시간 여행 추적을 수집 합니다.](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. **컬렉션 시작**을 클릭하여 snappoint를 켭니다.

   ![snappoint 켜기](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>스냅샷 가져오기

Snappoint를 켤 때의 snappoint를 배치할 코드 줄이 실행 될 때마다 스냅숏을 캡처합니다. 이 실행은 서버의 실제 요청에 의해 발생할 수 있습니다. 강제로 snappoint가 적중되도록 하려면 웹 사이트의 브라우저 보기로 이동하여 snappoint가 적중되도록 하는 데 필요한 모든 작업을 수행하세요.

## <a name="start-debugging-a-time-travel-recording"></a>한 번 디버깅을 시작 기록 이동

1. snappoint가 적중되면 진단 도구 창에 스냅샷이 표시됩니다. 이 창을 열려면 **디버그 > Windows > 진단 도구 표시**를 선택합니다.

   ![snappoint 열기](../debugger/media/snapshot-diagsession-window.png)

1. 코드 편집기에서 기록 시간 이동 열에 대 한 스냅숏 보기 링크를 클릭 합니다.
  
   TTD를 사용 하 여 기록한 코드의 모든 줄을 실행할 수 있습니다 합니다 **계속** 하 고 **계속 역방향** 단추입니다. 또한 합니다 **디버그** 도구 모음에 사용할 수 있습니다 **다음 문 표시**, **단계씩**, **프로시저 단위 실행**, **프로시저 나가기**, **로 돌아가**, **뒤로 건너뛰기**를 **단계 다시**입니다.

   ![디버깅 시작](../debugger/media/time-travel-debugging-step-commands.png)

   사용할 수도 있습니다는 **지역**를 **조사식**, 및 **호출 스택** windows 식을 평가 합니다.

   ![스냅샷 데이터 검사](../debugger/media/time-travel-debugging-start-debugging.png)

    라이브 상태인 웹 사이트 자체 이며 모든 후속 TTD 활동에서 최종 사용자에 게 영향 되지 않습니다. 기본적으로 snappoint당 하나의 스냅샷만 캡처됩니다. 하나의 스냅샷이 캡처되면 해당 snappoint가 꺼집니다. snappoint에서 또 하나의 스냅샷을 캡처하려면 **컬렉션 업데이트**를 클릭하여 snappoint를 다시 켤 수 있습니다.

**도움이 필요하세요?** [문제 해결 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md)와 [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md) 페이지를 참조하세요.

## <a name="set-a-conditional-snappoint"></a>조건부 snappoint 설정

앱의 특정 상태를 다시 만들기 어려운 경우 조건부 snappoint 사용이 도움이 될 수 있는지 고려해보세요. 수집 된 시간을 방지 하는 조건부 snappoint 도움말 앱 변수 검사 하려는 특정 값에 하는 경우와 같이 원하는 상태가 될 때까지 기록 이동 합니다. [적중 횟수 또는 필터 식을 사용 하는 조건을 설정](../debugger/debug-live-azure-apps-troubleshooting.md)합니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 Azure Virtual Machines에 대 한 기록 된 시간 이동 수집 하는 방법을 알아보았습니다. 스냅숏 디버거에 대 한 자세한 정보를 읽을 수도 있습니다.

> [!div class="nextstepaction"]
> [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md)