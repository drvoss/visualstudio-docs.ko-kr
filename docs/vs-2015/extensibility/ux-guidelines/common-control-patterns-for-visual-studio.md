---
title: 일반적인 컨트롤 패턴
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 246464baea7e07e4d97e3483b423d200cf2b960c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430036"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio의 일반 컨트롤 패턴
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_CommonControls"></a> 공용 컨트롤

### <a name="overview"></a>개요
 공용 컨트롤은 대부분의 Visual Studio의 사용자 인터페이스를 구성 합니다. Visual Studio 인터페이스에 사용 되는 가장 일반적인 컨트롤을 따라야 합니다 [Windows 데스크톱 상호 작용 지침](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)합니다. 이 문서는 Visual Studio에 전용 이며 특별 한 경우 또는 해당 Windows 지침을 확대 하는 세부 정보를 다룹니다.

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
 가장 먼저 컨트롤의 스타일을 지정 하는 경우를 고려해 야 할 경우 테마 UI에서 컨트롤 사용 여부 컨트롤에서 표준 UI 테마 UI 되며 따라야 [표준 Windows 데스크톱 스타일](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), 즉 이러한 다시 템플릿이 아닌 해당 기본 컨트롤 모양이 표시 됩니다.

- **표준 (유틸리티) 대화 상자:** 테마가 적용 되지 않습니다. 템플릿은 그렇지 않은 재구성을 수행 합니다. 기본 컨트롤 스타일 기본값을 사용 합니다.

- **도구 창, 문서 편집기, 디자인 화면 및 테마가 지정 된 대화 상자:** 색 서비스를 사용 하 여 특수화 된 테마가 지정 된 모양을 사용 합니다.

### <a name="BKMK_Scrollbars"></a> 스크롤 막대
 스크롤 막대 따라야 [Windows 스크롤 막대에 대 한 일반적인 상호 작용 패턴](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) 는 보강 된 콘텐츠 정보를 사용 하 여 같은 코드 편집기에서 하지 않는 한 합니다.

### <a name="BKMK_InputFields"></a> 입력된 필드
 일반적인 상호 작용이 동작을 수행 합니다 [텍스트 상자에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx)합니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 입력된 필드를 스타일 수 해야 합니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

- 테마가 지정 된 입력된 필드 테마가 지정 된 대화 상자 및 도구 창에만 사용 해야 합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용

- 읽기 전용 필드에는 기본 (활성) 전경 하지만 배경이 회색 (비활성) 해야 합니다.

- 필드 있어야 하는 데 필요한  **\<필요한 >** 내에서 워터 마크으로 합니다. 드문 경우를 제외 하 고 배경색을 변경 하지 않아야.

