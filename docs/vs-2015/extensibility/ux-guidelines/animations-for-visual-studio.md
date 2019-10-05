---
title: 애니메이션
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825361"
---
# <a name="animations-for-visual-studio"></a>Visual Studio의 애니메이션
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>애니메이션의 기본 사항

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio의 애니메이션 모범 사례
 Visual Studio의 IDE 전체에서 일관 되 고 사용자에 게 친숙 애니메이션 스타일을 유지 하도록 이러한 규칙을 따릅니다.

- **주의 기울여야 합니다.** 특정 용도로 사용 하는 애니메이션을 제한 합니다.

- **타이밍 및 속도 중요 한** 전환을 빠르고 자연 스러운 느낌 있는지 확인 합니다.

  - 0\.5 초 (500 밀리초) 내에서 애니메이션 된 전환이 완료 합니다.

  - 애니메이션 자주 발생 하는 사용자의 워크플로 중단 하지는 충분히 빠른 되도록 해야 합니다.

  - 따라서 빠르거나, 이해 하기 어려운 아니라 하지 너무 느려 수행 하는 하나 완료로 전환할 때 솔 임을 jarring 애니메이션 되지 않아야 합니다.

  - 중요도 강조 하기 위해 변수 타이밍을 사용 합니다. 예를 들어 클래스 다이어그램에서 항목의 시퀀스를 탐색 하면 항목 간의 전환을 통해 속도 다음 속도가 중요 한 항목에 집중할 수 있습니다.

- **점진적 비선형 감속/가속을 사용 하 여** 다른 하나의 상태에서 캄 고 자연 스러운 이동의 의미를 제공 합니다.

- 가능 하면 **미묘한 애니메이션을 사용 하 여 가리키기** 마우스에서 대화형 요소를 나타냅니다.

- 의존할 경우 과도 하 게 애니메이션 기능에서 다음 **해제할 수 있는 방법을 제공** 로컬로 (기능에 대 한 모든 사용자)에 옵션으로는 **도구 > 옵션** 대화 합니다.

- **한 번에 하나의 애니메이션 수행할지** 하나만 가지 정보를 전달 하 고 있습니다.

- **주의 해야 하는 것이 중요 합니다.** 대부분의 경우에서 애니메이션 해당 목적에 사용자 주의가 요구와 필요가 없습니다. 타이밍, 순서 지정 기능 및 동작에 약간의 변화가 인식에 크게 영향을 줄 수 있습니다 및 효과적이 고 비효율적인 애니메이션 간의 차이 만들 수 있습니다.

- 경우에 주목 하도록 애니메이션을 사용 하는 경우 **사용자 중단 가치가 있는지**의 학습 효율이 합니다.

- **진행률 또는 상태를 표시할 때** 애니메이션을 통해:

  - 기본 프로세스는 진행 되지 않으면 하는 경우 진행률 이동 표시를 중지 합니다.

  - 비활성화 프로세스에서 결정 되지 않은 프로세스를 구분 합니다.

  - 애니메이션 식별할 수 있는 완성 및 오류 상태에 있는지 확인 합니다.

  - 상태를 표시 하 고 실제 사용 시의 추가 정보를 제공 하 여 실제 값을 갖는지 여부를 지정 하는 효과 애니메이션 사용을 최소화 합니다. 예로 일시적인 상태 변경 및 응급 상황

#### <a name="do-not"></a>안 함:

- 작은 이동 (적으며 이동을)를 사용을 선호 페이드 변경 통해 개체를 이동 합니다.

- 화면 부동산의 큰 영역을 통해 수행 되는 애니메이션을 사용 합니다. 크기에 관계 없이 애니메이션의이 스타일은 사용자에 게 불필요 합니다.

- 사용자에 현재 포커스 된 개체 또는 상호 작용 하는 애니메이션을 사용 합니다.

- 사용자가 깜박임을 중지 하려면 깜박이 알림에 응답 하는 등의 상태를 다시 설정 하려면 사용자가 개입 해야 하는 애니메이션을 사용 합니다. 어떤 방식으로든에서 상호 작용을 해제 하는 데 충분 해야 합니다.

  이러한 모범 사례에 대 한 응용 프로그램에 대 한 자세한 내용은 참조 하세요. [애니메이션 패턴](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)합니다.

