---
title: Visual Studio의 일반 컨트롤 패턴 | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33becb67adb0453adef111ca2c8fb0d2b2e6edfc
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890966"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio의 일반 컨트롤 패턴
## <a name="BKMK_CommonControls"></a> 공용 컨트롤

### <a name="overview"></a>개요
공용 컨트롤은 대부분의 Visual Studio의 사용자 인터페이스를 구성 합니다. Visual Studio 인터페이스에 사용 되는 가장 일반적인 컨트롤을 따라야 합니다 [Windows 데스크톱 상호 작용 지침](/windows/desktop/uxguide/controls)합니다. 이 항목은 Visual Studio에 국한 되며 특별 한 경우 또는 해당 Windows 지침을 확대 하는 세부 정보를 다룹니다.

#### <a name="common-controls-in-this-topic"></a>이 항목의 공용 컨트롤

- [스크롤 막대](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [입력된 필드](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [콤보 상자 및 드롭다운 목록](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [확인란](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [라디오 단추](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [그룹 프레임](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [텍스트 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [단추, 하이퍼링크](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [트리 뷰](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>비주얼 스타일
가장 먼저 컨트롤의 스타일을 지정 하는 경우를 고려해 야 할 경우 테마 UI에서 컨트롤 사용 여부 컨트롤에서 표준 UI 테마 UI 되며 따라야 [표준 Windows 데스크톱 스타일](/windows/desktop/uxguide/controls), 즉 이러한 다시 템플릿이 아닌 해당 기본 컨트롤 모양이 표시 됩니다.

- **표준 (유틸리티) 대화 상자:** 테마가 적용 되지 않습니다. 템플릿을 다시 만들면 하지 않습니다. 기본 컨트롤 스타일 기본값을 사용 합니다.

- **도구 창, 문서 편집기, 디자인 화면 및 테마가 지정 된 대화 상자:** 색 서비스를 사용 하 여 특수화 된 테마가 지정 된 모양을 사용 합니다.

### <a name="BKMK_Scrollbars"></a> 스크롤 막대
 스크롤 막대 따라야 [Windows의 일반적인 상호 작용 패턴 스크롤 막대](/windows/desktop/Controls/about-scroll-bars) 코드 편집기에서와 같이 콘텐츠 정보를 사용 하 여 보강 하는 것을 하지 않는 한 합니다.

### <a name="BKMK_InputFields"></a> 입력된 필드
 일반적인 상호 작용이 동작을 수행 합니다 [텍스트 상자에 대 한 Windows 데스크톱 지침](/windows/desktop/uxguide/ctrl-text-boxes)합니다.

#### <a name="visual-style"></a>비주얼 스타일

- 입력된 필드 유틸리티 대화 상자에서 스타일을 지정할 수 없습니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

- 테마가 지정 된 입력된 필드 테마가 지정 된 대화 상자 및 도구 창에만 사용 해야 합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용

- 읽기 전용 필드에는 기본 (활성) 전경 하지만 배경이 회색 (비활성) 해야 합니다.

- 필드 있어야 하는 데 필요한  **\<필요한 >** 내에서 워터 마크으로 합니다. 드문 경우를 제외 하 고 배경색을 변경 하지 않아야.

- 오류가 유효성 검사: 참조 [Visual Studio의 알림 및 진행률](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- 입력된 필드 표시 된 창의 너비에 맞게 하지도 임의로 경로 같은 긴 필드의 길이 일치 하는 내용에 맞게 크기를 조정 해야 합니다. 길이 제한 횟수 문자는 필드에 허용 하는 것에 대 한 사용자에 게 표시를 수 있습니다.

     ![잘못 된 입력된 필드 길이: 이름을 long이 될 것입니다. ](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />잘못 된 입력된 필드 길이: 이름을 long이 될 것입니다.

     ![입력된 필드 길이 수정 합니다: 입력된 필드는 예상된 콘텐츠에 대 한 적절 한 너비입니다. ](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />입력된 필드 길이 수정 합니다: 입력된 필드는 예상된 콘텐츠에 대 한 적절 한 너비입니다.

### <a name="BKMK_ComboBoxesAndDropDowns"></a> 콤보 상자 및 드롭다운 목록
일반적인 상호 작용이 동작을 수행 합니다 [드롭 다운 목록 및 콤보 상자에 대 한 Windows 데스크톱 지침](/windows/desktop/uxguide/ctrl-drop)합니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 템플릿을 다시 만들면 컨트롤이 없습니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

- 테마 UI에서 콤보 상자 및 드롭다운 컨트롤에 대 한 표준 테마를 수행합니다.

#### <a name="layout"></a>레이아웃
콤보 상자 및 드롭다운 표시 된 창의 너비에 맞게 하지도 임의로 경로 같은 긴 필드의 길이 일치 하는 내용에 맞게 조정 합니다.

![잘못 된: 드롭 다운 너비 너무 깁니다 표시 되는 콘텐츠에 대 한 합니다. ](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />잘못 된: 드롭 다운 너비 너무 깁니다 표시 되는 콘텐츠에 대 한 합니다.

![올바른: 드롭다운 번역 성장을 허용 하지 불필요 하 게 긴로 조정 됩니다. ](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />올바른: 드롭다운 번역 성장을 허용 하지 불필요 하 게 긴로 조정 됩니다.

### <a name="BKMK_CheckBoxes"></a> 확인란
일반적인 상호 작용이 동작을 수행 합니다 [확인란에 대 한 Windows 데스크톱 지침](/windows/desktop/uxguide/ctrl-check-boxes)합니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 템플릿을 다시 만들면 컨트롤이 없습니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

- 테마 UI 확인란 컨트롤에 대 한 표준 테마를 수행합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용

- 확인란 상호 작용 하지 대화 상자를 표시 하거나 다른 영역으로 이동 해야 합니다.

- 확인란 텍스트의 첫 줄 기준선을 맞춥니다.

     ![잘못 된: 확인란 가운데에 표시 됩니다는 텍스트입니다. ](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />잘못 된: 확인란 가운데에 표시 됩니다는 텍스트입니다.

     ![올바른: 확인란 텍스트의 첫 번째 줄을 사용 하 여 정렬 됩니다. ](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />올바른: 확인란 텍스트의 첫 번째 줄을 사용 하 여 정렬 됩니다.

### <a name="BKMK_RadioButtons"></a> 라디오 단추
일반적인 상호 작용이 동작을 수행 합니다 [라디오 단추에 대 한 Windows 데스크톱 지침](/windows/desktop/uxguide/ctrl-radio-buttons)합니다.

#### <a name="visual-style"></a>비주얼 스타일
유틸리티 대화 상자에서 하지 스타일 라디오 단추를 수행 합니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용
긴밀 한 레이아웃에 그룹 구분을 유지 하기 위해 필요한 경우가 아니면 묶어야 라디오 옵션 그룹 틀을 사용 하는 데 필요한 것입니다.

### <a name="BKMK_GroupFrames"></a> 그룹 프레임
일반적인 상호 작용이 동작을 수행 합니다 [그룹 프레임에 대 한 Windows 데스크톱 지침](/windows/desktop/uxguide/ctrl-group-boxes)합니다.

#### <a name="visual-style"></a>비주얼 스타일
유틸리티 대화 상자에서 그룹 프레임 스타일 하지 마십시오. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

#### <a name="layout"></a>레이아웃

- 긴밀 한 레이아웃에 그룹 구분을 유지 하기 위해 필요한 경우가 아니면 묶어야 라디오 옵션 그룹 틀을 사용 하는 데 필요한 것입니다.

- 단일 컨트롤에 대 한 그룹 프레임을 사용 하지 않습니다.

- 경우에 따라 그룹 프레임 컨테이너 대신 가로 규칙을 사용 하는 것이 좋습니다.

## <a name="BKMK_TextControls"></a> 텍스트 컨트롤

### <a name="static-text-fields"></a>정적 텍스트 필드

정적 텍스트 필드를 읽기 전용 정보를 제공 하 고 사용자가 선택할 수 없습니다. 모든 텍스트를 클립보드로 복사할 수에 대 한 사용 하지 마십시오. 그러나 읽기 전용 정적 텍스트 상태의 변경을 반영 하도록 변경할 수 있습니다. 위에 있는 루트 Namespace 텍스트 상자에 대 한 변경 내용을 반영 하도록 변경 내용 그룹 아래에 출력 이름을 정적 텍스트를 아래 예제입니다.

정적 텍스트 정보를 표시 하는 방법은 두 가지가 있습니다.

정적 텍스트는 포함 하지 않고 대화 상자에서 고유한 경우에 충돌 하지 않는 그룹화 될 수 있습니다. 추가 상자 선은 반드시 필요한 경우를 결정 합니다. 아래와 같이 예로 그룹 선으로 만든 섹션 아래 디렉터리 경로 표시 합니다.

![텍스트 컨트롤에 정적 텍스트 정보](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />텍스트 컨트롤에 정적 텍스트 정보

여기서 다른 그룹화 된 영역에 존재 하 고 정보의 포함 도움이 가독성을 위해 대화 상자에서 섹션 수 숨기 거 나 표시 시기 및 (에서처럼 합니다 **속성 창** 설명 창) 또는 유사한 UI를 사용 하 여 일관성을 유지 하려는 경우 정적 텍스트 상자 내부에 배치 합니다. 이 그룹 상자 단일 규칙 이어야 하며 색으로 지정 된 된 `ButtonShadow`:

![속성 창에서 정적 텍스트](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />속성 창에서 정적 텍스트

### <a name="read-only-text-box"></a>읽기 전용 텍스트 상자

따라서 사용자 선택 필드 내의 텍스트를 편집할 수는 없습니다. 이러한 텍스트 상자를 사용 하 여 일반적인 3 차원 끌으로 경계가 `ButtonShadow` 채우기입니다.

텍스트 상자가 활성화 수는 사용자 변경/선택 취소 된 확인란 또는 라디오 단추를 선택/선택 취소 하는 등의 컨트롤을 연결된 하는 경우 (편집). 예를 들어,를 **도구 &gt; 옵션** 아래에 나와 있는 페이지를 **홈 페이지** 입력란 활성화 될 때를 **사용 하 여 기본** 확인란 선택 되지.

![읽기 전용 텍스트 상자, 비활성 및 활성 상태를 보여 주는](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />비활성 및 활성 상태를 보여 주는 읽기 전용 텍스트 상자

### <a name="using-text-in-dialogs"></a>대화 상자에서 텍스트를 사용 하 여

대화 상자에서 텍스트에 대 한 핵심 지침:

- 입력란, 목록 상자 및 대화 상자에서 unthemed 프레임에 대 한 레이블을 동사를 사용 하 여 시작한 첫 번째 단어 이기는 초기 자본에 콜론으로 끝나야 합니다.

    > 테마가 지정 된 대화 상자에서 텍스트 컨트롤에 따라 [Windows 데스크톱 UX 지침](/windows/desktop/uxguide/top-violations) 도움말 링크에서 물음표를 제외 하 고 종료 문장 부호를 주지 않습니다.

- 레이블 옵션 단추 및 확인란에 대해 첫 번째 단어 이기는 초기 자본이 동사를 사용 하 여 시작 하 고 종료 문장 부호 없는.

- 단추, 메뉴, 메뉴 항목 및 탭에 대 한 레이블을 경우 초기 대문자 각 단어 (글자를 대문자로)

- 레이블 용어는 다른 대화 상자에 비슷한 레이블이 일치 해야 합니다.

- 가능한 경우 기록기/편집기가 되어 쓰거나 구현에 대 한 개발자에 게 전달 되기 전에 텍스트를 승인 합니다.

- 모든 컨트롤에서 특별 한 경우 제외 하 고 레이블이 있으면는 탭에 충분 합니다.
도우미 텍스트 적절 한 경우 사용 합니다.

### <a name="helper-text"></a>도우미 텍스트

사용자가 대화의 용도 이해할 수 있도록 하거나 어떤 작업을 나타내기 위해 대화 상자에 포함 됩니다. 도우미 텍스트 간단한 대화 상자를 어지럽히지 않기 위해 필요한 경우에 사용 수 해야 합니다. 도우미 텍스트의 두 가지 변형에는 대화 상자 및 워터 마크입니다.

도우미 텍스트에 대 한 일반적인 위치를 따르고 소개 새 영역에 주의 기울여야 합니다. 도우미 텍스트에 대 한 일반적인 시나리오는:

- 복잡 한 대화 상자를 사용 하 여 상호 작용 하는 방법에 대 한 추가 방향 있도록 대화 상자 도우미 텍스트입니다.

- 빈 도구 창 또는 대화 상자, 콘텐츠 없음 표시 이유를 설명에 워터 마크 텍스트입니다.

- 설명 창 맨 아래에 같은 합니다 **속성 창**합니다.

- 시작 하려면 사용자 취해야 할 조치를 설명 하기 위해 빈 편집기에서 텍스트를 워터 마크입니다.

### <a name="dialog-helper-text"></a>대화 상자 도우미 텍스트

사용자 환경 디자이너로 도우미 텍스트가 적절 한지 결정 하는 데 도움이 됩니다. 디자이너는 해당 일반 콘텐츠 뿐 아니라 도우미 텍스트 나타나는 정의할 수 있습니다. 사용자 지원 쓰기/편집 가능 실제 텍스트입니다.

### <a name="watermarks"></a>워터 마크

대화 상자는 약간 다른 워터 마크 guidelines에서 활용합니다. 대화 상자가 특히 여러 UI 요소 (레이블, 설명 텍스트, 단추 및 텍스트를 사용 하 여 다른 컨테이너 컨트롤)를 사용 하 여 사용 중인 나타날 수 있기 때문에 워터 마크 진한 회색에서 더 나은 차별화 된 검은색으로 표시 되 면 (VSColor: `ButtonShadow`). 워터 마크 흰색 배경 사용 하 여 목록 상자 같은 컨트롤 안에 표시 되는 일반적으로 (VSColor: `Window`).

- 진한 회색으로 표시 되는 텍스트 (VSColor: `ButtonShadow`). 그러나 중간 회색 또는 기타 컬러 나타나면 워터 마크 (VSColor: `ButtonFace`) 백그라운드 및 가독성을 높일 수에 대 한 작업을 처리할 검정 텍스트를 사용 하 여 이동 (VSColor: `WindowText`).

- 워터 마크는 가운데 맞춤 또는 왼쪽 맞춤 수 있습니다. 맞춤 결정을 내릴 때 표준 디자인 규칙을 적용 합니다. 백그라운드에서 워터 마크를 선택할 수 없습니다.

![워터 마크 텍스트 예제](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />워터 마크 텍스트 예제

### <a name="context-specific-dynamic-text"></a>상황에 맞는 (동적) 텍스트

동적 텍스트 대화 상자 또는 모덜리스 UI에서 두 가지 방법 중 하나만 사용된 될 수 있습니다: 동적 레이블 또는 동적 콘텐츠입니다.

- 동적 레이블:와 같은 요소 및 오른쪽 표에 표시 된 요소에 대 한 속성의 목록을 포함 하는 대화 상자에서 선택한 항목에 대 한 자세한 정보를 제공 하는 설명이 포함 된 패널의 동적 텍스트의 일반적인 용도 것입니다. 속성 표에 대 한 레이블을 왼쪽 항목을 선택 하면 오른쪽 표에 해당 특정 항목에 대 한 정보를 표시 하는 수 있도록 동적 수 있습니다.

- 동적 텍스트: 여기서 이렇게에서 하지 일반 정보와 특정 정보를 표시 해야 하지만 조화 주의 해야 하는 경우에 유용할 수 있습니다.

사용자에 게 정보를 복사 하는 기능을 원한다 면 동적 텍스트 읽기 전용 텍스트 필드에 있어야 합니다.

## <a name="BKMK_ButtonsAndHyperlinks"></a> 단추, 하이퍼링크

### <a name="overview"></a>개요
단추 및 링크 컨트롤 (하이퍼링크) 따라야 [하이퍼링크에 대 한 기본 Windows 데스크톱 지침](/windows/desktop/uxguide/ctrl-links) 사용의 경우 단어를 조정 하 고 간격입니다.

### <a name="choosing-between-buttons-and-links"></a>단추 및 링크 중에서 선택
일반적으로 작업 단추 사용 되었 및 탐색에 대 한 예약 된 하이퍼링크입니다. 단추는 모든 경우에 사용할 수 있지만 역할 링크 단추 링크와 일부 조건에서 더 서로 바꿔 사용할 수 있도록 Visual Studio에서 확장 되었습니다.

명령 단추를 사용 하는 경우:

- 기본 명령

- 보조 명령 된 경우에 입력을 수집 하는 데 사용 되는 windows를 표시 하거나 선택

- 파괴적 이거나 되돌릴 수 없는 작업

- 마법사 페이지 흐름 내에서 커밋 단추

도구 창의 명령 단추를 방지 하거나 레이블에 대 한 두 개 이상의 단어를 사용 해야 합니다. 링크에는 긴 레이블을 가질 수 있습니다.

 링크를 사용 하는 경우:

- 다른 창, 문서 또는 웹 페이지에 대 한 탐색

- 긴 레이블 또는 작업의 의도 설명 하는 짧은 문장 해야 하는 상황

- 단추는 작업은 파괴적 이거나 되돌릴 수 없는 UI를 압도 긴밀 하 게 공간

- 취소가 강조 상황에서는 보조 명령 있는 많은 명령

#### <a name="examples"></a>예
![다음 상태 메시지 정보 표시줄에 사용 된 연결 명령을](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />다음 상태 메시지 정보 표시줄에 사용 된 명령 링크

![CodeLens 팝업에 사용 된 링크](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />CodeLens 팝업에 사용된 링크

![단추는 너무 많은 주의 유치는 보조 명령에 사용 되는 링크](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />보조 명령에 대 한 단추는 너무 많은 주의 유치 여기서 사용 된 연결

### <a name="common-buttons"></a>일반 단추

#### <a name="text"></a>텍스트
작성 지침을 따르세요 [UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)합니다.

#### <a name="visual-style"></a>비주얼 스타일

##### <a name="standard-unthemed"></a>표준 (unthemed)
Visual Studio에서 대부분의 단추 유틸리티 대화 상자에 나타나고 스타일 수 해야 합니다. 운영 체제에 따라 표준 단추 모양을 반영 해야 합니다.

##### <a name="themed"></a>테마가 지정 된
일부 경우에서 단추 스타일의 UI 내에서 사용할 수 있습니다 하 고 이러한 단추를 적절 하 게 스타일이 지정 해야 합니다. 참조 [대화 상자](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 테마가 지정 된 컨트롤에 대 한 정보에 대 한 합니다.

### <a name="special-buttons"></a>특수 단추

#### <a name="browse-buttons"></a>찾아보기... 단추
**[찾아보기...]**  단추는 표, 대화 상자 및 도구 창 및 기타 모덜리스 UI 요소를 사용 합니다. 사용자 컨트롤에 값을 채우는 데 도움이 되는 선택을 표시 됩니다. 이 단추를 길고 짧은의 두 가지 변형이 있습니다.

![긴 [찾아보기...] 단추](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />긴 [찾아보기...] 단추

![줄임표 전용 짧은 [...] 단추](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />줄임표 전용 짧은 [...] 단추

짧은 줄임표 전용 단추를 사용 하는 경우:

- 둘 이상의 긴 경우 **[찾아보기...]**  여러 필드 검색에 대 한 허용 되는 경우와 같은 대화 상자에서 단추입니다. 단기 사용 **[...]**  이 상황에서 만든 액세스 키를 혼동 하지 않으려면 각 단추 ( **& 찾아보기** 하 고 **B & 찾아보기** 동일한 대화 상자에서).

- 긴밀 한 대화 상자에서 또는 긴 단추를 적절 한 장소가 없습니다.

- 단추를 표 형태 컨트롤에 표시 합니다.

단추를 사용 하는 것에 대 한 지침:

- 액세스 키를 사용 하지 마세요. 키보드를 사용 하 여 액세스 하려면 사용자는 인접 한 컨트롤에서 탭 해야 합니다. 찾아보기 단추 필드를 채우도록 직후 대체 되도록 탭 순서 인지 확인 합니다. 첫 번째 기간 아래 밑줄을 사용 하지 않습니다.

- 활성 MSAA (Microsoft Accessibility)를 설정 **이름을** 속성을 **찾아보기...**  (줄임표) 포함 하므로 화면 판독기 읽기 "찾아보기"가 "점선-점선-점선" 또는 "기간-기간별."로 관리 되는 컨트롤에 대 한이 설정을 의미 합니다 **AccessibleName** 속성.

- 줄임표를 사용해 서는 안 **[...]**  찾아보기 동작을 제외한 항목에 대 한 단추입니다. 예를 들어, 필요한 경우는 **[새로 만들기...]**  단추 하지만 대화 상자를 다시 디자인 해야 합니다. 그런 다음 텍스트에 대해 충분 한 공간이 없는 합니다.

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
![[찾아보기...] 크기 조정 단추: 표준 버전은 75 x 23 픽셀, 짧은 버전은 26 x 23 픽셀](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />[찾아보기...] 크기 조정 단추

![간격 [찾아보기...] 단추: 짧은 찾아 관련된 컨트롤 사이의 간격 단추 관련된 컨트롤에서 표준 찾아보기 단추 7 픽셀 사이의 간격을 5 픽셀](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />[찾아보기...] 간격 조정 단추

#### <a name="graphical-buttons"></a>단추 그래픽
일부 단추를 항상 그래픽 이미지를 사용 하 여 공간을 절약 하 고 지역화 문제를 방지 하기 위해 텍스트를 포함 하지 않습니다. 이러한 필드 선택기 및 다른 정렬 가능한 목록에서 자주 사용 됩니다.

> [!NOTE]
> 사용자 (액세스 키가) 이러한 단추를 탭, 따라서 적절 한 순서로 배치 해야 합니다. 지도 `name` 화면 판독기 단추 동작을 올바르게 해석할 수 있도록 소요 되는 작업에 단추의 속성입니다.

| 함수 | 단추 |
| --- | --- |
| 추가 | ![그래픽 "추가" 단추](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| 제거 | ![그래픽 "제거" 단추](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| 모든 추가 | ![그래픽 "모두 추가" 단추](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| 모두 제거 | ![그래픽 "모두 제거" 단추](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| 위로 이동 | ![그래픽 "위로 이동" 단추](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| 아래로 이동 | ![그래픽 "아래로 이동" 단추](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| 삭제 | ![그래픽 "삭제" 단추](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
단추 그래픽의 짧은 버전 동일에 대 한 크기 조정 된 **[찾아보기...]**  단추 (26 x 23 픽셀).

![단추를 사용 하 여 및 투명 한 색 표시가 있거나 없는 그래픽 이미지의 모양을](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />단추를 사용 하 여 및 투명 한 색 표시가 있거나 없는 그래픽 이미지의 모양

### <a name="hyperlinks"></a>하이퍼링크
하이퍼링크는 도움말 항목, 모달 대화 상자 또는 마법사를 열 같은 탐색 기반 작업에 적합 합니다. 하이퍼링크를 명령에 대해 사용 하는 경우 UI에 표시 되 고 눈에 띄는 변경 항상 표시 됩니다. 일반적으로 작업 (예: [취소]를 저장 및 삭제) 작업에 대 한 커밋을 더 잘 전달 하는 단추를 사용 하 여 합니다.

#### <a name="writing-style"></a>필기 스타일
수행 합니다 [사용자 인터페이스 텍스트에 대 한 Windows 데스크톱 지침](/windows/desktop/uxguide/text-ui)합니다. "자세한 자세한 정보를" 사용 하지 않는 알 나 자세한 정보 "," 또는 "이 Get help" 구문입니다. 대신 도움말 내용에 따라 주요 답변 측면에서 도움말 링크 텍스트를 구입니다. 예를 들어, "**서버 탐색기에 서버를 추가 하려면 어떻게?** "

#### <a name="visual-style"></a>비주얼 스타일

- 하이퍼링크는 항상 사용 해야 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)합니다. 하이퍼링크 스타일이 없습니다 올바르게, 활성 상태인 경우 빨간색 깜박입니다 또는 방문 후 다른 색으로 표시 합니다.

- 아닌 경우 링크 된 전체 문장 내에서 문장 조각 같은 워터 마크의 상태를 가져가서 컨트롤에서 밑줄을 포함 하지 마십시오.

- 가리키기 밑줄 표시 해서는 안 됩니다. 대신, 링크가 활성화 되어 있음을 사용자에 게 피드백을 약간의 색 변경 하 고 적절 한 링크 커서는입니다.

## <a name="BKMK_TreeViews"></a> 트리 뷰

트리 뷰는 부모-자식 그룹으로 복잡 한 구성 하는 방법을 보여 줍니다.을 제공 합니다. 사용자는 확장 하거나 기본 자식 항목을 표시 하거나 숨기려면 부모 그룹을 축소할 수 있습니다. 추가 작업을 제공 하는 트리 뷰 내에서 각 항목을 선택할 수 있습니다.

### <a name="BKMK_TreeViewVisualStyle"></a> 트리 보기에 대 한 비주얼 스타일

#### <a name="expanders"></a>확장기
트리 뷰 컨트롤은 Windows 및 Visual Studio를 사용한 확장기 디자인을 따라야 합니다. 각 노드는 expander 컨트롤을 사용 하 여 기본 항목을 표시 하거나 숨깁니다. Expander 컨트롤을 사용 하 여 Windows 및 Visual Studio 내에서 다른 트리 뷰를 발생할 수 있는 사용자에 대 한 일관성을 제공 합니다.

![올바른: expander 컨트롤을 사용 하 여 트리 뷰 노드의 적절 한 스타일이](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Expander 컨트롤을 사용 하 여 트리 뷰 노드의 올바른: 적절 한 스타일

![잘못 되었습니다: 트리 뷰 노드의 잘못 된 스타일](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />트리 뷰 노드의 부적절 한 스타일 잘못 되었습니다.

#### <a name="selection"></a>선택
트리 보기에서 노드를 선택 하면 강조 표시를 트리 뷰 컨트롤의 전체 너비를 확장 해야 합니다. 이렇게 하면 사용자가 항목을 선택 했는지를 명확 하 게 식별 합니다. 선택 영역 색 현재 Visual Studio 테마를 반영 해야 합니다.

![올바른: 선택한 노드의 강조 표시 트리 뷰 컨트롤의 전체 너비에 맞춥니다. ](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />올바른: 선택한 노드의 강조 표시 트리 뷰 컨트롤의 전체 너비에 맞춥니다.

![잘못 되었습니다: 선택한 노드의 강조 표시에는 트리 뷰 컨트롤의 전체 너비를 맞지 않습니다. ](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />잘못 되었습니다: 선택한 노드의 강조 표시에는 트리 뷰 컨트롤의 전체 너비를 맞지 않습니다.

#### <a name="icons"></a>아이콘
항목 간의 차이 시각적으로 식별 하는 데 도움이 하는 경우에 아이콘 트리 뷰 컨트롤에서 사용 해야 합니다. 일반적으로 아이콘 아이콘 요소 형식을 구분 하기 위한 정보를 수행할 수 있는 유형이 다른 목록 에서만에서 사용할 수 해야 합니다. 유형이 같은 목록에서 아이콘을 사용 하 여 소음으로 자주 볼 수 있습니다 피해 야 합니다. 이 경우 그룹 아이콘 (부모) 내 항목의 형식을 전달할 수 있습니다. 이 규칙의 예외 아이콘 동적 되며 상태를 나타내는 데 사용 되는 것입니다.

#### <a name="scroll-bars"></a>스크롤 막대
스크롤 막대를 콘텐츠 트리 뷰 컨트롤에 맞으면에 항상 숨깁니다. 스크롤 막대에 대 한 허용 되는 스크롤 가능한 창에서 숨겨진 또는 반투명 하 게 될 및 트리 뷰를 포함 하는 창에 포커스가 있으면 나타나거나 트리의 가리키기 시 자체를 보려면

![내용이 있는 트리 뷰 컨트롤의 한계를 초과 하는 세로 및 가로 스크롤 막대가 모두 표시 됩니다. ](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />내용이 있는 트리 뷰 컨트롤의 한계를 초과 하는 세로 및 가로 스크롤 막대가 모두 표시 됩니다.

### <a name="BKMK_TreeViewInteractions"></a> 트리 뷰 상호 작용

#### <a name="context-menus"></a>상황에 맞는 메뉴
트리 뷰 노드에 상황에 맞는 메뉴에서 하위 메뉴 옵션을 표시할 수 있습니다. 일반적으로이 사용자가 항목을 마우스 오른쪽 단추로 클릭 하거나 선택한 항목에 사용 하는 Windows 키보드에서 메뉴 키를 누를 때 발생 합니다. 것이 중요 노드에 포커스를 획득 하 고 선택 합니다. 이렇게 하면 사용자에 속하는 하위 메뉴 항목을 식별 합니다.

![사용자에 게 상황에 맞는 메뉴 향상 포커스 항목 생성에 항목 선택 되었습니다. ](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />사용자에 게 상황에 맞는 메뉴 향상 포커스 항목 생성에 항목 선택 되었습니다.

#### <a name="keyboard"></a>키보드
트리 뷰 항목을 선택 하 고 키보드를 사용 하 여 노드 확장/축소 하는 기능을 제공 해야 합니다. 이렇게 하면 탐색의 접근성 요구 사항을 충족 합니다.

##### <a name="tree-view-control"></a>트리 뷰 컨트롤
Visual Studio 트리 컨트롤 일반적인 키보드 탐색을 수행 해야 합니다.

- **위쪽 화살표:** 트리를 이동 하 여 항목을 선택 합니다.

- **아래쪽 화살표:** 트리 아래로 이동 하 여 항목을 선택 합니다.

- **오른쪽 화살표:** 트리에서 노드를 확장 합니다.

- **왼쪽된 화살표:** 트리에서 노드를 축소

- **키를 입력 합니다.** 시작, 로드, 선택한 항목 실행

##### <a name="trid-tree-view-and-grid-view"></a>Trid (트리 보기 및 그리드 보기)
Trid 컨트롤은 grid에서 트리 뷰를 포함 하는 복잡 한 컨트롤입니다. 확장, 축소 및 트리를 탐색한 다음 내용을 추가 하 여 트리 뷰로 동일한 키보드 명령을 따라야 합니다.

- **오른쪽 화살표:** 노드를 확장 합니다. 노드가 확장 된 후 지속 되는 가장 가까운 열 오른쪽으로 이동 합니다. 행의 끝에서 탐색 중지 해야 합니다.

- **탭:** 오른쪽에 가장 가까운 셀으로 이동합니다.  행의 끝을 탐색 다음 행으로 계속 됩니다.

- **Shift + Tab:** 왼쪽의 가장 가까운 셀으로 이동합니다.  행의 부분을 탐색 이전 행의 오른쪽에 있는 셀을 계속합니다.

![Visual Studio의 trid 컨트롤](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Visual Studio의 trid 컨트롤