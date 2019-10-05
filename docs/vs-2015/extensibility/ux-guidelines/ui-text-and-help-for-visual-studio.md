---
title: UI 텍스트 및 도움말
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea4f2b49838340fcee41bc9c41ef94558e44825e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823618"
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI 텍스트 및 Visual Studio에 대 한 도움말
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_UITextAndTerminology"></a> UI 텍스트 및 용어
 포괄적 텍스트 매우 효과적인 UI에 중요 합니다. 소프트웨어 사용자가 읽을 경향이 레이블을 먼저 해당 namely 당면한 작업을 완료 하는 게 가장 적합 합니다. 정적 텍스트 적은 빈도로 읽힙니다. 대략적인 순서로 UI의 읽을 뒤에 전체 창에 빠른 검색을 사용 하 여 해당 작업 세션을 시작 하도록 계획 합니다.

1. 센터에서 대화형 컨트롤

2. 커밋 단추

3. 어딘가에 있는 대화형 컨트롤

4. 기본 지침

5. 추가 설명

6. 창 제목

7. 다른 정적 텍스트 본문에서

### <a name="usage-patterns-for-ui-text"></a>UI 텍스트에 대 한 사용 패턴

#### <a name="title-bar-text"></a>제목 표시줄 텍스트
 제목 표시줄 텍스트에는 UI를 생성 하는 명령을 일치 해야 합니다.

#### <a name="instructional-text-helper-text"></a>지침 텍스트 (도우미 텍스트)
 일부 대화 상자에서 페이지 또는 창에서 수행할 작업을 설명 하는 주요 기본 지침을 제공 하는 것이 유용 합니다. 이 경우에 따라 라고 "도우미 텍스트입니다."

##### <a name="writing-style-rules-for-helper-text"></a>도우미 텍스트에 대 한 스타일 규칙 작성

- 명백한 설명 하지는 마십시오. 반드시 필요한 경우가 아니면 지침 텍스트를 포함 하지 않습니다.

- 지침 텍스트 항상 대화 상자의 위쪽에 놓이고 수행 중인 작업을 참조 해야 합니다.

- 사용자에 게 수행 해야 할 사항을 설명 정확 하 게 합니다. 과도 한 통신 및 중복을 방지 합니다.

- 각 창을 검토 하 고 중복 된 단어 및 문을 제거 합니다.

- 짧은 지침 텍스트를 유지 합니다. 자세한 정보는 필요한 특정 사용자 또는 시나리오, 자세한 온라인 개념 항목에 대 한 링크를 제공 합니다.

- 모든 단어 가중치를 보유 하 고 필요한 텍스트를 씁니다.

- 에 대 한 기존 Microsoft 지침을 따릅니다 [사용자 인터페이스 텍스트](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) 하 고 [스타일 및 어조](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)합니다.