### <a name="animation-metrics"></a>애니메이션 메트릭

- 시스템은 사용자 제스처 10 밀리초 미만에 시각적으로 대응 해야 합니다.

- 애니메이션 된 전환이 완료 500 밀리초 보다 오래 걸리지 않습니다.

- 시간이 더 필요한 전환에 대 한 보정을 위해 한 가지 방법은; 두 부분으로 구분 하는 예를 들어 애니메이션의 첫 번째 부분 콘텐츠 페이드 뒤에 (최대 500 밀리초) 컨테이너에 빈 콘텐츠 컨테이너 (최대 500 밀리초)을 수 있습니다.

- 계산할 수 있는 로드 시간에 대 한 결정 진행률 지표 (% 완료 진행률 지표)를 선호 됩니다.

- 계산할 수 없습니다는 로드 시간, 커서 등 회전 포함 된 애니메이션 (로드 또는 작업 지표)를 사용 중 표시기가 적합 합니다.

### <a name="animation-as-communicator"></a>Communicator로 애니메이션
 Visual Studio의 ui에서 애니메이션 통신 도구로 작동합니다.  다양 한 UI;의 구조 변경 등의 정보를 통신에 사용 되 고 예를 들어 경우 메뉴 열거나 닫습니다. 애니메이션 설치 진행률 시각화와 같은 복잡 한 시스템의 시간에 따라 변하는 동작을 시각화 하는 데 도움이 또는 경고 및 알림 들의 관심을 유치 하는 데 사용할 합니다.

 UI 애니메이션은 일반적으로 네 가지 방법으로 함수: 시각화, 주의 유치, 시뮬레이션 및 응답을 표시 시간/진행 중입니다.

#### <a name="visualize"></a>시각화
 애니메이션 개체의 3 차원 특성을 강조 하 고 쉽게 해당 공간 구조를 시각화 하는 사용자에 대 한 수 있습니다. 이 위해 애니메이션 및 수 있습니다 해야 전체 원에 있는 개체를 회전 느린를 앞뒤로 전환 또는 개체에 더 가까운 곳으로 가져옵니다 약간 롤오버 또는 포커스를 강조 하기 위해 해당 크기를 늘립니다.

 3 차원 개체 (프로그래밍 방식으로 또는 수동으로) 디자이너에서 미리 결정 하는 사용자 정의 컨트롤을 사용 하 여 이동할 수 있습니다 하지만 어떻게 최적의 애니메이션 효과 주기 최적의 이해가 개체를 제공 하는 이동 합니다. 이 애니메이션 수 프로그래밍 다음 개체를 조작 하는 방법을 이해 해야 할 사용자 제어 이동 하는 반면 개체에 대해 커서를 배치 하 여 사용자가 활성화할 수 있습니다. 단일 축 또는 방향에서는 한 번에 이동 제한 크기 조정, 회전, 또는 중를 하나만 동시에 둘 이상 수행 하지 마십시오.

 시각화 범주에 포함 된 데이터, 관계, 상태의 측면을 구조, 시퀀스 및 시간입니다.

##### <a name="data"></a>보기
 복잡 하 고 변수 정보를 보여 줍니다.

- 차트 및 그래프와 같은 정보 시각화를 통해 이동합니다.

- 시퀀스를 통해 단계별 실행, 둘러보기, 및 페이징

- 세부 정보 호출 가리키고 특정 정보를 강조 표시

- 세부 정보 및 추가 정보는 포커스가 있는 요소 위에 오버레이

- 다른 하나의 구조 또는 조직 표현에서 모핑

- 시간 슬라이더, 조깅 셔틀 바퀴 및 전송 컨트롤 (play, stop 및 pause)를 사용 하 여 시간이 지남에 따라 변경 내용을 나타내는입니다.

##### <a name="relationships"></a>관계

