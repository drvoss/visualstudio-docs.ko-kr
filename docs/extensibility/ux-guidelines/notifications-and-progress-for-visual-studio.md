---
title: Visual Studio의 알림 및 진행률 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5ca3f02c37a76e31ad76f6875110487dffefd49
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310881"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Visual Studio의 알림 및 진행률
## <a name="BKMK_NotificationSystems"></a> 알림 시스템

### <a name="overview"></a>개요
 사용자에 게 소프트웨어 개발 작업에 대 한 Visual Studio에서 일어나는 방법은 여러 가지가 있습니다.

 모든 종류의 알림 구현 하는 경우:

- **최소값으로 알림 횟수를 유지** 유효 숫자입니다. 알림 메시지는 대부분의 Visual Studio 사용자 또는 특정 기능 영역 사용자에 게 적용 해야 합니다. 알림의 과도 하 게 사용 하 여 사용자 sidetrack 수도 인식된 시스템의 사용 편의성을 저하 있습니다.

- **명확 하 고 조치 가능한 메시지를 표시 하는 확인** 사용자 보다 복잡 한 선택 항목을 만들고 추가 작업을 수행 하는 것에 대 한 적절 한 컨텍스트를 호출 하는 데 사용할 수 있는 합니다.

- **동기 및 비동기 메시지를 적절 하 게 제공 합니다.** 동기 알림을 즉각적인 주의가 필요한 항목을 웹 서비스 충돌 하는 경우 또는 코드와 같은 예외가 발생을 나타냅니다. 모달 대화 상자에서와 같이 해당 입력이 필요한 방식 바로 이러한 경우 사용자를 알려야 합니다. 비동기 알림은 사용자에 대해 알아야 하지만 필요 하지를 즉시 취할 수 있도록 웹 사이트 배포를 완료 하는 빌드 작업이 완료 될 때 또는 같은 것입니다. 이러한 메시지 보다 앰비언트 있고 사용자의 작업 흐름을 중단 하지 않습니다.

- **사용자 추가 작업을 수행 하는 것을 금지 하는 데 필요한 경우에 모달 대화 상자를 사용 하 여** 메시지를 승인 하거나 대화 상자에 표시 되는 결정 하기 전에 합니다.

- **유효한 더 이상 없을 때 앰비언트 알림을 제거 합니다.** 에 대 한 알림을 받은 이러한 문제를 해결 하는 작업 이미 있는 경우 알림을 해제 하려면 사용자는 필요 하지 않습니다.

- **잘못 된 상관 관계 알림은 발생할 수 있습니다는 알아야 합니다.** 사용자가 하나 이상의 해당 작업을 트리거한 알림을 사실 했습니다 인과 관계가 없는 경우 생각할 수 있습니다. 컨텍스트, 트리거 및 알림 메시지의 원본에 대 한 알림 메시지 지우기 이어야 합니다.

### <a name="choosing-the-right-method"></a>적합 한 방법 선택
 이 표를 사용 하 여 메시지의 사용자에 게 적합 한 방법 선택 하는 데 도움이 됩니다.