- 오류가 유효성 검사: 참조 [Visual Studio의 알림 및 진행률](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- 입력된 필드 표시 된 창의 너비에 맞게 하지도 임의로 경로 같은 긴 필드의 길이 일치 하는 내용에 맞게 크기를 조정 해야 합니다. 길이 제한 횟수 문자는 필드에 허용 하는 것에 대 한 사용자에 게 표시를 수 있습니다.

     ![잘못 된 입력된 필드 컨트롤 너비](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl") **잘못 된 입력된 필드 길이: 이름을 long이 될 것입니다.**

     ![입력된 필드 컨트롤 너비를 수정](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl") **수정 필드 길이 입력: 입력된 필드에 필요한 콘텐츠에 대 한 적절 한 너비입니다.**

### <a name="BKMK_ComboBoxesAndDropDowns"></a> 콤보 상자 및 드롭다운 목록
 일반적인 상호 작용이 동작을 수행 합니다 [드롭 다운 목록 및 콤보 상자에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx)합니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 컨트롤 템플릿은 그렇지 않은 다시 수행 합니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

- 테마 UI에서 콤보 상자 및 드롭다운 컨트롤에 대 한 표준 테마를 수행합니다.

#### <a name="layout"></a>레이아웃
 콤보 상자 및 드롭다운 표시 된 창의 너비에 맞게 하지도 임의로 경로 같은 긴 필드의 길이 일치 하는 내용에 맞게 조정 합니다.

 ![잘못 된 삭제&#45;레이아웃 아래로](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")

 **드롭다운 목록 컨트롤에 대 한 잘못 된 필드 길이**

 ![올바른 드롭다운&#45;레이아웃 아래로](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 04_CorrectDropDownLayout")

 **드롭다운 목록 컨트롤에 대 한 올바른 필드 길이**

### <a name="BKMK_CheckBoxes"></a> 확인란
 일반적인 상호 작용이 동작을 수행 합니다 [확인란에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx)합니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 컨트롤 템플릿은 그렇지 않은 다시 수행 합니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

- 테마 UI 확인란 컨트롤에 대 한 표준 테마를 수행합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용

- 확인란 상호 작용 하지 대화 상자를 표시 하거나 다른 영역으로 이동 해야 합니다.

- 확인란 텍스트의 첫 줄 기준선을 맞춥니다.

     ![잘못 된 확인란 맞춤](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign") **잘못 된 확인란 맞춤: 확인란의 가운데 텍스트에 표시 됩니다.**

     ![확인란 맞춤 수정](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign") **확인란 맞춤을 수정 합니다. 확인란의 텍스트의 첫 줄 기준선에 맞춥니다.**

### <a name="BKMK_RadioButtons"></a> 라디오 단추
 일반적인 상호 작용이 동작을 수행 합니다 [라디오 단추에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx)합니다.

#### <a name="visual-style"></a>비주얼 스타일
 유틸리티 대화 상자에서 하지 스타일 라디오 단추를 수행 합니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용
 라디오 선택 묶어야 그룹 프레임을 사용 하는 데 필요한 것입니다.

### <a name="BKMK_GroupFrames"></a> 그룹 프레임
 일반적인 상호 작용이 동작을 수행 합니다 [그룹 프레임에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx)합니다.

#### <a name="visual-style"></a>비주얼 스타일
 유틸리티 대화 상자에서 스타일 그룹 프레임 하지 않습니다. 기본 스타일을 컨트롤에 내장 함수를 사용 합니다.

#### <a name="layout"></a>레이아웃

- 긴밀 한 레이아웃에 그룹 구분을 유지 하기 위해 필요한 경우가 아니면 묶어야 라디오 옵션 그룹 틀을 사용 하는 데 필요한 것입니다.

- 단일 컨트롤에 대 한 그룹 프레임을 사용 하지 않습니다.

- 경우에 따라 그룹 프레임 컨테이너 대신 가로 규칙을 사용 하는 것이 좋습니다.

## <a name="BKMK_TextControls"></a> 텍스트 컨트롤

### <a name="labels"></a>레이블

#### <a name="active-label-state"></a>레이블이 활성 상태

##### <a name="utility-standard-dialogs"></a>유틸리티 (표준) 대화 상자)

- 일반적으로 제어 레이블에 대 한 Windows 데스크톱 지침을 따르세요.

- 유틸리티 대화 상자에서 레이블이 굵은 글꼴이 아닌, 글꼴 및 텍스트 색을 표준 환경에 표시 됩니다. 참조 [글꼴 및 Visual Studio에 대 한 서식 지정](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)합니다.

- 줄임표는 레이블을 항상 따라야 합니다.

##### <a name="signature-themed-dialogs"></a>서명 (테마) 대화 상자)
 레이블 컨트롤에 굵게 또는 연한 회색으로 표시 될 수 있습니다.

#### <a name="disabled-label-state"></a>사용할 수 없는 레이블 상태
 레이블 연결 된 컨트롤의 모양을 반영 해야 합니다. 예를 들어, 연결된 된 컨트롤을 사용 하지 않도록 설정 하는 경우 다음 레이블이 나타납니다 회색 및 사용 안 함. 이 OS에서 일반적으로 처리 하며 특별 한 작업이 수행 되지 않습니다.

#### <a name="dynamic-labels"></a>동적 레이블
 현재 선택 영역에 따라 동적 레이블 변경 합니다. 가능 하면 사용자 정보를 표시 하지 일반 정보를 특정 선택 항목과 관련이 임을 이해 하는 데 도움이 마스터/세부 레이아웃의 동적 레이블을 사용 합니다.

 ![동적 콘텐츠를 사용 하 여 사용 된 동적 레이블](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")

 **동적 콘텐츠를 사용한 동적 레이블의 예**

#### <a name="instructional-text"></a>지침 텍스트
 몇 가지 인터페이스 요소 또는 수행할 작업을 나타내는 사용자 UI 용도 이해 하는 데 도움이 되는 지침 텍스트에서 활용 합니다.

- 사용 안내 텍스트 대화 상자 맨 위에 있는 가장 일반적인 이지만 명령 그룹화에 복잡 한 제어를 제공 하려면 다른 영역에 나타날 수 있습니다.

- 사용 안내 텍스트 비 대화형 이지만 도움말 항목에 대 한 하이퍼링크를 포함할 수 있습니다.

- 꼭 필요할 때만 및만 해당 되는 지침 텍스트를 사용 하 여 필요할 때.

##### <a name="formatting"></a>서식
 사용 안내 텍스트 환경 글꼴, 표준 (비 테마) 컨트롤 텍스트 여야 합니다. 참조 [글꼴 및 Visual Studio에 대 한 서식 지정](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)합니다.

 작성 되는 지침 텍스트에 대 한 세부 정보를 참조 하세요 [UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)합니다.

 ![사용 안내 텍스트 서식 지정](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 02_InstructionalTextFormatting")

 **Visual Studio 대화 상자에서 지침 텍스트**

#### <a name="informational-text"></a>정보 텍스트
 정보 텍스트에는 사용자는 추가 정보를 제공 하는 텍스트가입니다. 정적 또는 동적 알림으로 사용할 수 있습니다. 이 항상 읽기 전용 이지만 읽기 전용 텍스트 필드와 같은 컨트롤 컨테이너의 동적 텍스트를 배치할 경우 사용자에 게 정보를 복사 하는 기능에 대 한 두는 것이 유용 합니다.

##### <a name="dynamic-context-specific-text"></a>동적 (컨텍스트별) 텍스트
 사용자가 포커스를 전환 하는 경우와 같은 컨텍스트에 따라 동적 정보 텍스트 변경 됩니다. 항상 그렇지는 않지만 종종 동적 레이블로 동적 콘텐츠 쌍을 이룹니다.

 ![동적 정보 텍스트](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")

 **동적 정보 텍스트 컨텍스트에 따라 달라 집니다.**

##### <a name="formatting"></a>서식
 읽기 전용 텍스트 필드를 표시 하는 방법은 두 가지: UI에서 직접 (위 참조)을 노출 하거나 그룹 프레임 또는 텍스트 상자와 같은 다른 컨트롤에 포함 합니다. 상황에 따라 올바른 중 하나에 해당 합니다. 기능 디자이너는 읽기 전용 정보를 제공 하는 방법을 결정 됩니다.

 읽기 전용 텍스트 상자 내부에 텍스트를 수 있습니다. 이 일반적으로 나타냅니다 콘텐츠를 선택한 복사 될 수 있지만 편집할 수 없습니다.

 ![정보 텍스트 읽기에 대 한 서식 지정&#45;필드만](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")

 **읽기 전용 필드에 대 한 서식 지정 정보 텍스트**

#### <a name="watermarks"></a>워터 마크
 동일할 수 있습니다, 하는 동안에 워터 마크 및 지침 텍스트 간의 차이점은 해당 컨트롤이 나 창 비어 있지 않으며 사용 안내 텍스트 계속 표시 됩니다 항상 때 워터 마크 콘텐츠로 대체 됩니다.

 워터 마크 창 또는 컨트롤 비어 있을 때 사용 해야 합니다. 이러한 영역을 채우기 위해 수행 해야 하는 데 필요한 나타내고 끌기 소스와 같은 관련 창을 열려면 작업 링크를 포함할 수 있습니다.

##### <a name="visual-style"></a>비주얼 스타일

- 워터 마크 해야 창 내에서 가로 방향으로 가운데에 맞춥니다.

- 워터 마크 해야 가운데 맞춤 왼쪽 정렬 합니다.

- 워터 마크 세로로 가운데 되었거나 영역의 위쪽에 배치 합니다. 영역의 위쪽에 있으면 충분 한 공간이 있어야 위의 워터 마크 눈에 띄는 되도록 합니다.

- 사용 된 `Environment.GrayText` 토큰 및 표준 환경 글꼴 색입니다. 하이퍼링크에는 공유 하는 표준 하이퍼링크 토큰을 사용 해야 합니다: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, 및 `Environment.PanelHyperlinkDisabled`합니다.

- 백그라운드에서 워터 마크를 선택할 수 없습니다.

- 가능한 경우 시작 메뉴나 워터 마크에 대 한 링크를 포함 합니다.

  ![디자이너 창에서 텍스트를 워터 마크](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")

  ![텍스트 도구 창의 워터 마크](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")

  **Visual Studio의 워터 마크 텍스트의 예**

## <a name="BKMK_ButtonsAndHyperlinks"></a> 단추, 하이퍼링크

### <a name="overview"></a>개요
 단추 및 링크 컨트롤 (하이퍼링크) 따라야 [하이퍼링크에 대 한 기본 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) 사용의 경우 단어를 조정 하 고 간격입니다.

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

#### <a name="examples"></a>예제
 ![다음 상태 메시지 정보 표시줄 명령 링크](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")

 **다음 상태 메시지 정보 표시줄에 사용 된 명령 링크**

 ![CodeLens 팝업에 사용 된 링크](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")

 **CodeLens 팝업에 사용 된 링크**

 ![보조 명령으로 사용 하는 링크](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")

 **보조 명령에 대 한 단추는 너무 많은 주의 유치 여기서 사용 된 연결**

### <a name="common-buttons"></a>일반 단추

#### <a name="text"></a>텍스트
 작성 지침을 따르세요 [UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)합니다.

#### <a name="visual-style"></a>비주얼 스타일

##### <a name="standard-dialogs"></a>표준 대화 상자
 Visual Studio에서 대부분의 단추 표준 대화 상자에 나타나고 스타일 수 해야 합니다. 운영 체제에 따라 표준 단추 모양을 반영 해야 합니다.

##### <a name="themed"></a>테마가 지정 된
 일부 경우에서 단추 스타일의 UI 내에서 사용할 수 있습니다 하 고 이러한 단추를 적절 하 게 스타일이 지정 해야 합니다. 참조 [대화 상자](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 테마가 지정 된 컨트롤에 대 한 정보에 대 한 합니다.

### <a name="special-buttons"></a>특수 단추

#### <a name="browse-buttons"></a>찾아보기... 단추
 **[찾아보기...]**  단추는 표, 대화 상자 및 도구 창 및 기타 모덜리스 UI 요소를 사용 합니다. 사용자 컨트롤에 값을 채우는 데 도움이 되는 선택을 표시 됩니다. 이 단추를 길고 짧은의 두 가지 변형이 있습니다.

 ![Long &#91;찾아보기... &#93; 단추](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")

 **긴 [찾아보기...] 단추**

 ![짧은 줄임표&#45;만 &#91;찾아보기... &#93; 단추](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")

 **줄임표 전용 짧은 [...] 단추**

 짧은 줄임표 전용 단추를 사용 하는 경우:

- 둘 이상의 긴 경우 **[찾아보기...]**  여러 필드 검색에 대 한 허용 되는 경우와 같은 대화 상자에서 단추입니다. 단기 사용 **[...]**  이 상황에서 만든 액세스 키를 혼동 하지 않으려면 각 단추 ( **& 찾아보기** 하 고 **B & 찾아보기** 동일한 대화 상자에서).

- 긴밀 한 대화 상자에서 또는 긴 단추를 적절 한 장소가 없습니다.

- 단추를 표 형태 컨트롤에 표시 합니다.

  단추를 사용 하는 것에 대 한 지침:

- 액세스 키를 사용 하지 마세요. 키보드를 사용 하 여 액세스 하려면 사용자는 인접 한 컨트롤에서 탭 해야 합니다. 찾아보기 단추 필드를 채우도록 직후 대체 되도록 탭 순서 인지 확인 합니다. 첫 번째 기간 아래 밑줄을 사용 하지 않습니다.

- 활성 MSAA (Microsoft Accessibility)를 설정 **이름을** 속성을 **찾아보기...**  (줄임표) 포함 하므로 화면 판독기 읽기 "찾아보기"가 "점선-점선-점선" 또는 "기간-기간별."로 관리 되는 컨트롤에 대 한이 설정을 의미 합니다 **AccessibleName** 속성.

- 줄임표를 사용해 서는 안 **[...]**  찾아보기 동작을 제외한 항목에 대 한 단추입니다. 예를 들어, 필요한 경우는 **[새로 만들기...]**  단추 하지만 대화 상자를 다시 디자인 해야 합니다. 그런 다음 텍스트에 대해 충분 한 공간이 없는 합니다.

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
 ![크기 조정 &#91;찾아보기... &#93; 단추](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")

 **[찾아보기...] 단추를 크기 조정**

 ![간격 &#91;찾아보기... &#93; 단추](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")

 **간격 [찾아보기...] 단추**

#### <a name="graphical-buttons"></a>단추 그래픽
 일부 단추를 항상 그래픽 이미지를 사용 하 여 공간을 절약 하 고 지역화 문제를 방지 하기 위해 텍스트를 포함 하지 않습니다. 이러한 필드 선택기 및 다른 정렬 가능한 목록에서 자주 사용 됩니다.

> [!NOTE]
> 사용자 (액세스 키가) 이러한 단추를 탭, 따라서 적절 한 순서로 배치 해야 합니다. 단추의 name 속성을 화면 판독기 단추 동작을 올바르게 해석할 수 있도록 소요 되는 작업에 매핑됩니다.

|||
|-|-|
|Add|![그래픽 "추가" 단추](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 08_ButtonAdd")|
|제거|![그래픽 "제거" 단추](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 09_ButtonRemove")|
|모든 추가|![그래픽 "모두 추가" 단추](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|
|모두 제거|![그래픽 "모두 제거" 단추](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 11_ButtonRemoveAll")|
|위로 이동|![그래픽 "위로 이동" 단추](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|
|아래로 이동|![그래픽 "아래로 이동" 단추](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|
|삭제|![그래픽 "삭제" 단추](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
 단추 그래픽의 짧은 버전 동일에 대 한 크기 조정 된 **[찾아보기...]**  단추 (26 x 23 픽셀).

 ![투명 한 색 표시가 있거나 없는 단추](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")

 **단추를 사용 하 여 및 투명 한 색 표시가 있거나 없는 그래픽 이미지의 모양**

### <a name="hyperlinks"></a>하이퍼링크
 하이퍼링크는 도움말 항목, 모달 대화 상자 또는 마법사 열기와 같은 탐색 기반 작업에 적합 합니다. 하이퍼링크를 명령에 대해 사용 하는 경우 UI에 표시 되 고 눈에 띄는 변경 항상 표시 됩니다. 일반적으로 작업 (예: 취소를 저장 및 삭제) 작업에 대 한 커밋을 더 잘 전달 하는 단추를 사용 하 여 합니다.

#### <a name="writing-style"></a>필기 스타일
 수행 합니다 [사용자 인터페이스 텍스트에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)합니다. "자세한 자세한 정보를" 사용 하지 않는 알 나 자세한 정보 "," 또는 "이 Get help" 구문입니다. 대신 도움말 내용에 따라 주요 답변 측면에서 도움말 링크 텍스트를 구입니다. 예를 들어, "**서버 탐색기에 서버를 추가 하려면 어떻게?** "

#### <a name="visual-style"></a>비주얼 스타일

- 하이퍼링크는 항상 사용 해야 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)합니다. 하이퍼링크 스타일이 없습니다 올바르게, 활성 상태인 경우 빨간색 깜박입니다 또는 방문 후 다른 색으로 표시 합니다.

- 아닌 경우 링크 된 전체 문장 내에서 문장 조각 같은 워터 마크의 상태를 가져가서 컨트롤에서 밑줄을 포함 하지 않습니다.

- Hover에 밑줄을 표시 하지. 대신, 링크가 활성화 되어 있음을 사용자에 게 피드백을 약간의 색 변경 하 고 적절 한 링크 커서는입니다.

## <a name="BKMK_TreeViews"></a> 트리 뷰

### <a name="overview"></a>개요
 트리 뷰는 부모-자식 그룹으로 복잡 한 구성 하는 방법을 보여 줍니다.을 제공 합니다. 사용자는 확장 하거나 기본 자식 항목을 표시 하거나 숨기려면 부모 그룹을 축소할 수 있습니다. 추가 작업을 제공 하는 트리 뷰 내에서 각 항목을 선택할 수 있습니다.

 이 항목에서는 사용 제한, 적절 한 디자인 및 트리 보기의 기능을 설명합니다.

#### <a name="in-this-topic"></a>항목 내용

- [비주얼 스타일](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [상호 작용](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="BKMK_TreeViewVisualStyle"></a> 비주얼 스타일

#### <a name="expanders"></a>확장기
 트리 뷰 컨트롤은 Windows 및 Visual Studio를 사용한 확장기 디자인을 따라야 합니다. 각 노드는 expander 컨트롤을 사용 하 여 기본 항목을 표시 하거나 숨깁니다. Expander 컨트롤을 사용 하 여 Windows 및 Visual Studio 내에서 다른 트리 뷰를 발생할 수 있는 사용자에 대 한 일관성을 제공 합니다.

 ![트리 뷰 컨트롤을 수정](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Expander 컨트롤을 사용 하 여 트리 뷰 노드의 올바른: 적절 한 스타일**

 ![잘못 된 트리 뷰 노드](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")

 **트리 뷰 노드의 부적절 한 스타일 잘못 되었습니다.**

#### <a name="selection"></a>선택
 트리 보기에서 노드를 선택 하면 강조 표시를 트리 뷰 컨트롤의 전체 너비를 확장 해야 합니다. 이렇게 하면 사용자가 항목을 선택 했는지를 명확 하 게 식별 합니다. 선택 영역 색 현재 Visual Studio 테마를 반영 해야 합니다.

 ![트리 뷰 컨트롤을 수정](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **올바른: 선택한 노드의 강조 표시 트리 뷰 컨트롤의 전체 너비에 맞춥니다.**

 ![잘못 된 트리 뷰 강조 표시](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")

 **잘못 되었습니다: 선택한 노드의 강조 표시 트리 뷰 컨트롤의 전체 너비에 맞지 않습니다.**

#### <a name="icons"></a>아이콘
 항목 간의 차이 시각적으로 식별 하는 데 도움이 하는 경우에 아이콘 트리 뷰 컨트롤에서 사용 해야 합니다. 일반적으로 아이콘 아이콘 요소 형식을 구분 하기 위한 정보를 수행할 수 있는 유형이 다른 목록 에서만에서 사용할 수 해야 합니다. 유형이 같은 목록에서 아이콘을 사용 하 여 소음으로 자주 볼 수 있습니다 피해 야 합니다. 이 경우 그룹 아이콘 (부모) 내 항목의 형식을 전달할 수 있습니다. 이 규칙의 예외 아이콘 동적 되며 상태를 나타내는 데 사용 되는 것입니다.

#### <a name="scroll-bars"></a>스크롤 막대
 스크롤 막대를 콘텐츠 트리 뷰 컨트롤에 맞으면에 항상 숨깁니다. 스크롤 막대에 대 한 허용 되는 스크롤 가능한 창에서 숨겨진 또는 반투명 하 게 될 및 트리 뷰를 포함 하는 창에 포커스가 있으면 나타나거나 트리의 가리키기 시 자체를 보려면

 ![스크롤 막대를 사용 하 여 뷰를 트리](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")

 **내용이 있는 트리 뷰 컨트롤의 한계를 초과 하는 세로 및 가로 스크롤 막대가 모두 표시 됩니다.**

### <a name="BKMK_TreeViewInteractions"></a> 상호 작용

#### <a name="context-menus"></a>상황에 맞는 메뉴
 트리 뷰 노드에 상황에 맞는 메뉴에서 하위 메뉴 옵션을 표시할 수 있습니다. 일반적으로이 사용자가 항목을 마우스 오른쪽 단추로 클릭 하거나 선택한 항목에 사용 하는 Windows 키보드에서 메뉴 키를 누를 때 발생 합니다. 것이 중요 노드에 포커스를 획득 하 고 선택 합니다. 이렇게 하면 사용자에 속하는 하위 메뉴 항목을 식별 합니다.

 ![선택된 된 트리 노드 및 상황에 맞는 메뉴](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")

 **사용자에 게 상황에 맞는 메뉴 향상 포커스 항목 생성에 항목 선택 되었습니다.**

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
 Trid 컨트롤은 grid에서 트리 뷰를 포함 하는 복잡 한 제어 합니다. 확장, 축소 및 트리를 탐색한 다음 내용을 추가 하 여 트리 뷰로 동일한 키보드 명령을 따라야 합니다.

- **오른쪽 화살표:** 노드를 확장 합니다. 노드가 확장 된 후 지속 되는 가장 가까운 열 오른쪽으로 이동 합니다. 행의 끝에서 탐색 중지 해야 합니다.

- **탭:** 오른쪽에 가장 가까운 셀으로 이동합니다.  행의 끝을 탐색 다음 행으로 계속 됩니다.

- **Shift + Tab:** 왼쪽의 가장 가까운 셀으로 이동합니다.  행의 부분을 탐색 이전 행의 오른쪽에 있는 셀을 계속합니다.

  ![Visual Studio의 Trid 컨트롤](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")

  **Visual Studio의 trid 컨트롤**
