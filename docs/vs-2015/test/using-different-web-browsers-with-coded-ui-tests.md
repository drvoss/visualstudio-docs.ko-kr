---
title: 코딩된 UI 테스트에 다른 웹 브라우저 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3854f4844fba3b3c1a0a519f06d59d31c4f7072
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445887"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>코딩된 UI 테스트에 다른 웹 브라우저 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코딩된 UI 테스트는 Internet Explorer로 테스트를 기록하여 웹 애플리케이션 테스트를 자동화합니다. 그런 다음 이러한 웹 애플리케이션에 대해 Internet Explorer 또는 기타 브라우저를 사용하여 테스트를 사용자 지정하고 재생할 수 있습니다.  
  
 **요구 사항**  
  
- Visual Studio Enterprise  
  
- 운영 체제  
  
  - Microsoft Windows 7  
  
  - Microsoft Windows 8  
  
  - Microsoft Windows Server 2008 R2 SP1  
  
- 웹 브라우저 버전:  
  
  - Windows Internet Explorer 9  
  
  - Windows Internet Explorer 10  
  
  - Mozilla Firefox 및 Google Chrome의 지원되는 버전을 확인하려면 [여기](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)로 이동하세요.  
  
- [코딩된 UI 다중 브라우저용 Selenium 구성 요소](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)를 설치합니다.  
  
  **모든 웹 브라우저에 어떤 기능이 지원됩니까?**  
  
- 속성, 검색, 재생 대기자 등 [기능 제어를 위한 사용자 지정 코드를 추가](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx)합니다.  
  
- 팝업 및 대화 상자  
  
