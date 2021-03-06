---
title: 변경 로그(Visual Studio Tools for Unity) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: f21a5491d1b0e23bff90ce0105b81eb6291ac7e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807195"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>변경 로그(Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio Tools for Unity에 대한 변경 로그입니다.

## <a name="23"></a>2.3
 릴리스됨 2016-07-14

### <a name="new-features"></a>새 기능

-   **일반:**

    -   Visual Studio의 오류 목록에서 Unity 콘솔 로그를 사용하지 않도록 설정하는 옵션이 추가되었습니다.

    -   생성된 프로젝트 속성을 수정할 수 있도록 허용하는 옵션이 추가되었습니다.

-   **디버거:**

    -   텍스트, XML, HTML 및 JSON 문자열 시각화 도우미가 추가되었습니다.

-   **마법사:**

    -   누락된 MonoBehavior가 추가되었습니다.

### <a name="bug-fixes"></a>버그 수정

-   **일반:**

    -   Visual Studio 설정 내부의 컨트롤이 표시되지 않도록 하는 ReSharper 충돌이 수정되었습니다.

    -   경우에 따라 디버깅을 막는 Xamarin 충돌이 수정되었습니다.

-   **디버거:**

    -   디버깅할 때 Visual Studio가 중단되는 문제가 해결되었습니다.

    -   Visual Studio 2015의 함수 중단점 관련 문제가 수정되었습니다.

    -   여러 식 계산 문제가 수정되었습니다.

## <a name="22"></a>2.2
 릴리스됨 2016-02-04

### <a name="new-features"></a>새 기능

-   **마법사:**

    -   **MonoBehavior 구현** 마법사에 스마트 검색이 추가되었습니다.

    -   마법사가 컨텍스트를 인식할 수 있게 되었습니다. 예를 들어 NetworkBehavior 메시지는 NetworkBehavior를 사용할 때만 사용할 수 있습니다.

    -   마법사에서 NetworkBehavior 메시지에 대한 지원이 추가되었습니다.

-   **UI:**

    -   MonoBehavior 메시지의 표시 여부를 구성하는 옵션이 추가되었습니다.

    -   Unity 프로젝트와 관련 없는 Visual Studio 속성 페이지가 제거되었습니다.

### <a name="bug-fixes"></a>버그 수정

