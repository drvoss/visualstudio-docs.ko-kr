---
title: 스냅숏 디버거에 대 한 시작 페이지
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905270"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>스냅숏 디버거를 시작 하기

Visual Studio 스냅숏 디버거를 서비스에 연결 되 고 디버깅 하는 데 스냅숏 수집을 시작할 수 있습니다.

스냅숏 디버거를 사용 하려면 코드에서 일부 snappoint를 설정, 스냅숏 수집을 시작 하려면 단추를 클릭 하 고 시나리오를 실행 합니다. 실행 코드가 있는 snappoint, 설정한에서 응용 프로그램의 스냅숏을 생성 합니다. 그런 다음 Visual studio 진단 도구 창에서 클릭 하 여 스냅숏을 엽니다. 이제 로컬 것 처럼 서비스에서 스냅숏의 디버그할 수 있습니다. 자세한 내용은 계속 읽어보세요.

## <a name="collect-and-view-snapshots"></a>수집 하 고 스냅숏 보기

스냅숏 디버거는 응용 프로그램에서 스냅숏을 수집합니다. 스냅숏 시점의 시점에 appication의 사진을 같습니다. 시기 및 위치 코드에서 snappoint를 설정 하 여 스냅숏을 수집 하려면 Visual Studio 알려줍니다. Snappoint를 조사 하려는 문제에 대 한 스냅숏을 얻을 수 있는지 확인 해야 하는 조건을 설정 합니다.

### <a name="set-a-snappoint"></a>Snappoint를 설정 합니다.

1. 코드 편집기에서 관심 있는에서 snappoint를 설정 하려면 코드 줄 옆에 있는 왼쪽된 여백을 클릭 합니다. 실행될지 알고 있는 코드 인지 확인 합니다.

    ![편집기에서 snappoint를 설정](../media/snapshot-startpage-set-snappoint.png)

    자주색 육각형 왼쪽 클릭 하면 표시 됩니다.

2. **컬렉션 시작**을 클릭하여 snappoint를 켭니다.

### <a name="open-a-snapshot"></a>스냅숏을 열기

1. Snappoint는 적중 될 때 스냅숏이 오른쪽 위에 있는 진단 도구 창에 표시 됩니다. 창이 열리지 않으면 경우 선택 하 여 열 수 있습니다 **디버깅할** > **Windows** > **진단 도구 표시**합니다.

    ![진단 도구 창에서 스냅숏](../media/snapshot-startpage-diagsession-window.png)

2. 열려는 스냅숏을 두 번 클릭 합니다.

### <a name="inspect-snapshot-data"></a>스냅숏 데이터를 검사 합니다.

DataTips를 보고, 조사식, 지역 변수를 사용 하 여, 호출 하는 변수를 마우스로 가리키면이 보기에서 windows, 스택 및 식 평가 합니다.

웹 사이트 자체는 계속 라이브 상태이며 최종 사용자는 영향을 받지 않습니다. 기본적으로 하나의 스냅숏만 snappoint 당 캡처됩니다. 즉, 스냅숏으로 캡처된 후 snappoint를 해제 합니다. snappoint에서 또 하나의 스냅샷을 캡처하려면 **컬렉션 업데이트**를 클릭하여 snappoint를 다시 켤 수 있습니다.

### <a name="set-a-logpoint"></a>Logpoint를 설정 합니다.

1. Snappoint 아이콘 (자주색 육각형)를 마우스 오른쪽 단추로 클릭 하 고 선택 **설정을**합니다.

2. 에 **Snappoint 설정을** 창에서 **작업**합니다.

    ![Snappoint 조건](../media/snapshot-startpage-logpoint.png)

3. 에 **메시지** 필드에 기록 하려는 로그 메시지를 입력 합니다. 로그 메시지에서 변수를 중괄호 안에 배치하여 변수를 평가할 수도 있습니다.

    선택 하면 **출력 창에 보냅니다**, 메시지는 logpoint 적중 될 때 진단 도구 창에 나타납니다.

    선택 하면 **응용 프로그램 로그 보내기**, 메시지의 메시지에서 볼 수 있는 아무 곳 이나 표시 `System.Diagnostics.Trace` (또는 `ILogger` .NET Core에서), App Insights는 logpoint 적중 될 때 같은 합니다.

## <a name="learn-more"></a>자세한 내용

스냅숏 디버거에 대 한 자세한 정보를 찾을 수 있습니다 합니다 [docs 페이지](../debug-live-azure-applications.md)합니다. 쉽게 버그를 찾는 조건을 설정 하는 방법에 대 한 자세히 알아봅니다.

## <a name="dont-show-me-this-again"></a>다시 표시 안 함

스냅숏 디버거를 연결 하는 경우 스냅숏 디버거 시작 페이지를 다시 표시 안 함, 변경 된 **세션 시작 시 'Getting Started 페이지 표시** 옵션 **도구**  >   **옵션** > **스냅숏 디버거**합니다.

![스냅숏 디버거 도구 옵션 페이지](../media/snapshot-startpage-tools-options.png)