- [반환 형식이 없는 기본 JavaScript 실행](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
- 검색 복원력(스마트 매치 사용) 및 [성능 향상](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>여러 웹 브라우저 형식에 코딩된 UI 테스트를 사용해야 하는 이유는 무엇입니까?  
 다양한 웹 브라우저 종류로 웹 애플리케이션을 테스트하면 다양한 브라우저를 실행하는 사용자의 UI 환경을 더 잘 에뮬레이션할 수 있습니다. 예를 들어, 애플리케이션에 다른 웹 브라우저와 호환되지 않는 Internet Explorer의 컨트롤 또는 코드를 포함할 수 있습니다. 다른 브라우저에서 코딩된 UI 테스트를 실행하면 고객에게 영향을 미치기 전에 문제를 발견하고 수정할 수 있습니다.  
  
## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>지원되는 웹 브라우저를 사용하여 웹 애플리케이션에서 코딩된 UI 테스트를 기록 및 재생하는 방법  
 **기록:** Internet Explorer를 사용하여 웹 애플리케이션 테스트를 기록하려면 코딩된 UI 테스트 빌더를 사용해야 합니다. 코딩된 UI 테스트와 같은 방식으로, 미리 정의된 집합을 사용하여 테스트된 컨트롤에 대해 유효성 검사 및 사용자 지정 코드를 추가할 수 있습니다(선택 사항). 자세한 내용은 [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)를 참조하세요.  
  
> [!NOTE]
> Google Chrome 또는 Mozilla Firefox 브라우저로는 코딩된 UI 테스트를 기록할 수 없습니다.  
  
 **Internet Explorer로 재생:** 브라우저를 명시적으로 지정하지 않은 경우 기본적으로 Internet Explorer에서 테스트가 실행됩니다. 테스트 코드에서 **BrowserWindow.CurrentBrowser** 속성을 설정하여 사용할 브라우저를 명시적으로 설정할 수 있습니다. Internet Explorer의 경우 이 속성을 **IE** 또는 **Internet Explorer**로 설정해야 합니다.  
  
 **Internet Explorer 이외의 웹 브라우저:** Internet Explorer 이외의 브라우저에서 재생하려면 테스트 코드에서 BrowserWindow.CurrentBrowser 속성을 **Firefox** 또는 **Chrome**으로 설정합니다.  
  
 IE가 아닌 웹 브라우저에서 테스트를 재생하려면 **코딩된 UI 다중 브라우저용 Selenium 구성 요소**를 설치해야 합니다.  
  
#### <a name="installing-selenium-components"></a>Selenium 구성 요소 설치  
  
1. **도구** 메뉴 모음에서 **확장 및 업데이트**를 선택합니다.  
  
2. [확장] 및 [업데이트] 대화 상자에서 `Selenium components for Cross Browser Testing`을 검색합니다.  
  
3. 확장명을 강조 표시하고 **다운로드**를 선택합니다.  
  
   > [!TIP]
   > 또한 [여기](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)에서 코딩된 UI 다중 브라우저 테스트용 Selenium 구성 요소를 다운로드할 수 있습니다.  
  
   코딩된 UI 테스트를 만들고 사용하는 방법은 [코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)를 참조하세요.  
  
### <a name="enable-debugging"></a>디버깅 사용  
 웹 애플리케이션을 디버깅하려면 다음 구성 옵션을 완료해야 합니다.  
  
1. 내 코드만 사용:  
  
    1. **도구** 메뉴에서 **옵션**을 선택한 다음 **디버깅**을 선택합니다.  
  
    2. **내 코드만 사용**을 선택합니다.  
  
2. CLR 예외 사용 안 함:  
  
    1. **디버그** 메뉴에서 **예외**를 선택합니다.  
  
    2. **공용 언어 런타임 예외**에 대해 **사용자가 처리하지 않음**을 선택 취소합니다.  
  
## <a name="generate"></a> *코딩된 UI 테스트에 BrowserWindow.CurrentBrowser를 변경할 수 있는 옵션이 표시되지 않습니다.*  
 다양한 웹 브라우저를 사용하여 코딩된 UI 테스트를 지원하지 않는 [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] 버전을 사용하는 중일 수 있습니다. 코딩된 UI 테스트를 사용하려면 Visual Studio Enterprise를 사용해야 합니다.  
  
 *그 외 무엇을 알아야 하나요?*  
 **참고**  
  
- ![필수 조건](../test/media/prereq.png "필수 조건") Apple Safari 웹 브라우저는 지원되지 않습니다.  
  
- ![필수 조건](../test/media/prereq.png "필수 조건") 웹 브라우저를 시작하는 작업은 코딩된 UI 테스트에 포함되어야 합니다.  
  
   웹 브라우저가 이미 열려 있는 상태에서는 Internet Explorer를 사용하지 않는 이상 단계를 실행하려고 해도 재생이 실패합니다. 따라서 코딩된 UI 테스트에 웹 브라우저 시작을 포함하는 것이 좋습니다.  
  
- ![필수 조건](../test/media/prereq.png "필수 조건") 최대화, 최소화, 복원 등의 브라우저별 기본 UI 작업은 자동화할 수 없습니다.  
  
  **팁**  
  
- ![팁](../test/media/tip.png "팁") 출력을 구성하여 코딩된 UI 로그에 스크린 샷을 포함할 수 있습니다. 이렇게 하려면 QTAgent32.exe.config 파일에 일부 구성 설정을 설정해야 합니다. 기본적으로 이 파일은 다음 디렉터리에 설치됩니다.  
  
   **C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE**  
  
   다음 값을 설정합니다.  
  
  - `EqtTraceLevel` 섹션의 `system.diagnostics`  
  
  - `<add name="EqtTraceLevel" value="4" />`  
  
     값을 3 이상으로 설정하면 각 작업에 대한 스크린 샷이 캡처됩니다. 값을 1 또는 2로 설정할 경우에는 스크린 샷이 오류 작업에 대해서만 캡처됩니다.  
  
    자세한 내용은 [코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)을 참조하세요.  
  
## <a name="external-resources"></a>외부 리소스  
  
### <a name="videos"></a>비디오  
 [IE에서 기록하고 어디에서나 재생](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [코딩된 UI 테스트 빌더로 다중 브라우저 테스트 작성](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [UI 맵 없이 일반 수작업 코딩으로 다중 브라우저 테스트 작성](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [여러 브라우저에서 다중 브라우저 테스트 순차 실행](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [다중 브라우저 테스트 오류 문제 해결](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### <a name="guidance"></a>지침  
 [Visual Studio 2012 – Chapter 2를 사용한 연속 배달 테스트: 단위 테스트: 내부 테스트](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Visual Studio 2012 – Chapter 5를 사용한 연속 배달 테스트: 시스템 테스트 자동화](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>FAQ  
 [코딩된 UI 테스트 FAQ - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [코딩된 UI 테스트 FAQ - 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>포럼  
 [Visual Studio UI 자동화 테스트(Coded UI 포함)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>참고 항목  
 [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)   
 [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