#### <a name="supplemental-instructions"></a>추가 지침
 추가 지침은 사용자가 컨트롤을 이해 하거나 그룹화를 제어할 수 있도록 추가 정보를 제공 합니다. 힌트 텍스트 입력된 컨트롤을 예상 하는 어떤 형식으로 이해 하는 데 필요한 포함 될 수 있습니다. 추가 지침을 제한적으로 사용 합니다. 사용자 선택 항목을 맺는 것의 결과 완전히 이해 하지 않습니다 가능성이 인 경우 해당를 예약 합니다.

 ![Visual Studio의 추가 텍스트](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601 b_SupplementalText1")

 **Visual Studio의 추가 텍스트**

 ![Visual Studio의 추가 텍스트](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601 c_SupplementalText2")

 **Visual Studio의 추가 텍스트**

#### <a name="infotips"></a>InfoTips
 종종 지침 텍스트 전체 UI에서 위치로 길어질 수 있습니다 또는 숙련 된 사용자에 게 혼란을 여겨질 새 사용자 에게만 유용할 수 있습니다. 이 경우 정보/사용 안내 텍스트 정보 팁에서 도구 설명으로 배치 되어야 합니다.

 정보 팁 눈에 띄는 아직 방해가 되지 않는 특정 정보 팁 아이콘을 사용 해야 관련 된 컨트롤은 거의 배치 되어야 합니다.

 ![Visual Studio에서 InfoTip](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")

 **Visual Studio의 정보 팁 예제**

##### <a name="writing-style-rules-for-infotips"></a>정보 팁에 대 한 스타일 규칙 작성

- 완전 한 문장으로 정보 팁을 작성 합니다. 특정 동사, 문장 및 문장 부호 필요 합니다.

- 사용자의 기본 명령 또는 정보를 보완 하기 위해 정보 팁을 사용 합니다. 사용 하 고 있는 다른 단어 주요 개념을 다시 말하지만, 정보 팁 필요가 없습니다.

- 짧고 정보 팁을 유지 합니다. 간단한 단어 및 일반을 사용 하 여 일상적인 언어를 지원 하 고 사용자를 권장 합니다.

- 에 대 한 기존 Microsoft 지침을 따릅니다 [사용자 인터페이스 텍스트](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) 하 고 [스타일 및 어조](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)합니다.

#### <a name="control-labels"></a>컨트롤 레이블
 컨트롤 레이블 짧은, 간결 하며 수행 합니다 [컨트롤에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)합니다.

 컨트롤 레이블 형식 및 UI 내에서 배치 하는 방법에 대 한 자세한 내용은 참조 [Visual Studio에 대 한 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md)합니다.

#### <a name="help-links"></a>도움말 링크
 도움말 링크 되는 지침 텍스트 내에서 또는 UI의 본문에 배치할 수 있습니다. 도움말 링크를 하거나 내부 대화 상자를 시작할 수 있습니다.

##### <a name="visual-style-rules-for-help-links"></a>도움말 링크에 대 한 비주얼 스타일 규칙

- 하이퍼링크에 대 한 올바른 환경 색을 사용 합니다. 제대로 스타일이 적용 된 하이퍼링크를 클릭할 때 빨간색 간단 하 게 플래시 되지 않습니다. 표시 되 면이 환경 색 사용 하지 않는 표시 됩니다.

- 밑줄은 가리킨 항목 또는 링크를 단락에 포함 된 경우에 사용 해야 합니다.

- 하이퍼링크에 대 한 시각적 개체와 상호 작용 스타일에 대 한 자세한 내용은 단추, 하이퍼링크를 참조 하세요.

##### <a name="writing-style-rules-for-help-links"></a>도움말 링크에 대 한 스타일 규칙 작성

- 대화 상자를 시작할 때에 타원의 표준을 유지 관리: 탐색, 줄임표 필요한 추가 UI 작업에 대 한 줄임표 없습니다.

     ![Visual Studio에서 도움말 링크](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601 e_HelpLink")

     **태스크 UI를 추가 해야 합니다. 도움말 링크에는 줄임표 (...)를 나타냅니다.**

- 사용자의 의도 된 대로 링크 "학습,"로 시작 하지 않아야 합니다. 사용자가 특정 질문에 대답, 일반적인 교육을 받지 하려고 합니다.

- 구 도움말 항목에 응답 하는 질문을 요청할 수 있도록 연결 합니다.

     잘못된 예:    "Windows Azure Mobile Services 가격 책정 자세히 알아보기"

     맞는:    "어떤 가격 옵션은 Windows Azure Mobile Services에 사용할 수 있는"?

- 사용 하지 마십시오 *클릭...* 링크 텍스트입니다.

- 되지 링크만 단어 "여기"입니다. 하이퍼링크 단어만 음성는 일부 화면 읽기 프로그램의 경우 문제가 됩니다.

     잘못된 예:    "Windows Azure Mobile Services에 대 한 정보를 찾으려면 **여기**"

     맞는:    "어떤 가격 옵션은 Windows Azure Mobile Services에 사용할 수 있는"?

- 도움말 링크에 대 한 올바른 필기 스타일에 대 한 자세한 내용은 참조는 [도움말에 대 한 Windows 데스크톱 지침](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx)합니다.

#### <a name="hint-text"></a>힌트 텍스트
 컨트롤 내에서 컨트롤 또는 아래 워터 마크로 힌트 텍스트가 표시 됩니다. 적절 한 VSColors 토큰을 사용 하 여 올바른 서식이 적용 될 `Environment.GrayText`합니다.

 다양 한 폼에서에서 나타날 수 있습니다.

- 대신 컨트롤 레이블:

     ![Visual Studio에서 텍스트를 힌트로](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601 f_HintText1")

- 동사를 사용 하 여 지침을 제공 합니다.

     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601-g_HintText2")

- 텍스트를 사용 하 여 필요한 항목을 나타내는:

     ![Visual Studio에서 텍스트를 힌트로](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601 h_HintText3")

#### <a name="watermark-text"></a>워터 마크 텍스트
 빈 디자인 화면에서을 수행할 수 있을 뿐만 아니라 해당 하는 경우 다른 관련된 창 열기에 대 한 링크를 제공 텍스트를 나타내야 합니다.

 ![Visual Studio에서 텍스트를 워터 마크](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601 i_WatermarkText")

 **Visual Studio에서 워터 마크 텍스트의 예**

### <a name="common-terminology"></a>일반적인 용어

|용어|설명|설명|
|----------|-----------------|-------------|
|로그인/로그 아웃|동사를 나타내는 웹 속성에 대 한 인증에 대 한 웹과 같은 뜻으로 사용 합니다. 클라이언트 내에서 사용이 한 번 최상위 개념으로 IDE 사용자 연결에서 로밍 하는 라이선스 등 더 높은 수준의 기능을 다른 모든 연결과 함께 사용할 수 없는 제공 하는 최상위 id를 나타내는 내부 및 외부로 서명 합니다.|IDE 사용자 로그인을 나타내는 / 동사를 로그 아웃 해야 하는 유일한 기능은 최상위 IDE를 나타냅니다.|
|연결/연결 끊기|위치 기능 온라인 서비스에 단일 연결을 유지 하는 위치에서 사용 합니다.|서버 탐색기를 사용할 수 있는 한 번에 하나의 활성 Azure 연결에는 연결/연결 끊기의 예시입니다.|
|추가/제거|비-삭제 합니다. 추가 하거나 목록에서 항목을 제거 하는 경우 사용 합니다.|TFS 연결 관리자 서버 목록 대화 상자는 추가/제거의 예시입니다.|
|삭제|삭제 합니다. 요소가 제거 되는 경우에 사용 하 여 영구적으로 삭제 되거나 디스크에서 삭제 합니다.|결과 디스크에서 파일을 삭제 하는 경우에 프롬프트를을 해야 일반적으로 "삭제" 합니다.|

## <a name="error-messages"></a>오류 메시지

### <a name="overview"></a>개요
 오류가 발생 합니다. 제한 사항 사용자 수행할 수 있는 설정은 피할 수 있는 오류 메시지를 방지 합리적인 첫 번째 단계입니다. 그러나는 오류가 발생 하는 경우 잘 작성 된 오류 메시지를 문제를 완화 하기 위한을 이동 수 있습니다. 오류 메시지는 아마도 가장 중요 한 유형의 알림 사용자에 게, 동기 되어 문제를 해결할 수 해야 하는 문제가 없으므로 하나입니다. 잘못 작성 된 오류 메시지는 사용자가 자신의 오류의 원인을 결정 및 가능한 해결 방법에 둡니다.

 주의 저하 또는 혼란 스러운 오류 메시지를 사용자에 게 가치를 더하는 쓰기만 필요한 메시지 발생 하므로 사용자가 중지 될 수 있습니다. 메시지는 단순히 알림, 대체 표시를 사용 합니다.

### <a name="rules-for-creating-an-error-message"></a>오류 메시지 만들기에 대 한 규칙

- 오류 메시지를 생성 하는 경우 대상 그룹에 대 한 적절 한 오류 수준을 선택 합니다. 해당 하는 경우 사용자 작업을 제공 하는 간단한 요약에 대 한 목표 걸릴 수 있습니다. 사용자는 알 필요가 있는 모든 상태 하지 않습니다.

- 건설적인 지원을 제공 합니다. 읽기 및 명령이 포함 된 오류 메시지를 수행 하는 것이 쉽습니다.

- 이중 부정을 사용 하지 마세요.

- 자동화를 수행 하 고 수동 문법 및 맞춤법 작성 오류 메시지를 확인 합니다.

- 복잡 한 오류 메시지에 대 한 순차적 통신을 방지 합니다. 오류 메시지에는 F1 후크를 사용 하지 않습니다. 메시지 자체에 충분 해야 합니다.

- 올바른 아이콘을 사용 합니다.

- 질문을 더 쉽게 이해 하 고 "삭제" 및 "취소"와 같은 옵션이 선택 취소 하는 단추를 사용 합니다.

- 경고에 대 한 됩니다 계속 따른 명확 하 게 합니다. 단추는 결과 나타냅니다.

- 오류에 대 한 사용자가 문제를 해결 하려면 수행할 수 있는 작업을 설명 합니다. 단추 작업 이거나 "닫기" 합니다. 예를 들어합니다 오류 메시지를 "확인" 단추를 사용 하지 마세요.

- 몇 가지 질문이 오류 메시지를 생성 하는 경우:

  - 사용자만이 오류를 사용 하 여 문제를 해결 하는 방법에 대해 알 수 있습니까?

  - 사용자는이 오류와 같은 어휘를 사용 하나요?

  - 이 오류 모호 하거나 여러 상황에서 공유? 그렇다면 어떻게 수행 하면 사용자에 대 한 가이드 필요한 솔루션?

#### <a name="build-errors"></a>빌드 오류
 Visual Studio 소프트웨어 개발 도구 이므로 해당 구성 요소 중 상당수에 컴파일, 변환 또는 인코딩 개발자의 작업이 이진 형식으로 변환 하는 단계입니다. 이러한 변환은 컴파일러는 잘못 작성 된 파일을 처리할 수 없는 경우 또는 컴파일러 옵션이 올바르게 설정 되지 않은 경우 오류가 발생할 수 있습니다.

 Visual Studio 사용자에 게 수많은 빌드 오류를 해결 하는 개발 시간을 투자할 수 있습니다. 이 해결 시간 오류 종속성 또는 때 오류 메시지가 잘못 작성 된, 오류의 출처를 어렵게 만들 수 있습니다 하는 경우에 증가 합니다.

 최상의 빌드 오류를 Visual Studio 첫 번째 위치를 의미 하기 때문에 발생 하지 않습니다 하는 자동 완성 기능을 제공 되며 IntelliSense 물결선입니다. 스키마 유효성 검사기와 유사한 도구를 같은 종류의 피드백을 제공합니다. 이러한 메커니즘에는 사전에 빌드 오류 가능성을 수행 하는 올바른 형식의 코드를 작성 하는 사용자를 가이드입니다.

 Visual Studio 도구 창 사용자 수 읽고 문서 창에 발생 한 오류를 통해 이동 하는 위치를 제공 합니다. 바로 가기 키를 신속 하 게 많은 양의 코드를 탐색 하 고 문제의 위치를 직접 이동할 수 있는 사용자 제공 됩니다. Visual Studio에는 각 빌드 오류가 사용자 오류에 관한 더 심층적인 정보를 제공 하는 도움말 항목으로 직접 이동할 수 있도록 특정 도움말 키워드/컨텍스트 ID에 연결 될 수 있습니다.

 명확 하 고 간결한 빌드 오류를 씁니다.

- **평이한 언어를 사용 하 여** 거의 또는 전혀 컴파일러 전문 용어를 사용 하 여 문제를 설명 하는 합니다. 빌드 오류의 텍스트는 과도 하 게 기술 되지 않습니다.

- **가능한 원인에 설명 합니다.** 예를 들어, "속성과 값 사이 콜론을 누락 된 ' (속성): (값)' 선언 합니다."

- 잠재적 수정 사항에 대 한 정보를 제공 합니다. 충분 한 공간이 없는 경우 해당 도움말 항목에 추가 세부 정보를 보류할 수 있지만.

### <a name="components-of-a-well-written-error-message"></a>잘 작성 된 오류 메시지의 구성 요소

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>오류 메시지에 대 한 셸 대화 서비스를 사용 합니다.
 셸 대화 서비스를 사용 하면 메시지 모양을 제어할 수 있습니다 — 특히에서 글꼴-개별 요소에 크게 변경 되지 않고 있습니다. 사용 된 **IErrorInfo** 메커니즘 하 고 보고를 사용 하 여 **IVsUIShell::SetErrorInfo/ReportErrorInfo**합니다.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>효과적이 고 적절 한 알림 표시를 선택 합니다.
 (동기 알림) 데이터 손실을 방지 하기 위한 즉각적인 동작이 필요 하는 경우에 중요 한 경고를 사용 하 여 모달 대화 상자를 사용 합니다. 중요 아이콘 부정적인 결과가 발생할 수 있습니다는 닫기 읽지도 않고 메시지의 경우에 예약 되어 있습니다. 데이터 손실은 경보 수준 응답을 요구 하는 중요 한 상황입니다. 중요 아이콘 남용 되지 않도록 desensitizes의 중요성에 대 한 사용자입니다. 오류 메시지가 특성 정보 인 경우 모달 대화 상자 (비동기 알림)에 대 한 대안을 고려 합니다.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>기술 설명 하는 대신 문제가 발생 하는 이유는 무엇에 대 한 정리 하 고 간결한 설명을 제공 합니다.
 설명에 기술 세부 정보를 사용 하 여 사용자가 부담을 줄 됩니다 있도록 가능성이 오류 메시지를 무시 합니다. 적절 한 메시징 예제:

- "요청된 된 파일을 열 수 없습니다."

- "인터넷에 연결할 수 없습니다."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>문제를 해결 하는 방법에 대 한 정보를 제공 합니다.
 문제를 해결 하는 방법의 사용자를 제안 합니다. 솔직히 사용자 경우 제안이 없습니다. 기술 지원 또는 커뮤니티 지원과 같은 다른 온라인 원본에 대 한 직접 링크를 제공 합니다. 사용자가 특정 문제와 관련 된 온라인 정보를 가리키도록 시도 합니다. 오류 ID에 대 한 스레드에 해당 특정 오류에 대 한 사용자를 연결 하는 것이 좋습니다. 적절 한 메시징 예제:

- "인터넷에 연결 되어이 작업을 다시 시도 하에 있는지 확인 합니다."

- "파일이 있고 열 수 있는 권한이 있는지 확인 합니다."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>단기 및 지점에 메시지를 작성 합니다.
 오류 메시지를 알릴 수 설명 되 및 솔루션을 제공 되지만 여전히 너무 장황한 경우 무시 됩니다. 하나의 솔루션 세부 정보 단추를 사용 하 여 점진적 표시를 사용 하는 것입니다. 예를 들어 짧은 설명/솔루션을 지정 하 고 세부 정보 단추 아래에서 자세한 정보를 배치 합니다. 사용자 오류에서 자세한 정보를 읽을 수를 선택 하는 경우 변경할 수 있습니다.

 메시지의 언어는 다음과 같아야 합니다.

- **도메인에 적합 한 합니다.** 사용자는 이해 하는 언어를 사용 합니다. 고객에 게 개발자 인 경우에 없는 경우가 많습니다 컨텍스트 및 용어 했습니다.

- **특정 합니다.** 모호한 단어를 방지 하 고 관련된 개체의 특정 이름 및 위치를 제공 합니다. 예를 들어, 오류 메시지를 "문자가 잘못 되었습니다."와 같이 유용 하지 않습니다. 문자? "파일을 찾을 수 없습니다." 파일?

- **유휴 합니다.** 사용자를 비난 하거나 어리석 하지 마십시오. 악의적인 또는 불쾌감을 주는 언어 방지 (중단, 실행, 심각한, 잘못 된 종료). 종종 shouting으로 간주 되 고으로 읽을 수 없는 대문자 텍스트를 방지 합니다. 유머를 사용 하지 마세요.

- **맞는.** 올바른 철자 및 문법 (알파)에 사용 합니다. 오타는 비 전문적으로 및 당혹 스러운입니다.

- **적절 한 컨텍스트.** 적절 한 단추 텍스트를 사용 합니다. "확인" 단추를 방지 하 고 "계속" 또는 "예/아니요."를 대신 사용

### <a name="error-message-examples"></a>오류 메시지 예제

|양호|잘못 된|
|----------|---------|
|"를 서비스에 번호로 전화를 걸 파일이 없습니다. 확인 수 및 다시 전화 접속 하거나 0 연산자에 대 한 전화 접속. "|-"오류 (449): "잘못 된 수<br />-"이 처리 되지 않은 예외가 오류 작업이 완료 되었음을 나타냅니다."<br /><br /> ![Visual Studio에서 잘못 된 오류 메시지](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "a_ErrorDialog 0602")|

## <a name="accessing-help"></a>도움말 액세스

### <a name="overview"></a>개요
 MSDN의 설명서 외에도 Visual Studio 사용자 UI에서 사용자를 지원 하기 위해 여러 액세스 지점을 갖습니다. 이러한 액세스 지점은 일관 되 게 사용할 수 있도록, 하려면 기능 팀 환경에서 제공 하는 도움말 시스템을 활용 하기 위해 필요 합니다. 이러한 액세스 지점은 다음과 같습니다.

- **대화 상자에서 지침 및 추가 텍스트입니다.** 방향 또는 화면 또는 InfoTip 아이콘 위로 마우스를 가져가고에서 사용할 수 있는 UI에 설명을 제공 하는 정적 텍스트입니다.

- **F1 도움말** (편집기에만 해당). Visual Studio 편집기에서 사용자는 언제 든 지 F1 키를 누르면 열립니다. 현재 선택 영역에 특정 도움말 항목을 신뢰할 수 있습니다. F1 키를 사용 하 여 연결 된 항목이 적절 하 고 정보를 제공 되는지 확인 합니다.

- **도움말 항목에 대 한 하이퍼링크입니다.** 대화 상자, 도구 창 또는 사용자는 데 도움이 되는 기술, 기능 또는 작업을 수행 하는 방법에 대 한 정보에 대 한 자세한 내용은 항목을 시작 하는 디자인 화면 내에서 하이퍼링크입니다.

- **스마트 태그 및 구성 대화 상자와 같은 도우미 UI 메커니즘** 이러한 메커니즘 사용자는 데 도움이 되는 UI 요소를 이해 하거나 스마트 태그 또는 작성기 대화 상자 등의 작업을 용이 하 게 합니다.

- **UI 도움말 단추** (사용 되지 않음). 관련 된 F1 도움말 항목에 대 한 액세스를 제공 하는 제목 표시줄에 표시기를 표시 합니다.

### <a name="text"></a>텍스트

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>대화 상자에서 지침 및 추가 텍스트
 복잡 한 작업을 지 원하는 대화 상자에서 대화 상자 또는 복잡 한 컨트롤 거의 맨 위에 있는 종종 ui에서 지침 텍스트를 제공 해야 할 수 있습니다. 참조 [UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 스타일 작성에 대 한 세부 정보에 대 한 합니다.

#### <a name="infotips"></a>InfoTips
 자주 사용 안내 텍스트 UI에서 준비에서 위치로 길어질 수 있습니다 또는 숙련 된 사용자에 게 혼란을 여겨질 새 사용자 에게만 유용할 수 있습니다. 이 경우 정보/사용 안내 텍스트 정보 팁에서 도구 설명으로 배치 되어야 합니다.

 정보 팁 눈에 띄는 아직 방해가 되지 않는 특정 정보 팁 아이콘을 사용 해야 관련 된 컨트롤은 거의 배치 되어야 합니다.

 ![Visual Studio에서 InfoTip](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")

 **Visual Studio의 정보 팁 예제**

### <a name="interactive-help-mechanisms"></a>대화형 도움말 메커니즘

#### <a name="f1-help"></a>F1 도움말
 F1 도움말을 제공 하는 것은 필요한 편집기 또는 디자인 화면 내에서 하지만 Visual Studio 환경에서 다른 곳에서 없습니다.

#### <a name="hyperlinks-to-help-topics"></a>도움말 항목에 대 한 하이퍼링크
 작업을 수행 하 고, IDE 내에서 탐색 또는 브라우저에서 도움말을 시작할 하이퍼링크를 사용할 수 있습니다. 참조 [UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 07.10.01 언어에 대 한 세부 정보에 대 한 단추 및 시각적 개체 및 레이아웃 지침에 대 한 하이퍼링크입니다.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>(사용 되지 않음) 대화 상자 제목 표시줄 단추 [?] 도움말
 대부분의 경우 대화 상자의 제목 표시줄의 [?] 도움말 단추가 사용 되지 않습니다. UI 항목은 더 이상이 문서 모델에 포함 하 고 따라서 없을 연결할 관련 항목. 기본적으로, 제목 표시줄 단추 F1 도움말와 동일한 작업을 했으며 대화 상자에서 필요한 더 이상. 일부 경우에이 여전히 사용할 수를 사용할 수 있는 절차 또는 개념에 대 한 자세한 내용은 표시기로 하이퍼링크 최신 UI에서 자주 사용 되는 있지만 합니다.

##### <a name="dialogs-created-through-the-environment"></a>생성 된 환경을 통해 대화 상자
 많은 셸 대화 상자를 통해 만들어진 합니다 **VBDialogBoxParam** 함수입니다. 이동 지원 하기 위해 업데이트 된이 공유 함수는 **도움말** 대화 상자에서 단추를 **?** 단추는 이전 버전과 아키텍처를 유지 하면서 호환 되 고 확장 가능 합니다.

 특히 합니다 **VBDialogBoxParam** 함수 ID가 인 단추에 대 한 대화 상자 템플릿을 살펴봅니다 **IDHELP** (9) 레이블 이거나 **도움말** 또는 **&도움말**. 숨겨져 도움말 단추가 있으면 및 **WS_EX_CONTEXTHELP** 스타일은 배치 하는 대화 상자에 추가 된 **?** 대화 상자의 제목 표시줄의 단추입니다.

 대화 상자 프로시저를 스택으로 푸시 대화 상자를 만들면 및 라는 사전 처리 대화 상자 프로시저를 사용 하 여 대화 상자를 호출 **DialogPreProc**합니다. 경우는 **?** 전송 단추를 **WM_SYSCOMMAND** 의 **SC_CONTEXTHELP** 대화 상자. 합니다 **DialogPreProc** 이 명령은 캡처 및 변경 하는 **WM_HELP** 원래 대화 프로시저에 전달 되는 메시지

 대부분의 환경 생성 대화 상자에 대화 상자는 도움말 단추가 있습니다. 대화 상자가 표시 되 면 도움말 단추 되며 자동으로 숨겨진만 **?** 단추가 작동 합니다. 경우는 **?** 적이 단추 제거 되었거나 Windows에서 변경 된 경우이 솔루션을 사용 하면 신속 하 게 원래 도움말 단추를 다시 이동할 수 있습니다.

 이 솔루션에 버그를 일으킬 수 있는 네 가지 가정을 합니다.

- 대화 상자의 도움말 단추 **IDHELP** (9).

- 도움말 단추 숨겨질 때 대화 상자를 올바르게 표시 합니다.

- 대화 상자는 winproc를 대체 하지 않아야 합니다.

- 대화 상자는 다른 대화 상자 내에서 포함 되지 않습니다.

  대화 상자 msenv 내에 상주 하 고 사용 하지 않는 경우 **VBDialogBoxParam**를 활용 하 여 조사 **VBDialogBoxParam** 고유한 처리기를 구현 하기 전에 합니다.

##### <a name="dialogs-created-through-other-packages"></a>다른 패키지를 통해 생성 대화 상자
 Msenv 외부에 있는 대화 상자에 대 한 사용자 고유의 솔루션을 구현할 수 있습니다. VSPackage의 공유 대화 상자 클래스에 대 한 제목 표시줄에 단추를 이동 하거나 각 대화 상자에서 처리기를 구현 하는 것이 좋습니다. 다음 코드는 시작할 수 있도록 하는 구현의 기본 구조:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>관리 코드에서 도움말 단추
 창 제목 표시줄 도움말 단추 기본 동작을 재정의 하는 것은 관리 코드에서 쉽습니다. 다음은이 동작을 보여 주는 전체 데모 응용 프로그램입니다. 폼의 재정의 해야 하는 기본적으로 **WndProc** 메서드와 F1 도움말 해제 한 다음 실행 될 때 요청을 **SC_CONTEXTHELP** 메시지를 가로채 합니다.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>관련 항목
 [글꼴 및 Visual Studio에 대 한 서식 지정](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md) [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md) [Visual Studio의 알림 및 진행률](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
