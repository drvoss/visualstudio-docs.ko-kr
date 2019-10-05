---
title: UX Essentials
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3ed2d3f8bc52b21f6a87ac7d6da00f665f6b28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181483"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio 용 UX Essentials
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>모범 사례

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio 환경 내에서 일관 되어야 합니다.

- 셸 내에서 기존 상호 작용 패턴을 따릅니다.

- 셸의 visual 언어 및 장인 요구 사항 일치 하는 기능을 디자인 합니다.

- 있을 경우 공유 명령 및 컨트롤을 사용 합니다.

- Visual Studio 계층 및 컨텍스트를 설정 및 UI를 구동 하는 방법을 이해 합니다.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. 글꼴 및 색에 대 한 환경 서비스를 사용 합니다.

- UI는 사용자 지정 글꼴 및 색 페이지 옵션 대화 상자에서 표시 되는 경우가 아니면 현재 환경 글꼴 설정을 따라야 합니다.

- UI 요소에는 공유 환경 토큰 또는 기능별 토큰을 사용 하 여 VSColor Service를 사용 해야 합니다.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. 모든 이미지를 새 VS 스타일을 사용 하 여 일관 되 게 합니다.

- 아이콘, 문자 모양 및 기타 그래픽에 대 한 Visual Studio 디자인 원칙을 따릅니다.

- 그래픽 요소에 텍스트를 배치 하지 마십시오.

### <a name="4-design-from-a-user-centric-perspective"></a>4. 사용자 중심의 관점에서 디자인 합니다.

- 내의 개별 기능 하기 전에 작업 흐름을 만듭니다.

- 사용자가 잘 알고 있어야 하 고 해당 정보를 사용자 사양에 명시적으로 만들어야 합니다.

- UI를 검토 하는 경우 전체 환경 뿐만 아니라 세부 정보를 평가 합니다.

- 기능 및 로캘이나 언어에 관계 없이 매력적인 유지 하도록 UI를 디자인 합니다.

## <a name="screen-resolution"></a>화면 해상도

### <a name="minimum-resolution"></a>최소 해상도
 Visual Studio Dev14 최소 해결책은 1280 x 1024입니다. 즉, 것 *가능한* 최적의 사용자 환경을 것이 확인에서 Visual Studio를 사용 하 합니다. 모든 측면은 1280 x 1024 보다 낮은 해상도로 사용할 수는 보장이 없습니다.

 초기 대화 상자 크기가 1000 96dpi에서이 최소 해상도 이내 IDE의 프레임 내에 있도록 높이 픽셀을 넘지 않아야 합니다.

### <a name="high-density-displays"></a>고밀도 표시
 Visual Studio의 UI는 모든 DPI 배율 기본적으로 지 원하는 Windows에서 잘 작동 해야 합니다. 150%, 200%에 만들어지고 250%입니다.

## <a name="anti-patterns"></a>안티패턴
 Visual Studio는 지침 및 모범 사례는 UI의 많은 예제를 포함 합니다. 일관성을 유지 하기 위해, 개발자는 종종 작성 하는 유사한 제품 UI 디자인 패턴에서 차용 합니다. 이 사용 하면 사용자 상호 작용 및 시각 디자인의 일관성을 드라이브 우리를 수행할 경우에 따라 제공 하는 기능 우선 순위 지정을 제거 하거나 일정 제약 조건으로 인해 지침을 충족 하지 않는 몇 가지 세부 정보를 사용 하 여 좋은 방법입니다. 이러한 경우에 하지 팀이 이러한 "안티 패턴" 중 하나를 복사 하므로 Visual Studio 환경 내에서 잘못 되었거나 일관 되지 않은 UI 급부상 하 고 있습니다.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>기본적으로 오류 상태에 표시 하는 필수 필드/설정

#### <a name="feature-team-goals"></a>기능 팀의 목표

- 사용자 추가 했다고 구성 해야 하는 요소에 대 한 경고를 표시 합니다.

- 사용자의 주를를 입력 해야 하는 영역을 그립니다.

#### <a name="anti-pattern-solution"></a>안티패턴 솔루션
 사용자가 작업을 시작 하는 즉시 및 이러한 작업을 완료 하기 전에 즉시 구성 해야 하는 영역 옆에 있는 중요 한 중지 아이콘을 배치 합니다.