-   **프로젝트 생성:**

    -   Unity 4.6에서 UnityEngine 및 UnityEditor에 대한 참조 문제가 해결되었습니다.

    -   Unity가 OSX에서 실행될 때 프로젝트 파일의 생성 문제가 해결되었습니다.

    -   hashmark(#) 문자를 포함하는 프로젝트 이름의 처리 문제가 해결되었습니다.

    -   생성된 프로젝트가 C# 4로 제한됩니다.

-   **디버거:**

    -   Unity coroutine 내에서 디버깅할 때 발생하는 식 평가 관련 문제가 해결되었습니다.

    -   디버깅할 때 Visual Studio가 중단되는 문제가 해결되었습니다.

-   **UI:**

    -   [Tabs Studio](https://tabsstudio.com/) Visual Studio 확장과의 비호환성 문제가 해결되었습니다.

-   **설치 프로그램:**

    -   HKLM 레지스트리 항목을 만들어 VSTU의 시스템 전체 설치(모든 사용자에 대한 설치)를 지원합니다.

    -   동일한 버전의 VSTU가 여러 다른 버전의 Visual Studio에 대해 설치될 때 나타나는 VSTU 제거 문제가 해결되었습니다. 예를 들어, VSTU **2015** 2.1.0.0 및 VSTU **2013** 2.1.0.0이 모두 설치된 경우가 여기에 해당합니다.

## <a name="21"></a>2.1
 릴리스됨 2015-09-08

### <a name="new-features"></a>새 기능

-   Unity 5.2 지원

### <a name="bug-fixes"></a>버그 수정

-   Unity < 4.2의 표시 메뉴 항목

-   Visual Studio에서 XML intellisense 파일을 잠근 경우 오류 메시지가 더 이상 표시되지 않습니다.

-   조건부 인수가 부울 값이 아닌 경우 <\<변경된 경우>> 조건부 중단점을 처리합니다.

-   Windows 스토어 앱용 UnityEngine 및 UnityEditor 어셈블리에 대한 참조를 수정했습니다.

-   디버거를 단계별로 실행할 때 발생하는 오류(단계별로 실행할 수 없음, 일반 예외)를 수정했습니다.

-   Visual Studio 2015의 적중 횟수 중단점을 수정했습니다.

## <a name="20"></a>2.0
 릴리스됨 2015-07-20

### <a name="bug-fixes"></a>버그 수정

-   **Unity 통합:**

    -   DLL과 해당 디버그 기호(PDB)를 가져올 때 Visual Studio 2015로 만든 디버그 기호의 변환을 수정했습니다.

    -   MDB 파일도 제공되는 경우를 제외하고 DLL 및 해당 디버그 기호(PDB)를 가져올 때 항상 MDB 파일을 생성합니다.

    -   Unity 프로젝트 디렉터리가 obj 디렉터리로 오염되는 문제를 수정했습니다.

    -   System.Xml.Link 및 System.Runtime.Serialization에 대한 참조 생성을 수정했습니다.

    -   프로젝트 파일 생성 API 후크에 대한 여러 구독자 지원이 추가되었습니다.

    -   생성할 파일 중 하나가 잠겨 있는 경우에도 항상 프로젝트 파일 생성을 완료합니다.

    -   C# 프로젝트에 포함할 파일을 지정할 때 확장 필터의 * 와일드카드에 대한 지원이 추가되었습니다.

-   **Visual Studio 통합**

    -   Productivity Power Tools와의 호환성 문제를 수정했습니다.

    -   이벤트 및 대리자 선언 기반의 MonoBehaviors 생성을 수정했습니다.

-   **디버거:**

    -   디버그할 때 잠재적인 중지를 수정했습니다.

    -   특정 스택 프레임에서 지역이 표시되지 않는 문제를 수정했습니다.

    -   빈 배열 검사를 수정했습니다.

## <a name="20-preview-2"></a>2.0 Preview 2
 릴리스됨 2015-04-02

### <a name="new-features"></a>새 기능

-   **Unity 프로젝트 탐색기:**

    -   Unity 프로젝트 탐색기에서 파일의 이름을 바꿀 때 클래스의 이름을 자동으로 바꿉니다( **옵션** 대화 상자 참조).

    -   Unity 프로젝트 탐색기에서 새로 만들어진 스크립트를 자동으로 선택합니다.

    -   Unity 프로젝트 탐색기에서 활성 스크립트를 추적합니다( **옵션** 대화 상자 참조).

    -   Visual Studio 솔루션 탐색기를 이중 동기화합니다( **옵션** 대화 상자 참조).

    -   Unity 프로젝트 탐색기에서 Visual Studio 아이콘을 채택합니다.

-   **디버거:**

    -   저장되거나 최근에 사용한 디버그 대상 목록에서 활성 디버그 대상을 선택합니다( **옵션** 대화 상자 참조).

    -   MonoBehavior 메서드에서 함수 중단점을 만들고 여러 MonoBehavior 클래스에 적용합니다.

    -   디버거에서 개체 ID 만들기를 지원합니다.

    -   디버거에서 중단점 적중 횟수를 지원합니다.

    -   디버거에서 예외 중단을 지원합니다(실험적. **옵션** 대화 상자 참조).

    -   디버거에서 식을 평가할 때 개체 및 배열 만들기를 지원합니다.

    -   디버거에서 식을 평가할 때 Null 비교를 지원합니다.

    -   디버거 조사식 창에서 사용되지 않는 멤버를 필터링합니다.

-   **설치 프로그램:**

    -   최적화된 Visual Studio Tools for Unity 확장 등록입니다.

    -   Unity 5에 대해 Visual Studio Tools for Unity 패키지를 설치합니다.

-   **설명서:** 문서 생성의 성능을 향상합니다.

-   **마법사:** Unity 4.6 및 Unity 5에 대한 새 MonoBehavior 메서드를 지원합니다.

-   **Unity:** 프로젝트 파일을 생성하는 동안 .rsp 파일에서 안전하지 않은 플래그 및 사용자 정의를 조회합니다.

-   **UI:** Visual Studio Tools for Unity **옵션** 대화 상자가 Visual Studio에 추가되었습니다.

### <a name="bug-fixes"></a>버그 수정

-   **Unity 프로젝트 탐색기:**

    -   Visual Studio 솔루션 탐색기에서 이름을 바꾸거나 파일을 이동한 후 Unity 프로젝트 탐색기를 새로 고칩니다.

    -   Unity 프로젝트 탐색기에서 파일의 이름을 바꿀 때 선택 항목을 유지합니다.

    -   Unity 프로젝트 탐색기에서 파일을 두 번 클릭할 때 자동 확장 및 축소를 방지합니다.

    -   새로 선택한 파일이 Unity 프로젝트 탐색기에 표시되는지 확인합니다.

-   **디버거:**

    -   디버거에서 식을 평가할 때 Visual Studio가 중지되지 않도록 방지합니다.

    -   메서드 호출이 디버거의 적절한 도메인에서 이루어지는지 확인합니다.

-   **Unity:**

    -   Unity 5가 있는 UnityVS.OpenFile의 위치를 수정합니다.

    -   Unity 5가 있는 pdb2mdb의 위치를 수정합니다.

    -   프로젝트 파일을 생성하는 동안 발생 가능한 예외를 방지합니다.

    -   OSX에서 Unity를 실행할 때 중지되지 않도록 방지합니다.

    -   내부 예외를 처리합니다.

    -   Unity 콘솔 로그를 VS 오류 목록에 보냅니다.

-   **설명서:** 새 Unity 설명서에 대한 문서 생성을 수정합니다.

-   **프로젝트:** 필요한 경우 폴더에서도 Unity.meta 파일을 이동하고 이름을 바꿉니다.

-   **마법사:** 코드를 생성할 때 MonoBehavior 메서드 매개 변수의 순서를 수정합니다.

-   **UI:** 상황에 맞는 메뉴 및 아이콘에 대한 Visual Studio 테마를 지원합니다.

## <a name="20-preview"></a>2.0 Preview
 릴리스됨 2014-11-12

### <a name="new-features"></a>새 기능

-   Visual Studio 2015가 지원됩니다.

-   Visual Studio 2015에서 Unity 셰이더에 대한 코드 색을 지정합니다.

-   디버깅할 때 값의 시각화가 향상되었습니다.

    -   ArrayLists, 목록, 해시 테이블 및 사전에 대한 시각화가 향상되었습니다.

    -   조사식 및 로컬 뷰에서 public이 아닌 멤버 및 정적 멤버를 범주로 표시합니다.

    -   Unity의 SerializedProperty가 향상되어 해당 속성에 유효한 값 필드만 평가합니다.

    -   클래스 및 구조체에 대한 DebuggerDisplayAttribute를 지원합니다.

    -   DebuggerTypeProxyAttribute를 지원합니다.

-   마법사를 사용하여 사용자 코딩 규칙을 준수하도록 MonoBehaviour 메서드의 삽입을 확인합니다.

-   UnityVS에서 생성된 프로젝트에서 컴파일 시간 텍스트 템플릿에 대한 지원을 구현합니다.

-   UnityVS에서 생성된 프로젝트에서 ResX 리소스에 대한 지원을 구현합니다.

-   Unity의 Visual Studio에서 열기 셰이더를 지원합니다.

### <a name="bug-fixes"></a>버그 수정

-   연결 및 재생이 Visual Studio에서 트리거된 후 Unity에서 게임을 시작하기 전에 소켓을 정리합니다. 연결 및 재생을 사용할 때 Unity와 VS 간 연결 안정성과 관련된 일부 문제가 해결됩니다.

-   Unity를 중지 상태로 만들기 쉬운 Unity의 스크립팅 엔진 디버거 인터페이스에서 메서드 호출을 피합니다. 디버거를 연결할 때 Unity가 중지되는 문제가 해결됩니다.

-   사용할 수 있는 기호가 없을 때의 호출 스택 표시 문제를 수정합니다.

-   필요 없는 경우 로그 콜백을 등록하지 않습니다.

## <a name="192"></a>1.9.2
 릴리스됨 2014-10-09

### <a name="new-features"></a>새 기능

-   Unity 플레이어의 검색을 향상합니다.

-   파일 열기를 사용할 때 Unity에서 파일 이름과 더불어 줄 번호를 통과하도록 합니다.

-   로컬 문서가 없는 경우 온라인 Unity 설명서를 기본값으로 설정합니다.

### <a name="bug-fixes"></a>버그 수정

-   도메인을 다시 로드한 후 중단점을 적중하는 경우 발생하는 잠재적인 Unity 충돌 문제를 수정합니다.

-   도메인을 다시 로드한 후 구성 또는 정보 창을 닫을 때 Unity 콘솔에 표시되는 예외 문제를 수정합니다.

-   로컬로 실행되는 64비트 Unity의 검색 문제를 수정합니다.

-   마법사에서 Unity 버전 당 MonoBehaviours의 필터링 문제를 수정합니다.

-   확장 필터가 비어 있을 때 프로젝트 파일에 모든 자산이 포함되는 버그를 수정합니다.

## <a name="191"></a>1.9.1
 릴리스됨 2014-09-22

### <a name="new-features"></a>새 기능

-   원본 위치로 바인딩 중단점을 최적화합니다.

-   디버거의 식 평가에서 오버로드된 메서드를 지원합니다.

-   디버거의 식 평가에서 boxing 기본 형식 및 값 형식을 지원합니다.

-   무명 메서드를 디버그하는 경우 C# 환경 로컬 변수 다시 만들기를 지원합니다.

-   Visual Studio에서 파일을 삭제하거나 이름을 바꾸는 경우 .meta 파일을 삭제하고 이름을 바꿉니다.

### <a name="bug-fixes"></a>버그 수정

-   Visual Studio 테마 처리 문제를 수정합니다. 이전에는 검은색 테마의 대화 상자가 비어 있는 것처럼 표시될 수 있었습니다.

-   Unity를 다시 컴파일하는 동안 디버거를 연결하는 경우 Unity 중지를 수정합니다.

-   다른 시스템에서 컴파일된 원격 편집기 또는 플레이어를 디버그하는 경우의 중단점 문제를 수정합니다.

-   중단점에 적중할 때 발생할 수 있는 Visual Studio 충돌 문제를 수정합니다.

-   중단점을 언로드됨으로 표시하지 않기 위해 중단점 바인딩을 수정합니다.

-   범위 밖에 표시되는 라이브 변수를 방지하기 위해 디버거에서의 변수 범위 처리를 수정합니다.

-   디버거의 식 계산에서 정적 멤버 조회 문제를 수정합니다.

-   정적 필드 및 속성을 표시하기 위해 디버거의 식 계산에서 유형 표시를 수정합니다.

-   Unity 프로젝트 이름에 Visual Studio가 금지하는 특수 문자가 포함되는 경우(연결 문제 #948666)의 솔루션 생성 문제를 수정합니다.

-   옵션을 선택하지 않은 후 콘솔 이벤트 전달을 즉시 중지하기 위해(연결 문제 #933357) Visual Studio Tools Unity 패키지를 수정합니다.

-   UnityVS에서 생성한 프로젝트에서 UnityEngine.UI 등의 새 API에 대한 참조를 올바르게 다시 생성하기 위해 참조의 검색을 수정합니다.

-   손상된 설치를 방지하기 위해 설치하기 전에 Visual Studio를 닫도록 설치 프로그램을 수정합니다.

-   VSTU의 모든 버전 간에 공유된 적절한 독립 실행형 구성 요소로 Unity 참조 어셈블리를 설치하기 위해 설치 프로그램을 수정합니다.

-   Unity의 64비트 버전에서 VSTU로 개방 스크립트 문제를 수정합니다.

## <a name="19"></a>1.9
 릴리스됨 2014-07-29

### <a name="new-features"></a>새 기능

-   Unity 디버거 연결 창에서 디버그할 사용자 지정 IP 및 포트를 입력하는 기능을 추가합니다.

-   구성 옵션을 추가하여 Unity의 백그라운드에서 실행 여부를 설정합니다.

-   솔루션 및 프로젝트 파일 또는 프로젝트 파일만 생성하는 구성 옵션을 추가하여

-   시작 대상: Unity에 연결 또는 Unity에 연결 및 재생하도록 선택합니다.

-   디버거에서 다차원 배열을 표시합니다.

-   포트를 디버그하는 새 Unity 플레이어를 처리합니다.

-   Unity의 4.6 GUI 어셈블리와 같은 새로운 Unity 어셈블리에 대한 참조를 처리합니다.

-   디버그하는 경우 지역 변수를 올바르게 표시하기 위해 클로저를 해체합니다.

-   디버그하는 경우 생성된 반복기 변수를 인수에 해체합니다.

-   프로젝트를 다시 로드한 후 Unity 프로젝트 탐색기의 상태를 유지합니다.

-   Unity 프로젝트 탐색기를 현재 문서와 동기화하는 명령을 추가합니다.

### <a name="bug-fixes"></a>버그 수정

-   디버거를 시작하기 전의 해당 조건이 설정된 조건부 중단점 문제를 수정합니다.

-   경고를 방지하기 위해 UnityEngine에 대한 참조를 수정합니다.

-   Unity 베타에 대한 구문 분석 버전 문제를 수정합니다.

-   중단점 또는 단계별 적중 시 로컬 변수 창에 변수가 나타나지 않는 문제를 수정합니다.

-   Visual Studio 2013의 변수 도구 설명 문제를 수정합니다.

-   Unity 4.5에 대한 IntelliSense 설명서의 생성 문제를 수정합니다.

-   도메인을 다시 로드한 후(Unity에서 재생/중지)의 Unity/Visual Studio 통신 문제를 수정합니다.

-   Visual Studio 테마 부분에 대한 처리 문제를 수정합니다.

> [!IMPORTANT]
>  Unity 에코시스템에서 널리 사용되는 C# 언어 - 새로운 샘플 자산은 C#으로 되어 있으며 Unity 설명서는 C#이 기본값으로 설정됩니다. C# 환경에 초점을 맞추기 위해 UnityScript 및 Boo에 대한 기본 지원을 제거했습니다. 결과적으로 VSTU 솔루션은 이제 C# 전용이며 훨씬 빠르게 로드됩니다.

## <a name="182"></a>1.8.2
 릴리스됨 2014-01-07

### <a name="new-features"></a>새 기능

-   편집기의 원격 검색을 위해 Mavericks에서 Unity의 스크립팅 엔진 네트워크 계층에 있는 문제를 해결합니다.

-   원격 Unity 플레이어를 검색하는 새 포트를 처리합니다.

-   현재 빌드 대상을 특정으로 하는 UnityEngine 어셈블리를 참조하세요.

-   생성된 프로젝트에 포함할 파일을 필터링하는 설정을 추가합니다.

-   Visual Studio 오류 목록에 콘솔 로그를 보내지 않도록 하는 설정을 추가합니다. Unity에서 콘솔 로그를 받기 위해 등록된 콜백이 하나만 있을 수 있으므로 PlayMaker 또는 콘솔 프로를 사용하는 경우 유용합니다.

-   mdb 디버그 기호를 생성하지 않는 설정을 추가합니다. 이는 mdb를 직접 생성하는 경우 유용합니다.

### <a name="bug-fixes"></a>버그 수정

-   VS를 통해 Unity >= 4.2로부터 연 파일에서 IntelliSense가 손실될 때의 재발 문제를 수정합니다.

-   사용자 지정 테마를 처리하는 VS 대화 상자 문제를 수정합니다.

-   UPE의 상황에 맞는 메뉴 닫기 문제를 수정합니다.

-   동기화되지 않은 경우 버전 특정 어셈블리를 생성할 때 Unity의 충돌을 방지합니다.

## <a name="181"></a>1.8.1
 릴리스됨 2013-11-21

### <a name="new-features"></a>새 기능

-   Unity 4.3 API와 함께 MonoBehaviour 마법사가 조정되었습니다.

-   사용하는 버전에 따라 MonoBehaviour 마법사에서 Unity API를 필터링합니다.

-   Unity > 4.1에 대한 프로젝트에 System.Xml.Linq에 대한 참조를 추가합니다.

-   메시지에 stacktrace의 시작 부분을 포함하지 않도록 Debug.Log에 대한 호출을 꾸밉니다.

### <a name="bug-fixes"></a>버그 수정

-   Visual Studio에서 JavaScript 파일의 기본 처리를 방해하는 버그를 수정했습니다.

-   VS에 나타나는 흰색 픽셀 문제를 확실히 수정했습니다.

-   SCM에서 읽기 전용으로 표시한 경우 UnityVS.VersionSpecific 어셈블리가 삭제되는 문제를 수정했습니다.

-   UnityVS 패키지에서 소켓을 만들 때의 예외 문제를 수정했습니다.

-   Visual Studio 어셈블리에서 스톡 이미지를 로드할 때 Visual Studio에서 충돌이 발생하는 문제를 수정했습니다.

-   Unity 소스 빌드에 대한 UnityVS.VersionSpecific 생성에서의 버그를 수정했습니다.

-   Unity 패키지에서 소켓을 열 때 발생할 수 있는 중지 문제를 수정했습니다.

-   이름에 대시(-)가 있는 Unity 프로젝트의 처리 문제를 수정했습니다.

-   Unity에서 스크립트를 열 때 Unity 4.2 이상의 ALT+TAB 순서를 혼동하지 않도록 수정했습니다.

## <a name="180"></a>1.8.0
 릴리스됨 2013-09-24

### <a name="new-features"></a>새 기능

-   디버거 연결 속도가 크게 향상되었습니다.

-   Unity 4.2 이상에서 파일과 줄에 대한 탐색을 자동으로 처리합니다.

-   조건부 중단점입니다.

-   프로젝트 파일 생성기는 이제 T4 템플릿을 처리합니다.

-   새 API와 함께 MonBehavior 마법사를 업데이트합니다.

-   Unity 형식에 대한 C#의 Intellisense 설명서입니다.

-   산술 및 논리 식 계산입니다.

-   원격 디버깅 미리 보기에 대한 원격 편집기를 보다 효율적으로 검색합니다.

### <a name="bug-fixes"></a>버그 수정

-   디버거의 연결을 해제한 후 VS에서 스레드가 누수되는 버그를 수정했습니다.

-   VS에 나타나는 흰색 픽셀 문제를 수정했습니다.

-   상태 표시줄 아이콘에서 클릭 처리 문제를 수정했습니다.

-   플러그 인 폴더에서의 어셈블리를 사용한 참조의 생성 문제를 수정했습니다.

-   예외 발생 시의 UnityVS 패키지에서 소켓 만들기 문제를 수정했습니다.

-   UnityVS의 새 버전 검색 문제를 수정했습니다.

-   라이선스가 만료되었을 때의 라이선스 관리자 프롬프트 문제를 수정했습니다.

-   VS의 프로세스에 디버거 연결 창에서 프로세스 목록을 빈 상태로 만들 수 있는 버그를 수정했습니다.

-   로컬 뷰에서 변동되는 부울 값 문제를 수정했습니다.

## <a name="122"></a>1.2.2
 릴리스됨 2013-07-09

### <a name="bug-fixes"></a>버그 수정

-   식 계산기에서 정규화된 이름을 처리합니다.

-   Unity 스크립팅 엔진에서 잘못된 stackframe 데이터를 보내는 예외 처리와 관련된 중지 문제를 수정했습니다.

-   웹 대상에 대한 빌드 프로세스 문제를 수정했습니다.

-   Visual Studio를 시작할 때 열 파일 목록에 삭제된 파일이 표시되는 오류를 수정했습니다.

-   컴파일된 셰이더 등 스크립트가 아닌 파일을 처리하도록 UnityVS.OpenFile을 수정했습니다.

-   이제 모든 C# 프로젝트에서 Boo.Lang 및 UnityScript.Lang을 참조합니다.

-   프로젝트에 특수 문자가 있는 경우의 프로젝트에서 참조가 생성되는 문제를 수정했습니다.

-   삭제된 프로젝트에 대한 메서드 호출이 여러 NullReferenceException MessageBox를 트리거하는 VS 문제를 해결합니다.

-   Unity 4.2 베타 어셈블리의 처리 문제를 수정했습니다.

## <a name="121"></a>1.2.1
 릴리스됨 2013-04-09

### <a name="bug-fixes"></a>버그 수정

-   IO 오류 발생 시 코드 완성 기능에 대한 Unity 어셈블리의 로컬 배포 문제를 수정했습니다(예: 읽기 전용 파일 또는 Visual Studio에서 잠긴 파일).

-   Unity에서 스크립트를 열 때 Visual Studio에서 이미 열려 있는 경우 파일에 포커스를 두지 않는 재발 문제를 수정했습니다.

-   새 예외 처리의 성능 문제를 수정했습니다.

-   일부 외부 DLL에서 중단점의 바인딩 문제를 수정했습니다.

## <a name="12"></a>1.2
 릴리스됨 2013-03-25

### <a name="new-features"></a>새 기능

-   디버거 연결 속도가 크게 향상되었습니다.

-   대규모 프로젝트에 대한 Unity 프로젝트 탐색기가 최적화되었습니다.

-   처리된 예외와 처리되지 않은 예외에서 중단되거나 중단되지 않도록 Visual Studio 설정을 부여합니다.

-   로컬 변수에서 ToString을 호출하도록 Visual Studio 설정을 부여합니다.

-   Unity 플레이어를 디버그하는 데 사용할 수 있는 새 메뉴 디버그 -> Unity 디버거 연결을 추가합니다.

-   솔루션 파일 생성 시 UnityVS 솔루션에 추가한 사용자 지정 프로젝트를 유지합니다.

-   캐럿 위치에서 Unity 기능 또는 멤버에 대한 Unity 설명서를 표시하려면 새 바로 가기 키 CTRL+ALT+M -> CTRL+H를 추가합니다.

-   Visual Studio에서 컴파일하는 경우 컴파일러 응답 파일(rsp)을 고려합니다.

-   생성기 메서드를 디버그하는 경우 변수를 표시하도록 컴파일러에서 생성한 형식을 해체합니다.

-   공유 폴더를 Unity로 구성해야 하는 필요성을 제거하여 원격 디버깅을 간소화합니다. 이제 Windows에서 Unity 프로젝트에 액세스하기만 하면 됩니다.

-   사용자 지정 Unity 프로필을 표준 .net 대상 프로필로 설치합니다. ReSharper가 나타낼 수 있는 모든 가양성을 수정합니다.

-   디버거에서 제대로 등록하지 않은 스레드를 중단하지 않도록 Unity 스크립팅 엔진 버그를 해결합니다.

-   파일 열기 요청에서 충돌이 발생하는 동안 파일을 열 수 있는 것으로 표시하는 VS에서의 경쟁 조건을 방지하기 위해 파일 열기를 다시 작업합니다.

-   UnityVS는 이제 VS에서 파일을 저장할 때가 아니라 프로젝트를 빌드할 때 빌드를 새로 고치도록 요청합니다.

### <a name="bug-fixes"></a>버그 수정

-   사용자 지정 .net 프로필을 수정했습니다.

-   테마 설정 통합을 수정했습니다. VS 2012 어두운 테마와 관련된 문제를 수정합니다.

-   VS 2012에서 빠른 동작 바로 가기 문제를 수정했습니다.

-   디버그할 때 주 스레드가 중단점을 적중하는 경우 발생할 수 있는 단계별 실행 문제를 수정했습니다.

-   정수 등의 형식 별칭의 UnityScript 및 Boo 완료 문제를 수정했습니다.

-   새 UnityScript 또는 Boo 문자열을 작성할 때 예외 문제를 수정했습니다.

-   솔루션을 로드하지 않은 경우 Unity 메뉴에서의 예외 문제를 수정했습니다.

-   버그 UVS-48 수정: 큰따옴표를 입력하면 오류가 발생하고 모든 기능(코드 완성, 구문 강조 등)이 중단되는 문제.

-   버그 UVS-46 수정: Visual Studio의 오류 목록을 클릭할 때 열린 스크립트 파일(UnityScript) 중복 문제

-   버그 UVS-42 수정: VS 2012에서 상태 표시줄의 Unity 연결 로고가 마우스 이벤트를 처리하지 않는 문제

-   버그 UVS-44 수정: VS 2012에서 빠른 MonoBehaviour에 대해 CTRL+SHIFT+Q를 사용할 수 없는 문제

-   버그 UVS-40 수정: 창이 VS2012의 “어두운" 테마에서 비활성화된 경우 Unity 프로젝트 탐색기에서 선택한 항목을 읽지 못하는 문제

-   버그 UVS-39 수정: 이스케이프된 문자열 토큰화 문제

-   버그 UVS-35 수정: 변수를 검사할 때 개체에 대한 ToString 호출 문제

-   버그 UVS-27 수정: VS2012에서 "어두운" 테마와 Goto 기호 창 불일치 문제

-   버그 UVS-11 수정: 코루틴의 로컬 문제

## <a name="11--beta-release"></a>1.1 - 베타 릴리스
 릴리스됨 2014-10-09

## <a name="1013"></a>1.0.13
 릴리스됨 2013-01-21

### <a name="bug-fixes"></a>버그 수정

-   대상 디버기에서 잘못된 스레드 이벤트를 보내는 경우 발생할 수 있는 Visual Studio 잠금 문제를 수정했습니다. 일반적으로 OSX에서 원격 Unity를 디버그하는 경우 발생합니다.

-   예외가 디버거를 종료하는 경우 발생할 수 있는 Visual Studio 잠금 문제를 수정했습니다.

-   C# MonoBehavior가 네임스페이스에 있을 때의 MonoBehavior 도우미 문제를 수정했습니다.

-   Visual Studio 2012에서 UnityScript에 대한 디버거 도구 설명 문제를 수정했습니다.

-   Unity에서 디버그 상수만 변경되는 경우의 프로젝트 생성 문제를 수정했습니다.

-   Unity 프로젝트 탐색기에서의 키보드 탐색 문제를 수정했습니다.

-   이스케이프된 문자열에 대한 UnityScript 색 지정 문제를 수정했습니다.

-   Unity 외부에서 사용한 경우 프로젝트 이름을 보다 잘 추측할 수 있도록 파일 열기를 수정했습니다. 사용자가 UnityVS에 위임하는 Unity의 타사 파일 열기를 사용하는 경우 필요합니다.

-   Unity에서 UnityVS로 전송한 긴 메시지의 처리 문제를 수정했습니다. 이전에 긴 메시지는 UnityVS의 메시징 부분과 충돌할 수 있었습니다. 결과적으로 UnityVS가 Unity에서 파일을 열지 않는 경우가 있었습니다.

## <a name="1012"></a>1.0.12
 릴리스됨 2013-01-03

### <a name="bug-fixes"></a>버그 수정

-   Visual Studio에서 중단점을 삭제하는 경우 발생할 수 있는 Visual Studio 잠금 문제를 수정했습니다.

-   Unity가 게임 스크립트를 다시 컴파일한 후 일부 중단점이 적중되지 않는 버그를 수정했습니다.

-   중단점이 바인딩되지 않았을 때 Visual Studio에 올바르게 알리도록 디버거를 수정했습니다.

-   Visual Studio 디버거에서 기본 프로그램을 디버그하지 못하도록 할 수 있는 등록 문제를 수정했습니다.

-   UnityScript 및 Boo 식을 계산할 때 발생할 수 있는 예외 문제를 수정했습니다.

-   프로젝트 파일의 업데이트를 트리거하지 않는 Unity에서 .net API 수준을 변경하는 재발 문제를 수정했습니다.

-   사용자 코드가 로그 콜백 처리기에 관여할 수 없는 API 결함을 수정했습니다.

## <a name="1011"></a>1.0.11
 릴리스됨 2012-11-28

### <a name="new-features"></a>새 기능

-   Unity 4를 공식 지원합니다.

-   Unity 프로젝트 탐색기에서 스크립트를 조작할 수 있습니다.

-   Visual Studio의 탐색을 창에 통합합니다.

-   정보 콘솔 메시지를 구문 분석하여 오류 목록 클릭 시 기호로 된 첫 번째 stackframe으로 안내합니다.

-   [API](../cross-platform/customize-project-files-created-by-vstu.md) 를 추가하여 사용자가 프로젝트 생성에 참여할 수 있도록 합니다.

-   [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) 를 추가하여 사용자가 LogCallback에 참여할 수 있도록 합니다.

### <a name="bug-fixes"></a>버그 수정

-   Visual Studio 2012에서 Unity 프로젝트 탐색기의 백그라운드에 있는 재발 문제를 수정했습니다.

-   전체 .net 프로필의 사용자에 대한 프로젝트 생성 문제를 수정했습니다.

-   웹 대상의 사용자에 대한 프로젝트 생성 문제를 수정했습니다.

-   Unity에서처럼 DEBUG 및 TRACE 컴파일 기호를 포함하도록 프로젝트 생성을 수정했습니다.

-   Goto 기호 창에서 특수 문자를 사용하는 경우의 충돌 문제를 수정했습니다.

-   Visual Studio의 상태 표시줄에서 아이콘을 넣을 수 없는 경우의 충돌 문제를 수정했습니다.

## <a name="1010"></a>1.0.10
 릴리스됨 2012-10-09

### <a name="bug-fixes"></a>버그 수정

-   Visual Studio 2010에서 Unity 프로젝트 탐색기의 배경 문제를 수정했습니다.

-   UnityVS에서 이전에 디버거 인터페이스가 충돌한 Unity에 디버거를 연결 시도한 경우 발생할 수 있는 Visual Studio 중지 문제를 수정했습니다.

-   중단점이 설정되고 AppDomain 다시 로드가 발생하는 경우의 Visual Studio 중지 문제를 수정했습니다.

-   파일 잠금이나 Unity 빌드 프로세스 혼동이 발생하지 않도록 Unity에서 어셈블리를 검색하는 방법을 수정했습니다.

## <a name="109"></a>1.0.9
 릴리스됨 2012-10-03

### <a name="bug-fixes"></a>버그 수정

-   Unity 프로젝트에 실제 JavaScript 자산이 포함되는 경우의 프로젝트 생성 문제를 수정했습니다.

-   식 계산에서의 오류 처리 문제를 수정했습니다.

-   값 형식의 필드에 새 값을 설정할 때의 문제를 수정했습니다.

-   코드 편집기에서 식을 마우스로 가리킬 때 가능한 부작용을 수정했습니다.

-   식 계산에 대해 로드된 어셈블리에서 형식을 검색하는 방법을 수정했습니다.

-   버그 UVS-21 수정: Unity 개체에서의 할당 계산이 영향을 미치지 않는 문제

-   버그 UVS-21 수정: Unity Math API에 대한 메서드 호출을 계산할 때의 잘못된 포인터 문제

## <a name="108"></a>1.0.8
 릴리스됨 2012-09-26

### <a name="bug-fixes"></a>버그 수정

-   스크립트 열기에서 Visual Studio와 스크립트를 모두 열 수 있도록 프로젝트의 경로를 얻는 방법을 수정했습니다.

-   디버깅 세션이 실행할 때 만들어진 중단점이 Visual Studio를 잠글 수 있는 버그를 수정했습니다.

-   UnityVS를 Visual Studio 2010에 등록하는 방법을 수정했습니다.

## <a name="107"></a>1.0.7
 릴리스됨 2012-09-14

### <a name="new-features"></a>새 기능

-   Visual Studio 2012를 지원합니다.

### <a name="bug-fixes"></a>버그 수정

-   Unity의 동작에 맞도록 편집기 및 플러그 인 프로젝트 파일의 생성 문제를 수정했습니다.

-   Unity 4에서 .pdb 기호의 변환 문제를 수정했습니다.

> [!IMPORTANT]
>  Visual Studio 2012 지원으로 인해 일부 파일의 이름을 바꾸고 다른 위치로 이동했습니다. Unity를 가져오기 위한 UnityVS 패키지는 이제 Visual Studio 2010 및 Visual Studio 2012에 대해 각각 UnityVS 2010 또는 UnityVS 2012로 명명되었습니다. 이 버전에서는 UnityVS 프로젝트 파일을 다시 생성해야 합니다.

## <a name="106---internal-build"></a>1.0.6 - 내부 빌드
 릴리스됨 2012-09-12

## <a name="105"></a>1.0.5
 릴리스됨 2012-09-10

### <a name="bug-fixes"></a>버그 수정

-   스크립트 또는 셰이더에 잘못된 xml 문자가 있을 때 프로젝트 파일의 생성 문제를 수정했습니다.

-   Unity를 자산 서버에 연결했을 때 Unity 인스턴스 검색 문제를 수정했습니다. 이 버그로 인해 Unity에서 파일을 열지 못하고 Visual Studio 디버거에 자동으로 연결하지 못했습니다.

## <a name="104"></a>1.0.4
 릴리스됨 2012-09-05

### <a name="new-features"></a>새 기능

-   Unity에서 디버그 기호가 자동으로 변환됩니다.

     자산 폴더에 .NET .dll 어셈블리와 관련된.pdb가 있는 경우 어셈블리를 다시 가져오면 UnityVS에서 .pdb를 Unity의 스크립팅 엔진이 인식하는 디버그 기호 파일로 변환하며 UnityVS에서 .NET 어셈블리로 단계를 실행할 수 있습니다.

### <a name="bug-fixes"></a>버그 수정

-   Unity 내에서 메서드 또는 속성이 발생시킨 예외로 인한 디버그 도중 UnityVS가 충돌하는 문제를 수정했습니다.

## <a name="103"></a>1.0.3
 릴리스됨 2012-09-04

### <a name="new-features"></a>새 기능

-   Unity에서 파일을 열기 위해 UnityVS의 사용을 비활성화하는 새 구성 옵션입니다.

### <a name="bug-fixes"></a>버그 수정

-   비 편집기 프로젝트의 UnityEditor에 대한 참조 생성 문제를 수정했습니다.

-   비 편집기 프로젝트에 대한 UNITY_EDITOR 기호의 정의 문제를 수정했습니다.

-   사용자 지정 상태 표시줄로 인한 임의 VS 충돌 문제를 수정했습니다.

## <a name="102"></a>1.0.2
 릴리스됨 2012-08-30

### <a name="bug-fixes"></a>버그 수정

-   PythonTools 디버거와의 충돌 문제를 수정했습니다.

-   Mono.Cecil에 대한 참조 문제를 수정했습니다.

-   Unity 4 b7이 포함된 Unity에서 스크립팅 어셈블리를 검색하는 방법에 대한 버그를 수정했습니다.

## <a name="101"></a>1.0.1
 릴리스됨 2012-08-28

### <a name="new-features"></a>새 기능

-   Unity 4.0 베타에 대한 미리 보기를 지원합니다.

### <a name="bug-fixes"></a>버그 수정

-   예외가 발생되는 속성의 검사 문제를 수정했습니다.

-   개체를 검사하는 경우 기준 개체로 내림차순되는 문제를 수정했습니다.

-   MonoBehavior 마법사의 삽입 지점에 대한 빈 드롭다운 목록을 수정했습니다.

-   UnityScript 및 Boo의 자산 폴더 내부 dll에 대한 완료를 수정했습니다.

## <a name="10--initial-release"></a>1.0 - 초기 버전
 릴리스됨 2012-08-22