|메서드|사용|사용 하지 마세요|
|------------|---------|----------------|
|[모달 오류 메시지 대화 상자](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|사용자 응답을 계속 하기 전에 필요한 경우 사용 합니다.|사용자를 차단 하 고 해당 흐름을 중단 하지 않아도 경우 사용 하지 마세요. 줄어들었습니다, 다른 방식으로 메시지를 표시 하는 것이 불가능 한 경우 모달 대화 상자를 사용 하지 마십시오.|
|[IDE 상태 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|프로세스의 상태와 관련 된 앰비언트 텍스트 정보가 있으면 사용 합니다.|단독으로 사용 하지 마세요. 다른 의견 보내기 메커니즘을 사용 하 여 함께에서 가장 적합합니다.|
|[포함 된 정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|도구 창이 나 문서 창에 진행률, 오류 상태, 결과 및/또는 실행 가능한 정보에 알리기 위해 사용 합니다.|정보 infobar를 배치할 위치와 관련이 없는 경우 사용 하지 마십시오.<br /><br /> 문서/도구 기간을 벗어나 사용 하지 마세요.|
|[마우스 커서가 변경](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|프로세스 것임을 알리기 위해 사용할 수 있습니다. 마우스 커서가 그리기 모드와 같은 특정 모드에서 끌어서 놓기 또는 진행 하는 경우와 같은 마우스 상태 변경이 있다는 것을 알리는 데 사용도.|짧은 진행 중인 변경에 대 한 사용 하지 않거나 경우의 펄럭이는 커서 가능성이 있습니다 (예를 들어 경우 대신 전체 프로세스를 더 오래 실행 중인 프로세스의 부분에 연결).|
|[진행률 표시기](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|(비활성화 상태 또는 결정 되지 않은) 진행률을 보고 해야 하는 경우 사용 합니다. 진행률 표시기 유형이 및 각각에 대 한 특정 사용 하는 여러 가지가 있습니다. 참조 [진행률 표시기](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)합니다.||
|[Visual Studio 알림 창](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|알림 창을 공개적으로 확장할 수 없습니다. 그러나 다양 한 라이선스와 Visual Studio로 또는 패키지에 업데이트 정보 알림을 중요 한 문제를 포함 하 여 Visual Studio에 대 한 메시지를 통신에 사용 됩니다.|다른 유형의 알림 사용 하지 마세요.|
|[오류 목록](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|문제 (오류/경고/정보)에 문제가 사용자의 현재 열려 있는 솔루션에 직접 연결을 하는 경우 코드에서 작업을 수행 해야 할 수 있습니다.<br /><br /> 이 예를 포함 합니다.<br /><br /> 컴파일러 메시지 (오류/경고/정보)<br /><br /> 코드에 대 한 코드 분석/진단 메시지<br /><br /> --메시지를 작성 하는 중<br /><br /> 프로젝트 또는 솔루션 파일에 관련 된 문제에 대 한 적절 한 수 있지만 먼저 솔루션 탐색기를 표시 하는 것이 좋습니다.|모든 사용자의 열려 있는 솔루션 코드 관련이 없는 항목에 대 한 사용 하지 마세요.|
|편집기 알림: 밝은 전구|열려 있는 파일에 존재 하는 문제를 해결할 수 있는 수정 해야 하는 경우 사용 합니다.<br /><br /> 전구는 또한 주문형, 리팩터링, 같은 사용자의 코드에서 수행 되는 경우 "알림 스타일입니다."를 표시 되지 것입니다 빠른 작업을 호스트 하기 위한 사용 가능|열린 파일에 모든 관계 없는 항목에 대 한 사용 하지 마세요.|
|편집기 알림: 오류 표시선|사용 하 여 사용자가 열려 있는 코드 (예를 들어, 오류에 대 한 빨간색 구부러진)의 특정 범위를 사용 하 여 문제를 알립니다.|가 열려 있는 코드의 특정 범위에 있는 항목에 대해 사용 하지 마세요.|
|[포함 된 상태 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|사용 하 여 콘텐츠 또는 특정 도구 창, 문서 창 또는 대화 상자 창의 컨텍스트 내에서 프로세스와 관련 된 상태를 제공 합니다.|일반적인 제품 알림, 프로세스 또는 특정 창 내에서 콘텐츠를 모든 관계 없는 항목에 대 한 사용 하지 마세요.|
|[Windows 트레이 알림](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|-의-out-proc 프로세스에 대 한 알림 화면 또는 응용 프로그램을 도우미를 사용 합니다.|IDE와 관련 된 알림을 사용 하지 마세요.|
|[알림 거품형](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|원격 프로세스를 미리 알리거나 변경 하는 데 **외부** IDE입니다.|프로세스의 사용자에 게 알리기 위한 수단으로 사용 하지 마세요 **내에서** IDE.|

### <a name="notification-methods"></a>알림 방법

#### <a name="BKMK_ModalErrorMessageDialogs"></a> 모달 오류 메시지 대화 상자
 모달 오류 메시지 대화 상자는 사용자의 확인 또는 작업 해야 하는 오류 메시지를 표시 하는 데 사용 됩니다.

 ![모달 오류 메시지](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")

 **데이터베이스에 잘못 된 연결 문자열의 사용자에 게 알리는 모달 오류 메시지 대화 상자**

#### <a name="BKMK_IDEStatusBar"></a> IDE 상태 표시줄
 사용자 상태 표시줄 텍스트를 확인 하는 가능성 다방면 컴퓨터 환경 및 Windows 플랫폼을 사용 하 여 특정 환경에 상호 연결 합니다. 기본 Visual Studio 고객도 잘 알고 있는 Windows 사용자 상태 표시줄에 대 한 변경 내용을 놓칠 수 있지만 두 영역에 숙련 되도록는 경향이 있습니다. 따라서 상태 표시줄 가장 사용할지 확인용으로 중복 신호로 정보가 다른 곳에서 표시에 대 한 합니다. 알림 도구 창 또는 대화 상자에서 모든 종류의 사용자를 즉시 해결 해야 하는 중요 한 정보를 제공 합니다.

 Visual Studio 상태 표시줄은 여러 유형의 정보 표시할 수 있도록 설계 되었습니다. 이 피드백, 디자이너, 진행률 표시줄, 애니메이션 및 클라이언트에 대 한 영역으로 구분 됩니다.

 피드백 영역 및 디자이너 영역이 항상 표시 됩니다. 진행률 표시줄 및 애니메이션 영역은 항상 동적이 고 사용자 컨텍스트 기반입니다. 디자이너 영역에 문자 메시지에 대 한 해당 리소스에서 끌어온 구성 인 하는 문자열의 길이 따라 다르며 고정 폭이 지정 합니다. 따라서 지역화가 된 코드 변경 없이 너비를 조정할 수 있습니다. 영어의 경우이 문자열의 너비는 약 220 픽셀입니다. 디자이너 영역 정상적으로 동작 합니다 및 피드백 영역에는 나머지 공간을 처리 합니다.

 상태 표시줄도 디버그 모드에서 IDE의 경우와 같은 다양 한 IDE 상태 변경을 통신 하 여 시각적 효과 기능 값을 추가할 색이 지정 됩니다.

 ![IDE 상태 표시줄 색 변경](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")

 **IDE 상태 표시줄 색상**

#### <a name="BKMK_EmbeddedInfobar"></a> 포함 된 정보 표시줄
 정보 표시줄을 상태 또는 조건의 사용자에 게 알려 문서 창이 나 도구 창의 맨 위에 있는 사용할 수 있습니다. 또한 사용자는 쉽게 작업을 수행 하는 방법의 그려볼 수 있습니다. 있도록 명령을 제공할 수 있습니다. 정보 표시줄 표준 셸 컨트롤입니다. 작동 되며 IDE에서 다른 사용자와 일치 하지 않는 표시는 사용자를 만들지 마세요. 참조 [표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) 구현 세부 정보 및 사용 지침에 대 한 합니다.

 ![Infobar 포함](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")

 **기록 디버깅 모드에는 IDE 및 편집기는 표준 디버깅 모드에서와 동일한 방식으로 응답 하지 않습니다 하는 사용자에 게 알리는 문서 창에서 정보 표시줄을 포함 합니다.**

#### <a name="BKMK_MouseCursorChanges"></a> 마우스 커서가 변경
 마우스 커서를 변경할 때 VSColor service에 연결 되어 있으며 커서와 연결 되어 있는 색을 사용 합니다. 커서가 진행 중인 작업을 나타내는 데 사용할 수 뿐만 아니라 끌어, 놓을, 또는 개체를 선택 하는 데 수 있는 대상을 사용자가 마우스로 영역을 적중 합니다.

 더 이상 모든 입력 표현에서 사용자를 방지 하는 작업에 대 한 모든 사용 가능한 CPU 시간을 예약 해야 하는 경우에 사용 중/대기 마우스 커서를 사용 합니다. 다중 스레딩을 사용 하는 잘 작성 된 응용 프로그램을 사용 하 여 대부분의 경우, 사용자에서 다른 작업을 수행할 수 없습니다 경우 시간이 거의 발생 하지 않아야 합니다.

 정보에 대 한 중복 신호 다른 곳에서 제공 하는 대로 커서가 유용 하다는 것을 염두에 두십시오. 사용자 해결 해야 하는 중요 한 항목을 전달 하려고 하는 경우에 특히 사용자와의 통신의 유일한 방법으로 커서 변경에 의존 하지 않습니다.

#### <a name="BKMK_NotSysProgressIndicators"></a> 진행률 표시기
 진행률 표시기는 데 몇 초가 걸리는 프로세스 중 사용자에 게 피드백을 제공 하는 것에 대 한 중요 합니다. 진행률 표시기를 표시할 수 있습니다 (near 시작 지점 진행 중인 작업의)에 포함 된 상태 표시줄에, 모달 대화 상자에서 또는 전체 Visual Studio 상태 표시줄에 있습니다. 지침을 따르세요 [진행률 표시기](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) 용도 구현에 대 한 합니다.

#### <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio 알림 창
 Visual Studio 알림 창에 라이선스, 환경 (Visual Studio), 확장 및 업데이트 하는 방법에 대 한 개발자를 게 알립니다. 사용자는 개별 알림을 해제할 수 또는 특정 종류의 알림 무시 하도록 선택할 수 있습니다. 무시 된 알림 목록에서 관리 되는 **도구 > 옵션** 페이지입니다.

 알림 창을 현재 확장할 수 없습니다.

 ![Visual Studio 알림 창](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")

 **Visual Studio 알림 도구 창**

#### <a name="BKMK_ErrorList"></a> 오류 목록
 오류 목록에서 알림을 컴파일하는 동안 발생 또는 및 프로세스를 빌드 및 코드는 특정 코드 오류를 이동할 수 있도록 하는 오류 및 경고를 나타냅니다.

 ![오류 목록](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")

 **Visual Studio 오류 목록**

#### <a name="BKMK_EmbeddedStatusBars"></a> 포함 된 상태 표시줄
 활성 문서 창이 고 사용자의 컨텍스트 및/또는 시스템 응답에서 업데이트 정보로 해당 클라이언트 영역 컨텍스트를 사용 하 여 IDE 상태 표시줄에는 동적 이기 때문에 어렵습니다 정보의 연속 표시를 유지 관리 또는 장기의 상태를 지정 합니다. 비동기 처리 합니다. 예를 들어, IDE 상태 표시줄에는 여러 실행 및/또는 즉시 실행 가능한 항목이 선택 항목에 대 한 테스트 실행 결과의 알림에 적합 하지 않습니다. 사용자가 항목을 선택 하거나 프로세스를 시작 있는 문서 또는 도구 창의 컨텍스트에서 이러한 상태 정보를 유지 하는 것이 반드시 합니다.

 ![포함 된 상태 표시줄](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")

 **Visual Studio에 포함 된 상태 표시줄**

#### <a name="BKMK_WindowsTray"></a> Windows 트레이 알림
 Windows 작업 표시줄의 알림 영역은 시스템 옆에 있는 Windows 클록입니다. 다양 한 유틸리티와 소프트웨어 구성 요소 사용자 화면 해상도 변경 하거나 소프트웨어 업데이트를 가져오는 등의 시스템 작업에 대 한 상황에 맞는 메뉴를 얻을 수 있도록이 영역에서 아이콘을 제공 합니다.

 환경 수준 알림은 Windows 알림 영역 Visual Studio 알림 허브에 표시 해야 합니다.

#### <a name="BKMK_NotificationBubbles"></a> 알림 거품형
 알림 거품형 정보는 편집기/디자이너 내에서 또는 Windows 알림 영역의 일부로 나타날 수 있습니다. 사용자에 게 이러한 거품은 나중에 확인할 수 있는 문제는 중요 하지 않은 알림에 유용 합니다. 거품은 사용자를 즉시 해결 해야 하는 중요 한 정보에 대 한 적합 하지 않습니다. 알림 거품형 Visual Studio를 사용 하는 경우에 따라 합니다 [알림 거품에 대 한 Windows 데스크톱 지침](/windows/desktop/uxguide/mess-notif)합니다.

 ![알림 거품형](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")

 **Visual Studio에 사용 되는 Windows 알림 영역에서 알림 거품형**

## <a name="BKMK_ProgressIndicators"></a> 진행률 표시기

### <a name="overview"></a>개요
 진행률 표시기는 사용자에 게 피드백을 제공 하는 것에 대 한 알림 시스템의 중요 한 부분입니다. 프로세스 및 작업 완료 되 면 사용자를 알 수 있습니다. 친숙 한 표시 형식에는 진행률 표시줄, 회전 커서 및 애니메이션된 아이콘 포함 됩니다. 형식 및 진행률 표시기의 배치를 보고 되는 것을 포함 하는 컨텍스트 및 기간 프로세스 또는 작업 완료에 소요 될에 따라 달라 집니다.

#### <a name="factors"></a>요소
 표시기 유형은 적합 한 결정을 하기 위해 다음 요소를 확인 해야 합니다.

1. **타이밍:** 시간의 길이 작업은 시간이 걸립니다.

2. **형식:** 작업 (잠금 프로세스가 완료 될 때까지 UI) 환경에 모달 인지 여부

3. **영구/임시:** 진행률의 최종 결과 나중에 보고 및/또는 볼 수 있는 가능 해야 하는 여부

4. **비활성화 상태/비활성:** 작업 종료 시간 및 진행률을 계산할 수 있는지 여부

5. **그래픽/Textual 위치:** 진행 상황이 나 프로세스 인지 트리 컨트롤 등의 컨트롤을 특정 메시지의 본문에 캡처된 인라인

6. **근접:** 관련이 있는 UI에 가깝게에서 진행률 여야 하는지 여부입니다. (예를 들어 멀리 될 수 있는 상태 표시줄에 있을 수 있습니다 또는 프로세스를 시작 하는 단추 옆에 있어야 있습니까)?

#### <a name="determinate-progress"></a>활성화 상태의 진행률

|진행 유형|시기 및 사용 하는 방법|노트|
|-------------------|-------------------------|-----------|
|진행률 표시줄 (비활성화 상태)|예상 기간 > 5 초입니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함 될 수 있습니다.|**없는** 애니메이션에 텍스트를 포함 합니다.|
|정보 표시줄|상황에 맞는 UI와 사용 하 여 연결 된 메시징 하십시오. 참조 [표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)합니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함 될 수 있습니다.|**없는** 여러 프로세스를 표시 해야 할 때 여러 정보 표시줄을 사용 합니다. 누적된 진행률 표시줄을 대신 사용 합니다.|
|출력 창|일시적인 알림: 해당 사용자가 해야 할 응용 프로그램 수준 프로세스 **검토** 완료 된 후의 세부 정보입니다.|**없는** 사용자 데이터를 나중에 참조 해야 하는 경우 사용 합니다.|
|로그 파일|이를 중요 한 경우에서 intransient 알림을 사용 하 여 쌍을 이루는 **저장할** 완료 한 후 세부 정보입니다.||
|상태 표시줄|일시적인 알림: 응용 프로그램 수준 프로세스는 사용자에 게 **필요가** 완료 된 후의 세부 정보입니다.<br /><br /> 포함 된 진행률 표시줄을 포함합니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함 될 수 있습니다.||

#### <a name="indeterminate-progress"></a>비활성화 상태의 진행률

|진행 유형|시기 및 사용 하는 방법|노트|
|-------------------|-------------------------|-----------|
|진행률 표시줄 (비활성화 상태)|예상 기간 > 5 초입니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함 될 수 있습니다.|**없는** 애니메이션에 텍스트를 포함 합니다.|
|Ants (애니메이션된 가로 점)|서버에 왕복 합니다.<br /><br /> 부모 컨테이너의 맨 위에 가로질러 near 지점의 컨텍스트를 배치 합니다.|**없는** 없습니다 전체 컨테이너에 의해 부모로 지정 하는 경우 사용 합니다.|
|스핀 상자 (진행률 링)|상황에 맞는 UI 나 공간이 고려 사항에 연결 하는 프로세스입니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함 될 수 있습니다.||
|정보 표시줄|상황에 맞는 UI와 사용 하 여 연결 된 메시징 하십시오. 참조 [표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)합니다.|**없는** 여러 프로세스를 표시 해야 할 때 여러 정보 표시줄을 사용 합니다. 누적된 진행률 표시줄을 대신 사용 합니다.|
|출력 창|일시적인 알림: 응용 프로그램 수준 프로세스는 사용자를 할 **검토** 완료 된 후의 세부 정보입니다.|**없는** 세션 간에 유지 해야 하는 정보를 사용 합니다.|
|로그 파일|이를 중요 한 경우에서 intransient 알림을 사용 하 여 쌍을 이루는 **저장할** 완료 한 후 세부 정보입니다.||
|상태 표시줄|일시적인 알림: 응용 프로그램 수준 프로세스는 사용자에 게 **필요가** 완료 된 후의 세부 정보입니다.<br /><br /> 포함 된 진행률 표시줄을 포함합니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함 될 수 있습니다.||

### <a name="progress-indicator-types"></a>진행률 표시기 유형이

#### <a name="progress-bars"></a>진행률 표시줄

##### <a name="indeterminate"></a>비활성화
 ![비활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")

 **비활성화 상태의 진행률 표시줄**

 "비활성화"는 작업의 전반적인 진행 상황을 의미 하거나 프로세스를 확인할 수 없습니다. 비활성화 상태의 진행률 표시줄을 사용 하 여 제한 된 시간을 필요로 하는 작업에 대 한 또는 액세스 하는 개체의 수 알된 수 있습니다. 상황에 대 한 텍스트 설명을 사용 합니다. 시간 기반 연산으로 범위를 제공 하려면 시간 초과 사용 합니다. 비활성화 상태의 진행률 표시줄 진행 상황, 수행 되는 어떠한 다른 정보도 제공 표시할 애니메이션을 사용 합니다. 만 기반으로 정확도 가능한 부족 부정형 진행률 표시줄을 선택 하지 마십시오.

##### <a name="determinate"></a>비활성화 상태
 ![활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")

 **활성화 상태의 진행률 표시줄**

 "비활성화"는 작업 또는 프로세스에 필요 함을 의미는 제한 된 기간 동안 시간을 정확 하 게 예측할 수 없는 경우에 합니다. 명확 하 게 완료를 표시 합니다. 작업이 완료 된 경우가 아니면 100%로 이동 하는 진행률 표시줄을 허용 하지 마십시오. 활성화 상태의 진행률 표시줄 애니메이션 0에서 100% 왼쪽-오른쪽 이동합니다.

 작업 중 이전 버전과 진행률 표시기를 이동 하지 않습니다. 막대는 앞으로 이동 꾸준히 작업이 시작 되 면 하 고 종료 될 때 100%에 도달 해야 합니다. 진행률 표시줄의 점은 사용자 전체 작업이 걸리는, 얼마나 많은 단계는 관계 없이 알 수 있도록 합니다.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>동시 (누적된 진행률 표시줄)를 보고 합니다.
 작업-시간이 오래 걸리는 경우 아마도 몇 분-다음 두 가지 진행률 표시줄 사용할 수, 작업에 대 한 전반적인 진행률 및 현재 단계를 진행 하는 다른 표시 하는 하나입니다. 예를 들어, 설치 프로그램은 여러 파일에 복사 하는 경우 하나의 진행률 표시줄 시간 전체 프로세스는 두 번째는 현재 파일의 비율을 나타낼 수 있습니다 또는 디렉터리를 복사 하는 동안 가리키는 데 있습니다. 5 개 동시 작업 또는 누적된 진행률 표시줄을 사용 하 여 프로세스를 보고 하지 않습니다. 5 개 동시 작업 또는 보고서에 대 한 프로세스에 있는 경우 사용 하 여 모달 대화 상자를 취소 단추와 보고서를 출력 창에 진행률 세부 정보.

##### <a name="textual-descriptions"></a>텍스트 설명
 완료 될 때까지 예상 시간과 함께 발생 하는 상황에 대 한 텍스트 설명을 사용 합니다. 작업은 얼마나 걸리나요 확인할 수 없는 경우 진행률 표시줄을 하지 않고 애니메이션된 아이콘 피드백을 제공 하는에 보다 적합할 수 있습니다.

 Visual Studio는 Visual Studio 통합 제품에서 사용할 수 있는 상태 표시줄에 표준 진행률 표시줄을 제공 합니다. 진행률 표시줄의 애니메이션을 적용 하는 동안 발생 하는 텍스트 설명에 대 한 상태 표시줄의 텍스트를 업데이트할 수 있습니다.

#### <a name="other-progress-indicators"></a>다른 진행률 표시기

##### <a name="ants-animated-horizontal-dots"></a>Ants (애니메이션된 가로 점)
 ![진행률 ants](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")

 "개미" 애니메이션된 가로 점는 결정 되지 않은 왕복 서버 프로세스에 대 한 시각적 참조를 제공 합니다.

##### <a name="spinner-progress-ring"></a>스핀 상자 (진행률 링)
 ![진행률 회전자](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")

 스핀 상자 ("진행률 링" 라고도 함)는 주로 다음 상황에 맞는 UI와 관련 하 여 비활성화 상태의 진행률 표시기입니다. 텍스트 범주 헤더, 메시징, 또는 컨트롤 같은 관련 콘텐츠에 맞게 근접해 있는 회전자를 표시 합니다.

##### <a name="cursor-feedback"></a>커서 피드백
 2 ~ 7 초 사이로 하는 작업에 대 한 커서 피드백을 제공 합니다. 이 경우 일반적으로 운영 체제에서 제공 하는 대기 커서를 사용 합니다. 지침에 대 한 MSDN 문서를 참조 하세요 [Cursors.Wait 속성](/dotnet/api/system.windows.input.cursors.wait)합니다.

#### <a name="progress-indicator-locations"></a>진행률 표시기 위치

##### <a name="status-bar"></a>상태 표시줄
 상태 표시줄을 통해 응용 프로그램 사용자의 작업을 중단 하지 않고 사용자에 게 메시지 및 유용한 정보를 표시할 수 있는 위치입니다. 진행률에 대 한 상태는 일반적으로 창의 맨 아래에 표시를 조합 하 여 진행률 표시줄 표시기를 사용 하 여 진행률을 측정 하는 방법에 대 한 메시지를 포함 하는 도구 팁 창 수 있습니다.

 ![진행률 표시줄을 사용 하 여 상태 표시줄](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")

 **진행률 표시줄을 사용 하 여 상태 표시줄**

 ![메시징을 사용 하 여 상태 표시줄](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")

 **상태 표시줄 텍스트 설명과 함께**

##### <a name="infobar"></a>정보 표시줄
 상태 표시줄 정보 표시줄 비슷하게 제공 상황에 맞는 알림 및 메시징는 진행률 표시줄 또는 스핀 상자와 같은 부정형 진행률 표시기를 사용 하 여 연결할 수 있습니다. 정보 표시줄 세분화 된 수준의 진행률 또는 활성화 상태의 진행률 표시를 제공 하지 않아야 합니다. 참조 [표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)합니다.

 ![진행률 표시줄 및 메시징을 포함 된 정보 표시줄](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")

 **진행률 표시줄 및 텍스트 설명을 포함 된 정보 표시줄**

 ![창 내의 정보 표시줄](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")

##### <a name="inline"></a>인라인
 진행률 로더 형식 중 하나에서 인라인 진행률 표시를 나타낼 수 있습니다. 진행률 표시기 메시징을 사용할 경우 일반적으로 쌍 연결 하지만이 요구 사항은 아닙니다.

 ![인라인 진행률 회전자](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")

 **회전자 텍스트 설명과 함께 결합**

 ![인라인 누적 진행률 표시줄](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")

 **확정적이 지 누적된 진행률 표시줄**

 ![인라인 진행률 메시징](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")

 **서버 탐색기 인라인 텍스트: 새로 고치고 있습니다...**

##### <a name="tool-windows"></a>도구 창
 전역 진행률 표시 도구 모음 바로 아래에 배치 부정형 진행률 표시줄을 표시 됩니다.

 ![전역 비활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")

 **팀 탐색기 전역 비활성화 상태의 진행률 표시줄**

##### <a name="dialogs"></a>대화 상자
 대화 상자는 진행률 로더 형식 중 하나를 포함할 수 있습니다. 진행률 표시기 수 수 메시징을 사용 하 여 쌍을 이루는 뿐만 아니라 여러 수준의 세부적인 나타내는 하위 프로세스를 진행 중 표시를 사용 하 여 결합 합니다.

 ![여러 진행률 표시기 유형이 있는 대화 상자](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")

 **동시 프로세스 및 여러 진행률 표시기 유형이 있는 visual Studio 대화 상자**

 ![진행률 로더 및 메시징이 있는 대화 상자](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")

 **진행률 로더 및 메시징 인라인 명령를 사용 하 여 visual Studio 대화 상자**

##### <a name="document-well"></a>문서 저장소
 잘 문서 컨트롤과 함께에서 여러 진행률 로더 형식을 표시할 수 있습니다.

 ![진행률 및 문서의 메시징](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")

 **도구 모음 아래 비활성화 상태의 진행률 표시줄**

##### <a name="output-window"></a>출력 창
 출력 창 프로세스 진행 및 인라인 텍스트 메시징을 통해 진행 상태를 처리 하기 위한 적합 합니다. 모든 출력 창의 진행률 보고와 함께 상태 표시줄을 사용 해야 합니다.

 ![출력 창에 메시징 진행률](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")

 **지속적인 프로세스 상태를 사용 하 여 출력 창 및 메시징 대기**

## <a name="BKMK_Infobars"></a> Infobars

### <a name="overview"></a>개요
 정보 표시줄 관심 지점에 가까운 표시기 사용자에 게 제공 하 고 공유 정보 표시줄 컨트롤을 사용 하면 시각적 모양과 상호 작용의 일관성이 보장 합니다.

 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Visual Studio에서 표시줄**

#### <a name="appropriate-uses-for-an-infobar"></a>정보 표시줄에 대 한 적절 한 사용

- 현재 컨텍스트에 관련 비차단 작지만 중요 한 메시지를 사용자에 게 부여 하려면

- UI의 특정 상태 또는 기록 디버깅과 같은 몇 가지 상호 작용 의미를 전달 하는 조건 임을 나타내려면

- 시스템 확장은 성능 문제를 유발 하는 경우 같은 문제를 감지 했음을 사용자에 게

- 사용자 탭 및 공백 파일에 혼합 된 편집기를 감지 하는 경우 등의 작업을 쉽게 사용 하는 방법을 제공

##### <a name="do"></a>수행 합니다.

- Infobar 메시지 텍스트를 짧게 유지 지점에 있습니다.

- 간결한 링크 및 단추 텍스트를 유지 합니다.

- 사용자에 게 제공 하는 "action" 옵션은 최소한의 필요한 동작만 표시를 확인 합니다.

##### <a name="dont"></a>안 함:

- 도구 모음에 배치 해야 하는 표준 명령을 제공 하는 정보 표시줄을 사용 합니다.

- 모달 대화 상자 대신 정보 표시줄을 사용 합니다.

- 기간을 벗어나 부동 메시지를 만듭니다.

- 같은 창 내에서 여러 위치에서 여러 정보 표시줄을 사용 합니다.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>동시에 여러 표시줄 표시할 수 있습니까?
 예, 여러 표시줄은 동시에 표시할 수 있습니다. 첫 번째 정보 표시줄 위쪽 및 추가 정보 표시줄 보여 주는 아래에 표시 된 대로, 처음 들어간 것부터 순서 대로 표시 됩니다.

 사용자에 게는 한 번에 최대 3 개의 표시줄 표시 후, 자세한 정보 표시줄을 사용할 수 없는 경우 정보 표시줄 영역 될 스크롤 가능 합니다.

### <a name="creating-an-infobar"></a>정보 표시줄을 만드는
 정보 표시줄에 왼쪽에서 오른쪽의 네 가지 섹션이 있습니다.

- **아이콘:** 이 모든 아이콘을 추가할 위치에 대 한 경고 아이콘 같은 정보 표시줄을 표시 하려는.

- **텍스트:** 필요한 경우 텍스트에 있는 링크와 함께, 시나리오/상황 사용자를 설명 하는 텍스트는 추가할 수 있습니다. 텍스트를 간결 하 게 유지 하도록 기억 합니다.

- **작업의 경우:** 이 섹션에는 링크와 단추를 사용자에 정보 표시줄에 수행할 수 있는 작업에 대 한 포함 되어야 합니다.

- **닫기 단추.** 마지막 섹션 오른쪽에 닫기 단추를 가질 수 있습니다.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>관리 코드에서 표준 infobar 만들기
 InfoBarModel 클래스 정보 표시줄에 대 한 데이터 소스를 만드는 데 사용할 수 있습니다. 이러한 네 가지 생성자 중 하나를 사용 합니다.

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 InfoBarModel 하이퍼링크, 실행 단추 및 아이콘을 사용 하 여 일부 텍스트를 사용 하 여 만드는 예제는 다음과 같습니다.

 ![하이퍼링크를 사용 하 여 Infobar](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>네이티브 코드에서 표준 infobar 만들기
 네이티브 코드에서 정보 표시줄을 제공 하기 위해 The IVsInfoBar 인터페이스를 구현 합니다.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>정보 표시줄이 UIElement 정보 표시줄을에서 가져오기
 InfoBarModel 또는 IVsInfoBar 구현에는 UI에 표시 하려면 UIElement를 켜야 하는 데이터 모델입니다. UIElement은 SVsInfoBarUIFactory/IVsInfoBarUIFactory 서비스를 사용 하 여 검색할 수 있습니다.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>배치
 다음 위치 중 하나 이상의 정보 표시줄을 표시할 수 있습니다.

- 도구 창

- 문서 탭

> [!IMPORTANT]
> 전역 컨텍스트에 대 한 메시지를 제공 하는 정보 표시줄을 배치 하는 것이 가능 합니다. 이 도구 모음 및 문서 저장소 간의 나타납니다. "건너뛰고 jerk"를 사용 하 여 문제를 발생 시키기 때문에 권장 되지는 않습니다 IDE의 경우가 아니면 말아야 절대적으로 필요 하 고 적절 한 합니다.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>정보 표시줄이 ToolWindowPane에서 배치
 ToolWindowPane.AddInfoBar(IVsInfoBar) 메서드를 사용 하 여 도구 창에 정보 표시줄을 추가할 수 있습니다. 이 API는 IVsInfoBar (어떤 InfoBarModel의 기본 구현 이며)를 추가 하거나 또는 IVsUIElement 합니다.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>정보 표시줄을 문서 또는 비 ToolWindowPane에서 배치
 정보 표시줄을 모든 대 한 IVsWindowFrame 배치할를 프레임에 대 한는 IVsInfoBarHost 가져오려고 실패 속성을 사용 하 고 정보 표시줄 UIElement를 추가 합니다.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>정보 표시줄을 주 창에 배치
 정보 표시줄을 주 창에 적용할 VSSPROPID_MainWindowInfoBarHost IVsShell 서비스를 사용 하 여 주 창의 IVsInfoBarHost 가져옵니다 하 고를 UIElement 정보 표시줄을 추가 합니다.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>사용자가 내 정보 표시줄에 작업을 수행 하는 경우 알게 됩니까?
 예, 이벤트 작업을 수행할 때마다 infobar 작성자에 게 반환 됩니다. 그런 다음 infobar 작성자 정보 표시줄에 대 한 사용자 선택에 따라 IDE에서 작업을 수행 하는 합니다. 정보 표시줄 인 닫기 단추가 클릭 되었으며, 호스트에서 자동으로 제거 되지만 추가 작업이 필요한 경우 다른 표시줄 제거 해야 후 닫습니다. 원격 분석도 할 각 infobar를 통해 독립적으로 로그인 할 수 있습니다.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane에서 infobar 이벤트를 수신합니다.
 ToolWindowPane는 표시줄에 대 한 두 개의 이벤트에 있습니다. ToolWindowPane에서 정보 표시줄을 닫으면 InfoBarClosed 이벤트가 발생 합니다. 하이퍼링크 또는 단추 표시줄 내부를 클릭할 때 InfoBarActionItemClicked 이벤트가 발생 합니다.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>UIElement에서 직접 infobar 이벤트를 수신합니다.
 정보 표시줄의 UIElement에서 직접 이벤트를 구독할 IVsInfoBarUIElement.Advise는 사용할 수 있습니다. IVsInfoBarUIEvents 구현 하면 작성자의 close를 받고 이벤트를 클릭 합니다.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="BKMK_ErrorValidation"></a> 오류 유효성 검사
 필수 필드는 생략 하는 경우 같은 또는 잘못 된 형식의 데이터를 입력 하는 경우에 허용 되지 않는 정보를 입력 하는 경우 차단 팝업 오류 대화 상자를 사용 하는 대신 컨트롤 근처 피드백 유효성 검사를 사용 하 여 제어 하는 것이 좋습니다.

### <a name="field-validation"></a>필드 유효성 검사
 세 가지 구성 요소로 이루어져 있습니다 폼 및 필드 유효성 검사: 컨트롤, 아이콘 및 도구 설명 합니다. 여러 유형의 컨트롤이이 사용 하는 동안 텍스트 상자를 예로 사용 됩니다.

 ![필드 유효성 검사 &#40;빈&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")

 필드가 필요한 경우 없어야 않았다는 텍스트가 워터 마크  **\<필요한 >** 하며 필드 배경을 밝은 노란색 (VSColor: `Environment.ControlEditRequiredBackground`) 전경 회색으로 표시 되어야 합니다. (VSColor: `Environment.ControlEditRequiredHintText`):

 ![필드 유효성 검사 "Required" 레이블로](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")

 프로그램 컨트롤의 상태 인지 확인할 수 있습니다 *입력 하는 잘못 된 콘텐츠* 다른 컨트롤로 포커스가 이동 하면 또는 [확인] 커밋 단추를 클릭할 때 또는 사용자에서 문서 또는 폼을 저장 하는 경우.

 잘못 된 콘텐츠 상태 결정 되 면 컨트롤 내부 또는 바로 그 옆에 있는 아이콘이 나타납니다. 아이콘 또는 컨트롤의 가리키기 오류를 설명 하는 도구 설명이 표시 됩니다. 또한 1 픽셀 테두리는 잘못 된 상태를 만드는 컨트롤 주위에 표시 됩니다.

 ![필드 유효성 검사 레이아웃 사양](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")

 **필드 유효성 검사 레이아웃 사양**

#### <a name="acceptable-variations-for-icon-location"></a>아이콘 위치에 대 한 허용 가능한 변형
 유효성 검사 오류에 대 한 알림을 받을 사용자가 해야 하는 수많은 고유 경우가 있습니다. 컨트롤 형식 및 UI 구성할 때 고려 상황에 맞는 아이콘 위치를 선택 합니다.

 ![아이콘 위치에 대 한 허용 위치](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")

 **필드 유효성 검사 아이콘 위치에 대 한 허용 가능한 변형**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>서버 또는 네트워크 연결의 왕복 이동 요구 하는 유효성 검사
 경우에 따라 서버에 왕복 콘텐츠를 확인 하는 데 필요 하 고 사용자 진행률을 확인 및 오류 상태를 표시할 중요 한 것입니다. 아래 그림이이 사례 및 권장 되는 UI의 예를 보여 줍니다.

 ![서버에 왕복 시간과 관련 된 유효성 검사](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")

 **서버에 왕복 시간과 관련 된 유효성 검사**

 "확인 중..." 및 "다시 시도" 텍스트를 수용 하기 위해 컨트롤의 오른쪽에 적절 한 사용 가능한 공간을 제공 해야 하는 참고 합니다.

#### <a name="in-place-warning-text"></a>전체 경고 텍스트
 컨트롤에 가까운 오류 메시지를 오류 상태로 전환 하려면 사용할 수 있는 공간이 있으면 단독으로 도구 설명을 사용 하는이 좋습니다.

 ![&#45;경고 발생 시 키](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")

 **전체 경고 텍스트**

#### <a name="watermarks"></a>워터 마크
 경우에 따라는 전체 컨트롤이 나 창 오류 상태에서입니다. 이 경우에 오류를 나타내는 워터 마크를 사용 합니다.

 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **워터 마크 필드 유효성 검사**