- 지정 된 항목과 관련 된 항목 또는 항목 간 관계를 보여 줍니다.

- 계층 및 부모-자식 또는 형제 관계 표시

- 다른 하나의 요소 생성

- 하나의 요소가 다른 요소에 최소화

- 다른 테더 링 된 하나의 요소

##### <a name="state"></a>State

- 콘텐츠 업데이트 합니다.

- 사용자 포커스 및 선택

- 진행률

- 오류

##### <a name="structure"></a>구조

- 노드 하나에서 구조를 피벗

- 방향을 새로 설정

- 최소화, 최대화 또는 확장 및 축소

##### <a name="sequence"></a>Sequence

- 슬라이드 쇼 시퀀스

- 그림을 통해 대칭 이동

##### <a name="time"></a>시간

- 시간, 시간 경과 및 스크린 캐스트를 통해 표시 변경

- 휴지통, 실행 취소 및 다시 실행 이동

- 기록 상태를 복원 합니다.

#### <a name="attract-attention"></a>주의 유치
 목표에서 여러 단일 요소에 대 한 사용자의 주목 하도록 또는 사용 하도록 업데이트 된 정보를 알리는 경우 애니메이션 적절 한 수 있습니다. 예를 들어, 응용 프로그램 시작 페이지는 페이지가 로드 된 후에 슬라이드 하는 시작 단추를 채택할 수 있습니다.

 일반적으로 화면의 마지막 이동 요소 동안 사용자의 관심을 유도 합니다.  애니메이션 요소 계열에서 사용자의 주의 마지막 개체가 이동 될 예정입니다.

##### <a name="alert"></a>경고

- 사용자 경고, 주의 수신 하 고, 진행률 표시

- 작업 중인 수행 되도록 올바르게 또는 잘못 표시 또는 진행 중 또는 진행 중인 변경

- 자세한 내용은 온라인 찾기 또는 현재 작업에 대 한 학습 등의 작업을 하는 동안 사용자에 게

##### <a name="notifications"></a>알림

- 오류가 발생 하는 방법에 대 한 사용자 알림

- 사용자에 게 다른 일에 참여 하려는 경우 표시를 중단 합니다.

- 조심 스럽게 프로세스 완료 되거나, 다운로드가 완료 되 면 같은 변경 하는 사용자를 게 알립니다.

#### <a name="simulate"></a>시뮬레이션
 이 범주에는 여실히 및 차원을 설명합니다.

- 개체에서 발생 한 위치 또는 이동할 위치를 보여 줍니다.

- 확장 및 축소 또는 열기 및 닫기

- 팬, 스크롤 및 페이지 설정

- 스택 및 z 순서

- Accordion을 만들어서 캐 러셀

- 대칭 이동 및 회전 UI

#### <a name="response-and-progress-indicators"></a>응답 및 진행률 표시기
 진행률 표시기에는 몇 가지 주요 장점이 있습니다.

- 두 확정적이 지 및 부정형 진행률 지표에는 시스템에서 반복적인 충돌이 발생 하 고 문제에 작동 하는 사용자를 원할 것입니다.

- 비활성화 상태 표시기 to the 마침 좀 더 자세히 가져오는 느낌 뿐 아니라 작업 진행 정도 쉽게 진행 중인 사용자에 게 제공 합니다.

## <a name="BKMK_AnimationPatterns"></a> 애니메이션 패턴

### <a name="overview"></a>개요
 Visual Studio에서 애니메이션은 특정 기능을 제공 하 여 사용자 생산성을 방해 하지 것입니다. 포함 하도록 준수 일반 애니메이션 특징:

- 작고 비간섭

- 자연스럽 고 현실적인

- 미묘 하 고 게 당한 후

- 빠르고 효율적으로