#### <a name="example-manifest-designer-declarations"></a>예제: 매니페스트 디자이너 선언
 선언 목록에 즉시 추가 사용자 필수 속성이 설정 될 때까지 유지 하는 오류 상태에 배치 됩니다.

 이 경우 추가 문제는 경고에 사용 되는 아이콘 "x"가 포함 되어 있으므로 그 옆에 있는 아이콘을 사용할 수 있으므로 일반적인 제거. 결과적으로, UI 컨트롤을 더 이상 사용 하지 않게 제거 단추를 사용합니다.

 ![매니페스트 디자이너 오류 선언 맬웨어 방지&#45;패턴](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti 패턴")

 **Visual Studio 안티패턴은 기본적으로 UI 오류 상태에 배치 합니다.**

#### <a name="alternatives"></a>대체 형식
 이 문제를 훨씬 더 나은 솔루션을 해야 합니다.

- 경고 없이 선언에 추가할 사용자를 허용 하 고 항목 속성을 설정 하려면 즉시 이동 합니다.

- 경고 아이콘 (gold 삼각형)을 추가할 때 포커스가 이동 된 항목에서와 같은 다른 선언 목록에 추가 하거나 디자이너 내에서 탭을 변경 하려고 합니다.

- 사용자가 선언에서 속성을 설정 하기 전에 탭을 변경 하려고 하는 경우 응용 프로그램이 빌드되지 것입니다 설명 대화 상자 표시 (또는 원하는 의미) 경고를 해결 합니다. 사용자 대화 상자를 해제 하 고 탭을 변경 하는 경우 계속 다음 아이콘 (위험 또는 경고, 필요에 따라)에 추가 됩니다 선언 탭.

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>사용자가 UI를 해제 하기 전에 텍스트 읽기

#### <a name="feature-team-goals"></a>기능 팀의 목표
 첫 번째는 설명 텍스트를 표시 하지 않고 UI를 해제 하려면 사용자를 허용 하지 마십시오.

#### <a name="anti-pattern"></a>안티패턴
 X의 일반적인 패턴에 대해 결정 VS UI 내에서 다양 한 위치에 비디오 링크를 삽입 하는 팀 UX에 지정 된 대로 단추 및 도구 설명을 설명 닫고 대신을 드롭다운 하 고 "다시 표시 안 함" 링크를 구현 합니다.

 ![앤티 설명 텍스트&#45;패턴 &#45; 잘못](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **: 잘못 된 사용자가 UI를 해제 하기 전에 설명 텍스트를 읽기 강제 Visual Studio 내에서 안티패턴은입니다.**

#### <a name="result"></a>결과
 간단한 닫기 단추 (한 번의 클릭) 하는 대신 사용자는 단순히 UI 비디오 링크가 표시 되는 모든 위치를 해제 하려면 두 번 클릭을 사용 하도록 강제 됩니다.

#### <a name="alternatives"></a>대체 형식
 Internet Explorer, Office 및 Visual Studio에 일반적인 패턴에 따라이 상황에 맞는 올바른 디자인 됩니다: 사용자 마우스로 가리키면 도구 설명을 볼 수 고 한 번의 클릭 UI를 숨깁니다.

 ![앤티 설명 텍스트&#45;패턴 &#45; 올바른](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti 패턴 수정")

 **올바른: 비디오 링크가 추가 정보와 함께 도구 설명이 마우스로 가리키면 표시 되 설계 된 대로, 및 "X"를 클릭 하면 사용자가 개입할 필요 없이 메시지를 해제 해야 합니다.**

### <a name="using-command-bars-for-settings"></a>명령 모음 설정에 대 한 사용
 ![앤티 명령 모음&#45;패턴 &#45; 그림 A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-패턴-FigureA")

 **그림 a: 명령 모음 안티패턴**

 **그림 A** 이 안티패턴을 나타냅니다: 명령만 이상에 적용 되는 명령 단추 아래에 있는 설정을 배치 합니다. 이 스케치에서은 디버깅을 시작 하는 것 외에도 명령-형식 브라우저 디버깅 하지 않고 시작 되 고 한 단계씩 코드 실행 보기-선택한 설정 존중입니다.

 ![앤티 명령 모음&#45;패턴 &#45; 그림 B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-패턴-FigureB")

 **그림 b: Better, 있지만 명령 모음 안티패턴**

 에 표시 된 대로 약간 더 나은 하지만 여전히 바람직하지 도구 모음에서이 유형의 설정 배치 됩니다 **그림 B**합니다. 분할 단추 적은 공간을 차지 하 고 드롭다운을 통해 개선 되므로, 모두 디자인 여전히 사용 하 여 도구 모음 명령을 실제로 그리 승격 합니다.

 ![앤티 명령 모음&#45;패턴 &#45; 그림 C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-패턴-FigureC")

 **그림 c: Visual Studio 명령 모음 패턴의 올바른 사용**

 **그림 C**, 설정을 일련의 명령에 연결 됩니다. 설정할 전역 설정은 없습니다 및 방금 4 개 명령은 간에 전환 하는 것입니다. 도구 모음에서 명령을 허용 되는 경우에만입니다.

### <a name="control-anti-patterns"></a>컨트롤 안티패턴
 몇 가지 안티패턴은 단순히 잘못 된 사용 또는 프레젠테이션 컨트롤 또는 컨트롤 그룹입니다.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>하이퍼링크 없습니다을 그룹 레이블로 사용 되는 밑줄 표시
 하이퍼링크에 대 한 밑줄 텍스트를 사용 해야 합니다.

 **잘못 된:**

 ![앤티 밑줄 표시&#45;그룹 레이블에서 패턴](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 g_GroupLabelIncorrect")

 **밑줄이 그어진된 텍스트 하이퍼링크 하지 않은 경우 Visual Studio 안티패턴**

 **좋은:**

 ![앤티 밑줄 표시&#45;그룹 레이블에서 패턴 &#40;올바른&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 h_GroupLabelCorrect")

 **올바르게 스타일 아닌 하이퍼링크 텍스트 표시 되지 않은 환경 글꼴로 표시 합니다.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>팝업 대화 상자에서 확인란 결과 클릭
 즉시 "Windows Azure 응용 프로그램 게시" 마법사에서 "모든 역할에 대 한 원격 데스크톱 사용" 확인란을 클릭 하면 팝업 대화 상자, Visual Studio 안티패턴 나타납니다. 또한 확인란 필드를 채우지 않은 확인란이 선택 된 후 다른 상호 작용 안티패턴입니다.

 ![확인란 팝업&#45;최신 맬웨어 방지&#45;패턴](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 i_CheckboxPopup")

 **Visual Studio 안티패턴은 확인란을 클릭 한 후 대화 상자를 불러오는 합니다.**

### <a name="hyperlink-anti-patterns"></a>하이퍼링크 안티패턴
 다음 예제에서는 두 가지 안티 패턴을 포함합니다.

1. Hover에 빨간색 켜기 전경은 글꼴 서비스에서 올바른 공유 색 사용 하지 않는 것을 의미 합니다.

2. 개념 항목에 대 한 링크에 대 한 적절 한 텍스트 아닙니다 "자세히". 사용자의 목표는 없습니다. 자세한 내용은 해당 선택의 결과 이해 하는 것입니다.

   ![앤티 하이퍼링크&#45;패턴](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")

   **무시 컬러 서비스와 "자세한 내용을 보려면" 대 한 하이퍼링크를 사용 하 여 Visual Studio 안티 패턴입니다.**

   **더 나은 솔루션:** 링크를 클릭 하 여 사용자 요청 하는 질문을 제기 합니다.

- Windows Azure 서비스는 어떻게 작동 하나요?

- Windows Azure Mobile Services 프로젝트를 경우 해야 하나요?

#### <a name="using-click-here-for-links"></a>링크에 대 한 "여기 클릭"을 사용 하 여
 하이퍼링크는 자체 설명적 이어야 합니다. "여기를 클릭"을 사용 하는 것이 안티패턴 또는 비슷한 변형입니다.

 **잘못 된:** "여기를 클릭 새 프로젝트를 만드는 방법에 대 한 지침은."

 **좋은:** "새 프로젝트를 어떻게 만들 수행"?