- 완화 되지 hurried

  다음 그림에서는 Visual Studio에서 사용 하기 위해 권장 되는 애니메이션 스타일을 보여 줍니다. 미묘한 애니메이션 없고 애니메이션 같은 페이드 인/페이드 아웃을 적용은 가장 자주 사용 됩니다. 와 같은 확장 및 축소 애니메이션 이동 제한 application, X 및 Y 위치 변경 및 회전 합니다.

  ![Visual Studio에 대 한 권장 되는 애니메이션 스타일](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 a_VSAnimStyles")

  **Visual Studio에 대 한 권장 되는 애니메이션 스타일**

#### <a name="appear-and-disappear"></a>사라질
 이 패턴을 사용 하 여 요소 축소의 보기를 전환 애니메이션 없이 다시 표시를 전환합니다.

 ![표시&#47;Visual Studio에서 애니메이션 사라집니다](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 b_AppearAndDisappear")

##### <a name="correct-usage"></a>올바른 사용법
 새로운 UI 요소는 즉시 나타나거나 사라질 사용자 사항 아니고 려 되도록 해야 합니다. 또한 성능 끌기 및 사라집니다 나타납니다 스타일을 사용 하 여 발생 하지 않습니다는 느린 이동 애니메이션 간주 될 수 있습니다.

##### <a name="incorrect-usage"></a>잘못 된 사용
 경우는 UI, 내용 갑자기 사용자 알지 표시 되 고 상황별 이해를 사용 하 여는 데 도움이 되는 애니메이션을 추가 합니다.

##### <a name="animation-properties"></a>애니메이션 속성
 시간 지연을 일반적으로 0 초입니다.

##### <a name="examples"></a>예

- 도구 창 자동 숨기기

- 바로 활성화 편집기 IntelliSense 및 매개 변수 도움말과 같은 UI

- 확장-축소 코드 영역

#### <a name="fade-in-and-fade-out"></a>페이드 인 및 페이드 아웃
 이 패턴을 사용 하 여 UI 요소 표시 되지 않습니다 (불투명도 0%)에서 전환 표시 (100% 불투명) 또는 그 반대로 합니다.

 ![Fade&#45;에서&#47;페이드&#45;Visual Studio에서 애니메이션 아웃](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 c_FadeInFadeOut")

##### <a name="correct-usage"></a>올바른 사용법
 이 UI 애니메이션 가장 일반적으로 좋습니다. 흐름이 중단 되지 않도록 관심을 추가 하는 미묘한 효과 것입니다. 경우에 따라 사용자 조차 모를 수 있는 애니메이션을 단순히 원활 하 고 흐르는 UI 시스템을 인식 합니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 불투명도 시작 합니다. 페이드 인, 페이드 아웃에 대 한 100 %%0

- 불투명도 종료 합니다. 페이드 인, 페이드 아웃에 대 한 0%에 대 한 100%

- 기간: 독립 실행형 200 밀리초 조합 애니메이션 시퀀스의 일부로 사용 되는 경우 100 밀리초

- 감속/가속 스타일: Sine InOut

##### <a name="examples"></a>예

- 도구 창 자동 숨기기

- 메뉴 열기 및 닫기

- 배경 및 전경 탭 전환

#### <a name="color-blend-from-a-to-b"></a>A에서 B로 색 혼합
 이 패턴을 사용 하 여 UI 요소는 색에서 색으로 변경 b:

 ![Visual Studio에서 색 혼합 애니메이션](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 d_ColorBlend")

##### <a name="correct-usage"></a>올바른 사용법
 으로 UI 요소를 한 컨텍스트나 상태에서 다른 색을 변경 하는 경우 애니메이션된 전환입니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 시작 색: UI 관련

- 끝 색: UI 관련

- 기간: 독립 실행형 200 밀리초 조합 애니메이션 시퀀스의 일부로 사용 되는 경우 100 밀리초

- 감속/가속 스타일: Sine InOut

##### <a name="examples"></a>예

- 문서 창 상태 전환 (활성, 마지막으로 활성 및 비활성)

- 도구 창 상태 전환 (포커스 및 포커스 없음)

#### <a name="expand-and-contract"></a>확장 / 축소
 이 패턴을 사용 하 여 X, Y 또는 양쪽 방향에서 UI 요소를 확장합니다.

 ![확장&#47;Visual Studio에서 애니메이션 계약](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 e_ExpandContract")

##### <a name="correct-usage"></a>올바른 사용법
 으로 UI 요소를 특정 컨텍스트에서 다른 크기를 변경 하는 경우 애니메이션된 전환입니다.

##### <a name="animation-properties"></a>애니메이션 속성

- X 배율: % 또는 특정 차원 (픽셀)

- Y 크기 조정: % 또는 특정 차원 (픽셀)

- 앵커 위치: 일반적으로 (왼쪽에서 오른쪽 언어용) 왼쪽 위 또는 왼쪽 (오른쪽에서 왼쪽 언어용)

- 기간: 독립 실행형 200 밀리초 조합 애니메이션 시퀀스의 일부로 사용 되는 경우 100 밀리초

##### <a name="examples"></a>예

- 아키텍처 탐색기 패널 확장 및 축소

- 시작 페이지 항목 확장 및 축소

#### <a name="x-y-position-change"></a>X, Y 위치 변경
 이 패턴을 사용 하 여 UI 요소를 X 또는 Y 위치 또는 둘 다 변경합니다.

 ![X&#47;Visual Studio에서 애니메이션을 변경 하는 Y 위치](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 f_XYPositionChange")

##### <a name="correct-usage"></a>올바른 사용법
 UI 요소를 특정 컨텍스트에서 다른 위치를 변경 하는 애니메이션된 전환으로 합니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 시작 X 및 Y 위치: UI 관련

- 종료 X 및 Y 위치: UI 관련

- 이동 패스: 없음

- 기간: 독립 실행형 200 밀리초 조합 애니메이션 시퀀스의 일부로 사용 되는 경우 100 밀리초

- 감속/가속 스타일: Sine InOut

##### <a name="example"></a>예제
 탭 순서 변경

#### <a name="rotate"></a>Rotate
 이 패턴을 사용 하 여 UI 요소 회전

 ![Visual Studio에서 회전 애니메이션](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 g_Rotate")

##### <a name="correct-usage"></a>올바른 사용법
 비활성화 회전 진행률 표시기에 대해서만입니다.

##### <a name="animation-properties"></a>애니메이션 속성

- 회전 각도입니다. 360

- 회전 중심: 개체의 중간

- 기간: 연속

##### <a name="example"></a>예제
 비활성화 상태의 진행률 표시기 (회전)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>일반적인 셸 UI 작업 및 권장 되는 애니메이션

#### <a name="tab-open"></a>탭 열기

- Style: 표시

- 기간: 0 초

  ![Visual Studio에서 열기 애니메이션 탭](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 h_TabOpen")

#### <a name="tab-close"></a>탭 닫기

- Style: X 위치 변경

- 기간: 200 밀리초

  ![Visual Studio에서 닫기 애니메이션 탭](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 i_TabClose")

#### <a name="tab-reorder"></a>탭 순서 변경

- Style: X 위치 변경

- 기간: 200 밀리초

  ![Visual Studio에서 순서 바꾸기 애니메이션 탭](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 j_TabReorder")

#### <a name="close-floating-document"></a>부동 문서 닫기

- Style: 표시

- 기간: 200 밀리초

  ![Visual Studio에서 문서 애니메이션 부동 닫기를](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>창 상태 전환

- Style: 다른 windows 일관 되도록 문서 닫기 애니메이션을 정의 하는 현재 운영 체제를 수 있습니다.

- 기간: 200 밀리초

  ![Visual Studio에서 창 상태 전환 애니메이션](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 l_WindowStateTransition")

#### <a name="menu-open"></a>메뉴 열기

- Style: 페이드 인

- 기간: 200 밀리초

  ![Visual Studio에서 메뉴 열기 애니메이션](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 m_MenuOpen")

#### <a name="menu-close"></a>메뉴 닫기

- Style: 페이드 아웃

- 기간: 200 밀리초

  ![Visual Studio에서 메뉴 닫기 애니메이션](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>자동 숨기기 도구 창 표시

- Style: 표시

- 기간: 0 초

  ![자동&#45;Visual Studio에서 도구 창 애니메이션을 숨기려면](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")
