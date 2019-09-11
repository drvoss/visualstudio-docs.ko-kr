---
title: Microsoft 도움말 뷰어 SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3e7cc2064e1ce74e2256d2246e46d2960c1cacc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349293"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft 도움말 뷰어 SDK

이 문서에서는 Visual Studio 도움말 뷰어 통합 업체에 대 한 다음 작업을 포함 됩니다.

- (F1 지원) 항목 만들기

- 도움말 뷰어 콘텐츠 브랜드 패키지 만들기

- 문서 집합을 배포합니다.

- Visual Studio shell (통합 또는 격리)에 추가 도움말

- 추가 리소스

## <a name="create-a-topic-f1-support"></a>(F1 지원) 토픽 만들기

이 섹션에서는 제공 된 항목, 항목에서는 요구 사항, 해당 렌더링 된 결과가 포함 된 항목 (F1 지원 요구 사항 포함) 및 마지막으로 예제 항목을 만드는 방법에 대 한 짧은 설명을의 구성 요소 개요를 제공 합니다.

**도움말 뷰어 항목 개요**

항목 렌더링에 대 한 호출 되 면 도움말 뷰어 설치 또는 XHTML 항목와 함께 마지막 업데이트 시 항목과 연관 된 브랜드 패키지 요소가 가져오고 두 콘텐츠 뷰에 표시 된 결과 결합 (데이터 브랜딩 + 항목 데이터)입니다.  브랜드 패키지에 로고, 콘텐츠 동작 및 브랜딩 텍스트 (저작권, 등)에 대 한 지원이 포함 되어 있습니다.  브랜드 패키지 요소에 대 한 자세한 내용은 아래 "브랜드 패키지 만들기"를 참조 하세요.  항목과 연결 브랜드 패키지가 있으면 이벤트에 도움말 뷰어는 도움말 뷰어 응용 프로그램 루트 (Branding_en US.mshc)에 있는 대체 (fallback) 브랜드 패키지를 사용 합니다.

**도움말 뷰어 항목에서는 요구 사항**

수는 도움말 뷰어 내에서 올바르게 렌더링을 원시 항목 콘텐츠 W3C 기본 1.1 XHTML 여야 합니다.

항목에는 일반적으로 두 개의 섹션이 포함 되어 있습니다.

- 메타 데이터 (참조 콘텐츠 메타 데이터): 예를 들어 항목 고유 ID, 키워드 값 항목 목차 ID 항목에 대 한 데이터 부모 등의 노드 ID입니다.

- 콘텐츠 본문: W3C 기본 1.1 XHTML 호환을 포함 하는 콘텐츠 동작 (축소 가능한 영역, 코드 조각 등 지원 전체 목록은 아래 표시 됩니다).

Visual Studio 브랜딩 패키지 컨트롤을 지원 합니다.

- 링크

- CodeSnippet

- CollapsibleArea

- 상속 된 멤버

- LanguageSpecificText

지원 되는 언어 문자열 (없습니다 대/소문자 구분):

- javascript

- csharp 또는 c#

- cplusplus visualc + + 또는 c + +

- jscript

- visualbasic 또는 vb

- f # fsharp 또는 fs

- 기타-언어 이름을 나타내는 문자열

**도움말 뷰어 항목을 만드는 중**

라는 ContosoTopic4.htm, XHTML 문서를 새로 만들고 title 태그 (아래)를 포함 합니다.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

다음으로, 추가 하는 방법 항목 (자체 브랜드 여부), 표시 되는 방식을 정의 하는 데이터 등을 F1, 목차에서 해당 ID (다른 항목으로 링크 참조) 내에 있는이 항목에 대 한이 항목을 참조 합니다. 지원 되는 메타 데이터의 전체 목록은 아래 "콘텐츠 메타 데이터" 표를 참조 하세요.

- 이 경우 고유한 브랜드 패키지를 Visual Studio 도움말 뷰어가 브랜드 패키지의 변형을 사용 됩니다.

- F1 메타 이름 및 값을 추가 ("Microsoft.Help.F1" 콘텐츠 "ContosoTopic4" =) IDE의 propertybag에 제공된 된 F1 값을 일치 하는 됩니다. (자세한 내용은 F1 지원 섹션을 참조 합니다.) 이 F1을 일치 하는 값은 IDE의 F1을 선택 하는 경우이 항목을 표시 하려면 ide에서 호출 합니다.

- 항목 ID를 추가 합니다. 이 항목에 연결할 다른 항목에서 사용 되는 문자열입니다. 이 항목에 대 한 도움말 뷰어 ID입니다.

- 목차에 대 한이 항목에서는 TOC 노드 표시 되는 위치를 정의 하려면이 항목의 부모 노드를 추가 합니다.

- 이 항목에서는 노드 순서 목차에 추가 합니다. 부모 노드에 있을 때 `n` 자식 수가 노드의 경우이 항목의이 위치를 자식 노드 순서 대로 정의 합니다. 예를 들어이 항목은 4 4 자식 항목의 수입니다.

예제 메타 데이터 섹션:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>
```

**항목 본문**

항목의 본문 (머리글 및 바닥글 제외 함)는 페이지 링크, 참고 섹션, 축소 가능한 영역, 코드 조각 및 언어별 텍스트의 섹션에 포함 됩니다.  브랜딩 표시 된 항목의 해당 영역에 대 한 자세한 내용은 섹션을 참조 하세요.

1. 항목 제목 태그를 추가 합니다.  `<div class="title">Contoso Topic 4</div>`

2. 참고 섹션을 추가 합니다. `<div class="alert"> add your table tag and text </div>`

3. 축소 가능한 영역을 추가 합니다.  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. 코드 조각을 추가 합니다.  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. 코드 언어 관련 텍스트를 추가 합니다.  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` `devLangnu=` 다른 언어를 입력할 수 있습니다. 예를 들어 `devLangnu="Fortran"` Fortran 표시 때 코드 조각을 DisplayLanguage Fortran =

6. 페이지 링크를 추가 합니다. `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> 참고:에 대 한 지원 되지 않는 새로운 "표시 언어" (예제에서는 F#, Cobol, Fortran) 코드 조각에서 코드 색 지정 단색 됩니다.

**예제에서는 도움말 뷰어 항목** 코드는 메타 데이터, 코드 조각, 축소 가능한 영역 및 언어 관련 텍스트를 정의 하는 방법을 보여 줍니다.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1 지원**

Visual Studio에서 F1을 선택 하면 IDE 내에서 커서의 위치에서 제공 하는 값을 생성을 채우는 "속성 모음"는 제공 된 값 (커서 위치를 기반으로 합니다. 커서 기능 x 이면 기능 x 활성/에서 포커스가 하 여 값을 사용 하 여 속성 모음을 채웁니다.  F1을 선택 하면 속성 모음 채워집니다 및 Visual Studio F1 코드만 고객 기본 도움말 소스 로컬 또는 온라인 인지 확인 (온라인 기본적으로) 한 다음 설정 하는 사용자를 기반으로 적절 한 문자열을 만듭니다 (online은 기본)-셸 실행 (가이드를 참조 하는 데 도움이 관리자 exe에 대 한 시작 매개 변수) 매개 변수는 로컬 도움말 뷰어 + 로컬 도움말을 기본값인 또는 매개 변수 목록에 키워드를 사용 하 여 MSDN URL 경우 propertybag에서 키워드를 사용 합니다.

다중값 문자열로 첫 번째 용어 조회에 대해 수행할 적중, 세 개의 문자열에 대 한 F1 반환 되는 경우 참조 하는 경우, 이제 끝났습니다; 및 그렇지 않은 경우 다음 문자열을 이동 합니다.  순서가 중요합니다. 다중 값 키워드의 표시에는 가장 짧은 문자열에 가장 긴 문자열 이어야 합니다.  이 다중값 키워드에 대 한 경우 확인 하려면 선택한 키워드를 포함 하는 온라인 F1 URL 문자열을 살펴봅니다.

Visual Studio 2012에서 의도적으로 만들었습니다 나누기를 강함 온라인 및 오프 라인 간에 온라인에 대 한 사용자의 설정 되었으면 다음에서는 단순히 F1 요청에 직접 전달 온라인 쿼리 서비스 도움말 라이브러리 에이전트를 통해 라우팅하는 것이 아니라 MSDN에서 있도록 Visual Studio 2010에서 했습니다. 그런 다음 의존 하는 상태 "설치 된 공급 업체 콘텐츠 = true" 해당 컨텍스트에서 다른 작업을 수행 여부를 결정 합니다. True 이면 다음 고객에 대 한 지원 하려는 항목에 따라이 구문 분석 및 라우팅 논리를 수행 합니다. False 이면 다음 우리가 방금으로 MSDN 사용자의 설정이 로컬 이면 로컬 도움말 엔진에 대 한 모든 호출은 이동 합니다.

F1 흐름 다이어그램:

![F1 흐름](../../extensibility/internals/media/f1flow.png "F1flow")

도움말 뷰어 기본 도움말 콘텐츠 소스 온라인 (브라우저에서 시작)로 설정 하면:

- Visual Studio 파트너 (VSP) 기능 (속성 모음 prefix.keyword 및 레지스트리에서 찾을 접두사에 대 한 온라인 URL) F1 propertybag에 값을 내보냅니다. F1은 VSP URL + 매개 변수를 브라우저에 보냅니다.

- Visual Studio 기능 (언어 편집기, Visual Studio 특정 메뉴 항목 등).  F1은 브라우저에는 Visual Studio URL을 보냅니다.

도움말 뷰어 기본 도움말 콘텐츠 소스 로컬 도움말 (도움말 뷰어에서 시작)로 설정 하면:

- VSP 기능 키워드 F1 속성 모음 및 로컬 저장소 인덱스 간에 일치 하는 위치 (속성 모음 prefix.keyword 즉, 로컬 저장소 인덱스에 있는 값 =):  F1 도움말 뷰어에서 항목을 렌더링합니다.

- Visual Studio 기능 (Visual Studio 기능에서 발생 하는 속성 모음의 재정의를 VSP에 대 한 옵션 없음): F1 도움말 뷰어에서 Visual Studio 항목을 렌더링합니다.

공급 업체 도움말 콘텐츠에 대 한 F1 대체 (fallback)를 사용 하도록 설정 하려면 다음 레지스트리 값을 설정 합니다. F1 대체 (fallback)는 도움말 뷰어 F1 도움말 콘텐츠를 검색할 온라인으로 설정 하 고 공급 업체 콘텐츠 사용자의 하드 드라이브에 로컬로 설치 되어 있는지를 의미 합니다. 도움말 뷰어에서 온라인 도움말에 대 한 기본 설정은 이더라도 콘텐츠에 대 한 로컬 도움말 같아야 합니다.

1. 설정 된 **VendorContent** 도움말 2.3 레지스트리 키 아래의 값:

   - 32 비트 운영 체제:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   - 64 비트 운영 체제:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

2. 2\.3 도움말 레지스트리 키에서 파트너 네임 스페이스를 등록 합니다.

   - 32 비트 운영 체제:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em>\\<namespace\></em>

      "location"="offline"

   - 64 비트 운영 체제:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em>\\<namespace\></em>

      "location"="offline"

**구문 분석 하는 기본 네이티브 Namespace**

구문 분석 하는 기본 네이티브 네임 스페이스를 설정 하려면 레지스트리에 이름으로 새 DWORD를 추가 합니다. BaseNativeNamespaces 해당 값을 1 (아래 지원 하고자 하는 카탈로그 키)로 설정 합니다.  예를 들어, Visual Studio 카탈로그를 사용 하려면 키 경로에 추가할 수 있습니다.

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

경우 헤더/메서드 발견 되는 형식에는 F1 키워드를 '/' 문자 구문 분석 됩니다, 다음 구문은 발생:

- 헤더: 레지스트리에 등록에 사용할 수 있는 네임 스페이스가 됩니다.

- 방법: 키워드를 통해 전달 되는이 됩니다.

예를 들어 CustomLibrary 라는 사용자 지정 라이브러리를 및 요청 제공에 F1로 포맷할 때 MyTestMethod, 라는 메서드를 지정 된 `CustomLibrary/MyTestMethod`합니다.

사용자가 다음 CustomLibrary 파트너 hive에서 네임 스페이스를 등록 하 고 원하는 모든 위치 키를 제공 하 고 쿼리를 전달 하는 키워드 MyTestMethod 됩니다.

**IDE에서 도구 디버깅 도움말을 사용 하도록 설정**

다음 레지스트리 키와 값을 추가 합니다.

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

값: 소매 데이터에서 디버그 출력을 표시 합니다. 예

IDE에서 도움말 메뉴 항목 선택 **도움말 컨텍스트 디버그**합니다.

**콘텐츠 메타 데이터**

다음 표에 대괄호 사이 나타나는 모든 문자열을 인식할 수 있는 값으로 대체 되어야 하는 자리 표시자입니다. 예를 들어, \<메타 name="Microsoft.Help.Locale" 콘텐츠 = "[언어 코드]" / >를 같은 "[언어 코드]" 값으로 대체 해야 합니다 "en-우리"입니다.

| 속성 (HTML 표시) | 설명 |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | 이 항목에 대 한 로캘을 설정합니다. 항목에서이 태그를 사용 하는 경우 한 번만 사용 해야 하 고 다른 Microsoft 도움말 태그 위에 삽입 해야 합니다. 항목의 본문 텍스트; 지정 된 경우 제품 로캘과 사용 하 여 연결 된 단어 분리기를 사용 하 여 인덱스화 되어이 태그를 사용 하지 않는 경우 이 고, 그렇지는 en-우리 단어 분리기가 사용 됩니다. 이 태그 ISOC RFC 4646을 준수 합니다. Microsoft 도움말 올바르게 작동 하도록 일반 언어 특성 대신이 속성을 사용 합니다. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | 다른 로캘에서 사용 하는 경우이 항목에 대 한 로캘을 설정 합니다. 이 태그 항목에서 사용 하는 경우 한 번만 사용 되어야 합니다. 카탈로그는 둘 이상의 언어로 콘텐츠를에서 포함 하는 경우이 태그를 사용 합니다. 카탈로그의 항목에서는 여러 ID가 같은 수 있지만 각 고유 TopicLocale 지정 해야 합니다. 카탈로그의 로캘과 일치 하는 TopicLocale를 지정 하는 항목에는 목차에 표시 되는 항목이입니다. 그러나 항목의 모든 언어 버전은 검색 결과에 표시 됩니다. |
| \< 제목 > [Title]\<제목/> | 이 항목의 제목을 지정합니다. 이 태그는 필요 이며 항목을 한 번만 사용 해야 합니다. 항목의 본문에 제목이 없는 경우 \<d i v > 섹션에이 제목은 목차에서 항목에 표시 됩니다. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | 도움말 뷰어의 인덱스 창에 표시 되는 링크의 텍스트를 지정 합니다. 링크를 클릭 하면 해당 항목이 표시 됩니다. 항목에 대 한 여러 인덱스 키워드를 지정할 수 있습니다 또는 인덱스에 표시 하려면이 항목에 대 한 링크를 원하지 않는 경우이 태그를 생략할 수 있습니다. 이 속성에 이전 버전의 도움말에서 "K" 키워드를 변환할 수 있습니다. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | 이 항목에 대 한 식별자를 설정합니다. 이 태그는 필요 이며 항목을 한 번만 사용 해야 합니다. ID는 로캘 설정이 같아야 하는 카탈로그의 항목 중에서 고유 해야 합니다. 다른 항목에서이 ID를 사용 하 여이 항목에 대 한 링크를 만들 수 있습니다. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ > | 이 항목에 대 한 F1 키워드를 지정합니다. 이 항목에서는 응용 프로그램 사용자가 F1 키를 누를 때 표시할를 원하지 않는 경우이 태그를 생략할 수 있습니다 또는 항목에 대 한 여러 F1 키워드를 지정할 수 있습니다. 일반적으로 항목에 대 한 F1 키워드를 하나만 지정 됩니다. 이 속성에 이전 버전의 도움말에서 "F" 키워드를 변환할 수 있습니다. |
| \< meta name="Description" content="[topic description]" /> | 이 항목의 내용에 대 한 짧은 요약을 제공합니다. 이 태그 항목에서 사용 하는 경우 한 번만 사용 되어야 합니다. 이 속성은 쿼리 library;에서 직접 액세스 인덱스 파일에 저장 되지 않습니다. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | 목차에서이 항목의 부모 항목을 지정합니다. 이 태그는 필요 이며 항목을 한 번만 사용 해야 합니다. 값은 부모의 Microsoft.Help.Id. 항목 내용의 테이블의 한 위치에 있을 수 있습니다. "-1"에 목차 루트에 대 한 항목 ID로 간주 됩니다. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], 해당 페이지에는 도움말 뷰어 홈 페이지입니다. 에서는 특히 TocParent = 1 표시 되는 것 맨 위에 있는 수준 수 있도록 몇 가지 항목을 추가 하는 동일한 이유입니다. 도움말 뷰어 홈 페이지는 시스템 페이지와 하므로 대체 불가능 합니다. VSP에-1의 ID 사용 하 여 페이지를 추가 하려고 하는 경우 해당 콘텐츠 집합에 추가 될 수 있습니다 하지만 도움말 뷰어는 도움말 뷰어 홈 system 페이지-항상 사용 |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | 목차에서이 항목에서는 표시 되는 피어 항목을 기준으로 지정 합니다. 이 태그는 필요 이며 항목을 한 번만 사용 해야 합니다. 값은 정수입니다. 값이 더 낮은 정수를 지정 하는 항목 값이 더 높은 정수를 지정 하는 항목 위에 나타납니다. |
| \< meta name="Microsoft.Help.Product" 콘텐츠 = "[product code]" / > | 이 항목에 설명 된 제품을 지정 합니다. 이 태그 항목에서 사용 하는 경우 한 번만 사용 되어야 합니다. 이 정보는 도움말 인덱서에 전달 되는 매개 변수로 지정할 수도 있습니다. |
| \< meta name="Microsoft.Help.ProductVersion" 콘텐츠 = "[버전]" / > | 이 항목에 설명 된 제품의 버전을 지정 합니다. 이 태그 항목에서 사용 하는 경우 한 번만 사용 되어야 합니다. 이 정보는 도움말 인덱서에 전달 되는 매개 변수로 지정할 수도 있습니다. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | 제품 사용 콘텐츠의 하위 섹션을 식별 합니다. 항목에 대 한 여러 하위 섹션을 식별할 수 있습니다 또는 하위 섹션을 식별 하는 링크를 원하지 않는 경우이 태그를 생략할 수 있습니다. 이 태그는 특성을 저장 TargetOS 및 TargetFrameworkMoniker 도움말의 이전 버전에서 항목을 변환할 때 사용 됩니다. 콘텐츠의 형식이 AttributeName:AttributeValue 되었습니다. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | 카탈로그에 여러 버전이 있을 경우 항목의이 버전을 지정 합니다. 항목의 버전이 둘 이상 카탈로그.NET Framework 3.5 및 항목에 대 한.NET Framework 4에 대 한 항목을 포함 하 고 둘 다 동일한 마이크로 경우 예를 들어 카탈로그에 있는 경우이 태그는 필요한 Microsoft.Help.Id 고유 하지 않으므로, 소프트 합니다. Help.Id 합니다. |
| \< meta 이름 = "SelfBranded" content = "[TRUE 또는 FALSE]" / > | 이 항목에서는 도움말 라이브러리 관리자 시작 브랜드 패키지 또는 항목에 관련 된 브랜드 패키지를 사용 하는지 여부를 지정 합니다. 이 태그는 TRUE 여야 합니다. 또는 FALSE입니다. 있으면 TRUE, 관련된 항목에 대 한 브랜딩 패키지 항목의 다른 콘텐츠 렌더링에서 서로 다른 경우에 의도 한 대로 렌더링 되도록 도움말 라이브러리 관리자를 시작할 때 설정 된 브랜드 패키지를 재정의 합니다. FALSE 인 경우 현재 항목은 도움말 라이브러리 관리자를 시작할 때 설정 된 브랜드 패키지에 따라 렌더링 됩니다. 기본적으로 도움말 라이브러리 관리자 가정 SelfBranded 변수가; TRUE로 선언 된 경우가 아니면 false로 자체 브랜딩 따라서 선언할 필요가 없습니다 \<메타 이름 = "SelfBranded" content = "FALSE" / >입니다. |

## <a name="create-a-branding-package"></a>브랜드 패키지 만들기

Visual Studio 릴리스는 Visual Studio 파트너에 대 한 격리 및 통합된 셸을 비롯 한 다양 한 Visual Studio 제품의 수를 포함 합니다.  이러한 제품의 각 항목 기반 도움말 콘텐츠의 지원 제품에 고유 브랜딩 어느 정도 필요 합니다.  예를 들어, Visual Studio 항목 해야 일관 된 브랜드 프레젠테이션을 SQL Studio ISO 셸을 래핑하는 자체 고유 도움말 내용에 대 한 브랜딩 각 항목에서는 사용 해야 합니다.  통합 셸 파트너를 브랜딩 하는 고유한 항목을 유지 하면서 Visual Studio 제품 도움말 콘텐츠 부모 내에서 되도록 해당 도움말 항목 좋습니다.

브랜드 패키지는 도움말 뷰어를 포함 하는 제품으로 설치 됩니다.  Visual Studio 제품:

- 대체 (fallback) 브랜드 패키지 (Branding_\<로캘 >.mshc) 도움말 뷰어 2.3 앱 루트에 설치 됩니다 (예: C:\Program 파일 (x86) \Microsoft Help Viewer\v2.3) 도움말 뷰어 언어 팩을 통해.  이 패키지를 브랜딩 제품 설치 되지 않은 경우에 사용 됩니다 (콘텐츠 없음 설치) 설치 된 브랜드 패키지가 없거나 손상 되었습니다.  Visual Studio 요소 (예: 로고 및 피드백) 앱 루트 대체 (fallback) 브랜드 패키지를 사용 하는 경우 무시 됩니다.

- 콘텐츠 패키지 서비스에서 Visual Studio 콘텐츠 설치 되 면 (첫 번째 시간 콘텐츠 설치 시나리오)에 대 한 브랜딩 패키지도 설치 됩니다.  브랜드 패키지에 대 한 업데이트 인 경우 다음 콘텐츠 업데이트 또는 추가 패키지 설치 작업을 수행 하는 경우 업데이트가 설치 됩니다.

Microsoft 도움말 뷰어는 항목 메타 데이터에 따라 항목의 브랜딩 지원 합니다.

- 항목 메타 데이터 정의 브랜드 셀프 = true, 그대로 항목 렌더링 (브랜드)에 관해서는 아무 작업도 수행 합니다.

- = False, 브랜드 셀프 항목 메타 데이터 정의 TopicVendor 메타 데이터 값과 연결 된 브랜드 패키지를 사용 합니다.

- 콘텐츠 위치 항목 메타 데이터 정의 name="Microsoft.Help.TopicVendor" =\< MSHA 공급 업체에 브랜드 패키지 이름 >, 콘텐츠 값에 정의 된 브랜드 패키지를 사용 합니다.

- Visual Studio 카탈로그 내에서 우선 순위 응용 프로그램을 브랜딩 패키지 있습니다.  첫 번째 Visual Studio 기본 브랜딩 적용 되 고 그런 다음 항목 메타 데이터에 정의 및 사용 하 여 지원 되는 경우 연결 된 브랜딩 (에 정의 된 설치 msha), 패키지 브랜딩 공급 업체 정의 된 재정의로 적용 됩니다.

브랜딩 요소는 일반적으로 세 가지 주요 범주로 구분 됩니다.

- 헤더 요소 (예를 들면 피드백 링크, 조건부 고 지 사항, 로고)

- 동작 (예제 확장/축소 컨트롤 텍스트 요소를 포함 및 코드 조각 요소)을 콘텐츠

- 바닥글 요소 (예: 저작권)

브랜드 요소에 포함 되어 있으므로 간주 하는 항목 (이 사양에 자세히 설명).

- 카탈로그/제품 로고 (예제에서는 Visual Studio)

- 피드백 링크 및 전자 메일 요소

- 고 지 사항 텍스트

- 저작권 텍스트

Visual Studio 도움말 뷰어가 브랜드 패키지에 지원 파일은 다음과 같습니다.

- 그래픽 (로고, 아이콘 등)

- Branding.js-스크립트 파일 지원 콘텐츠 동작

- Branding.xml-카탈로그 콘텐츠 간에 일관 되 게 사용 되는 문자열입니다.  참고: Visual Studio는 branding.xml 지역화 텍스트 요소에 _locID 포함 = "\<고유 값 >"

- Branding.css-프레젠테이션 일관성에 대 한 스타일 정의

- Printing.css-인쇄 된 일관성 있는 프레젠테이션에 대 한 스타일 정의

위에서 언급 했 듯이 브랜드 패키지는 항목으로 연결:

- 때 SelfBranded = false 메타 데이터에 정의 된, 패키지를 브랜딩 하는 카탈로그를 상속 하는 항목

- 때나 SelfBranded = false, 있습니다 고유 브랜딩 패키지 정의 됩니다는 MSHA에 사용할 수 있는 콘텐츠를 설치 하는 경우

VSPs 브랜딩 사용자 지정 패키지를 구현에 대 한 (VSP 콘텐츠를 SelfBranded = True)를 계속 하는 한 가지 방법은 (도움말 뷰어를 사용 하 여 설치)를 대체 (fallback) 브랜드 패키지를 사용 하 여 시작 하 고 적절 하 게 파일의 이름을 변경 하는 것입니다.  Branding_\<로캘 >.mshc 파일이.mshc로 변경 하는 파일 확장명을 가진 zip 파일, 따라서 단순히을.zip.mshc에서 확장을 변경 하 고 압축을 풉니다.  적절 하 게 수정 하 고 브랜드 패키지 요소에 대 한 아래를 참조 하세요 (예를 들어 VSP 로고 및 Branding.xml 파일에서 로고에 대 한 참조에 로고를 변경, VSP 세부 사항 등 당 Branding.xml 업데이트) 합니다.

모든 수정 작업을 완료 하는 경우 원하는 브랜딩 요소를 포함 한 zip 파일 만들고.mshc 확장이 변경 합니다.

브랜딩 사용자 지정 패키지에 연결 하려면 (항목 포함) 콘텐츠 mshc 함께 브랜딩 mshc 파일에 대 한 참조를 포함 하는 MSHA를 만듭니다.  기본 MSHA를 만드는 방법에 대 한 "MSHA" 아래를 참조 하세요.

Branding.xml 파일에 일관 되 게 항목을 포함 하는 경우 항목에서 특정 항목을 렌더링 하는 데 사용 되는 요소 목록이 \<메타 name="Microsoft.Help.SelfBranded" 콘텐츠 = "false" / >입니다.  Visual Studio에 대 한 목록은 Branding.xml 파일의 요소는 아래 나열 됩니다.  이 목록은 ISO 셸 도입자, 이러한 요소 (예: 로고, 피드백 및 저작권) 자신의 제품 브랜딩에 맞게 수정 위치에 대 한 템플릿을 요구 사항에 맞춰 사용할 것입니다.

참고: "{n}"에서 설명 하는 변수 코드 종속성이 있는-제거 하거나 이러한 값을 변경 하면 오류 및 응용 프로그램 작동이 중단 됩니다. 지역화 식별자 (예제 _locID="codesnippet.n")는 Visual Studio 브랜드 패키지에 포함 됩니다.

**Branding.xml**

| | |
| - | - |
| 기능: | **CollapsibleArea** |
| 사용: | 축소 텍스트 콘텐츠 컨트롤을 확장 합니다. |
| **요소** | **값** |
| ExpandText | Expand |
| CollapseText | 축소 |
| 기능: | **CodeSnippet** |
| 사용: | 코드 조각 컨트롤 텍스트입니다.  참고: 코드 조각 내용 "아님" 공간을 사용 하 여 공간으로 변경 됩니다. |
| **요소** | **값** |
| CopyToClipboard | 클립보드에 복사 |
| ViewColorizedText | 컬러로 보기 |
| CombinedVBTabDisplayLanguage | Visual Basic (샘플) |
| VBDeclaration | 선언 |
| VBUsage | 사용 |
| 기능: | **피드백, 바닥글 및 로고** |
| 사용: | 전자 메일을 통해 현재 항목에 대 한 피드백을 제공 하는 고객에 대 한 피드백 컨트롤을 제공 합니다.  콘텐츠에 대 한 저작권 텍스트입니다.  로고 정의입니다. |
| **요소** | **값 (콘텐츠 얼 리 어댑터 요구에 맞게 이러한 문자열을 수정할 수 있습니다.)** |
| CopyRight | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a = "{0}" {1}> 사용자 의견 보내기 \< /a >이 항목에서는 microsoft에서. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| 기능: | **고 지 사항** |
| 사용: | 컴퓨터에 대 한 경우 관련 고 지 사항 집합이 콘텐츠를 변환 합니다. |
| **요소** | **값** |
| MT_Editable | 이 문서는 기계 번역 되었습니다. 인터넷에 연결 하는 경우 동시 원본 영어 콘텐츠를 사용 하 여 편집 가능한 모드에서이 페이지를 보려면 "온라인에서이 항목 보기"를 선택 합니다. |
| MT_NonEditable | 이 문서는 기계 번역 되었습니다. 인터넷에 연결 하는 경우 동시 원본 영어 콘텐츠를 사용 하 여 편집 가능한 모드에서이 페이지를 보려면 "온라인에서이 항목 보기"를 선택 합니다. |
| MT_QualityEditable | 이 문서에서는 수동으로 번역 되었습니다. 인터넷에 연결 하는 경우 동시 원본 영어 콘텐츠를 사용 하 여 편집 가능한 모드에서이 페이지를 보려면 "온라인에서이 항목 보기"를 선택 합니다. |
| MT_QualityNonEditable | 이 문서에서는 수동으로 번역 되었습니다. 인터넷에 연결 하는 경우 동시 원본 영어 콘텐츠를 사용 하 여 편집 가능한 모드에서이 페이지를 보려면 "온라인에서이 항목 보기"를 선택 합니다. |
| MT_BetaContents | 이 문서는 예비 릴리스용으로 번역 되었습니다. 인터넷에 연결 하는 경우 동시 원본 영어 콘텐츠를 사용 하 여 편집 가능한 모드에서이 페이지를 보려면 "온라인에서이 항목 보기"를 선택 합니다. |
| MT_BetaRecycledContents | 이 문서는 예비 릴리스용으로 수동으로 번역 되었습니다. 인터넷에 연결 하는 경우 동시 원본 영어 콘텐츠를 사용 하 여 편집 가능한 모드에서이 페이지를 보려면 "온라인에서이 항목 보기"를 선택 합니다. |
| 기능: | **LinkTable** |
| 사용: | 온라인 항목 링크에 대 한 지원 |
| **요소** | **값** |
| LinkTableTitle | 링크 테이블 |
| TopicEnuLinkText | 영어 버전을 보려면 \< /a > 컴퓨터에 사용할 수 있는이 항목의 합니다. |
| TopicOnlineLinkText | 이 항목 보기 \<a = "{0}" {1}> 온라인 \< /a > |
| OnlineText | Online |
| 기능: | **비디오의 오디오 컨트롤** |
| 사용: | 요소 및 비디오 콘텐츠에 대 한 텍스트를 표시 합니다. |
| **요소** | **값** |
| MultiMediaNotSupported | 지원 하기 위해 Internet Explorer 9 또는 큰 반드시 설치할 {0} 콘텐츠입니다. |
| VideoText | 비디오를 표시합니다. |
| AudioText | 오디오를 스트리밍 |
| OnlineVideoLinkText | \<p >이 항목과 연결 된 비디오를 보려면 클릭 {0} \<는 href = "{1}" >{2}여기\</a >.\< / p > |
| OnlineAudioLinkText | \<p >이 항목과 연결 된 오디오를 들으려면, 클릭 {0} \<는 href = "{1}" >{2}여기\</a >.\< / p > |
| 기능: | **콘텐츠 설치 되지 않은 컨트롤** |
| 사용: | Contentnotinstalled.htm의 렌더링에 사용 되는 텍스트 요소 (문자열) |
| **요소** | **값** |
| ContentNotInstalledTitle | 컴퓨터에 없는 콘텐츠 찾을 수 있습니다. |
| ContentNotInstalledDownloadContentText | \<p > 사용자의 컴퓨터에 콘텐츠를 다운로드 하려면 \<a = "{0}" {1}> [관리] 탭을 클릭\</a >.\< / p > |
| ContentNotInstalledText | \<p > 콘텐츠가 없는 컴퓨터에 설치 됩니다. 로컬 도움말 콘텐츠 설치 관리자를 참조 하세요.  \< /p > |
| 기능: | **컨트롤을 찾을 수 없습니다 하는 항목** |
| 사용: | Topicnotfound.htm의 렌더링에 사용 되는 텍스트 요소 (문자열) |
| **요소** | **값** |
| TopicNotFoundTitle | 컴퓨터에서 요청한 항목을 찾을 수 없습니다. |
| TopicNotFoundViewOnlineText | \<p > 요청한 항목에서는 컴퓨터에서 찾을 수 없습니다 하 고 있지만 \<a = "{0}" {1}>의 항목을 온라인\</a >.\< / p > |
| TopicNotFoundDownloadContentText | \<p > 탐색 창 유사한 항목에 대 한 링크를 참조 하세요. 또는 \<a = "{0}" {1}> 관리 탭을 클릭\</a >를 컴퓨터에 콘텐츠를 다운로드 합니다.\< / p > |
| TopicNotFoundText | \<p > 요청한 항목에서는 컴퓨터에서 찾을 수 없습니다.  \< /p > |
| 기능: | **항목 컨트롤을 손상** |
| 사용: | Topiccorrupted.htm의 렌더링에 사용 되는 텍스트 요소 (문자열) |
| **요소** | **값** |
| TopicCorruptedTitle | 요청한 항목을 표시할 수 없습니다. |
| TopicCorruptedViewOnlineText | \<p > 도움말 뷰어에서 요청한 항목을 표시할 수 없는 합니다. 항목의 콘텐츠나 기본 시스템 종속성을에서 오류가 발생할 수 있습니다.  \< /p > |
| 기능: | **홈 페이지 컨트롤** |
| 사용: | 텍스트의 도움말 뷰어 최상위 노드 콘텐츠를 표시 하도록 지원 합니다. |
| **요소** | **값** |
| HomePageTitle | 도움말 뷰어 홈 |
| HomePageIntroduction | \<p > Microsoft 도움말 뷰어, 꼭 필요한 리소스는 모든 Microsoft 도구, 제품, 기술 및 서비스를 사용 하 여 사용자에 대 한 정보의 원천을 시작 합니다. 도움말 뷰어 사용 방법 및 참조 정보, 샘플 코드, 기술 문서 등에 액세스할 수 있습니다. 목차를 탐색 해야 하는 콘텐츠를 찾으려면 전체 텍스트 검색을 사용 하거나 키워드 색인을 사용 하 여 콘텐츠를 탐색 합니다.  \< /p > |
| HomePageContentInstallText | \<p >\<b r / > 사용 합니다 \<a = "{0}" {1}> 콘텐츠 관리\</a > 다음을 수행 하는 탭:\<ul >\<l i > 컴퓨터에 콘텐츠를 추가 합니다.\< / l i >\<l i > 로컬 콘텐츠에 업데이트를 확인 합니다.\< / l i >\<l i > 컴퓨터에서 콘텐츠를 제거 합니다.\< / l i >\</u l > \< /p > |
| HomePageInstalledBooks | 설치 된 책 |
| HomePageNoBooksInstalled | 컴퓨터에 없는 콘텐츠 찾을 수 있습니다. |
| HomePageHelpSettings | 도움말 콘텐츠 설정 |
| HomePageHelpSettingsText | \<p > 현재 설정에는 로컬 도움말입니다. 도움말 뷰어는 컴퓨터에 설치 된 콘텐츠를 표시 합니다. \<b r / > Visual Studio 메뉴 모음에서 도움말 콘텐츠의 소스를 변경 하려면 선택 \<style = "{0}" > 도움말, 도움말 기본 설정 지정\</s p a n >.\< b r / > \< /p > |
| MegaByte | MB |

**branding.js**

Branding.js 파일에서 Visual Studio 도움말 뷰어가 브랜딩 요소를 사용 하는 JavaScript를 포함 합니다.  브랜딩 요소 및 지원 JavaScript 함수의 목록은 다음과 같습니다.  모든 문자열을이 파일에 대 한 지역화할 수는이 파일의 맨 위에 있는 "지역화 가능한 문자열" 섹션에 정의 됩니다.  Branding.js 파일 내에서 loc 문자열 ICL 파일을 만들었습니다.

||||
|-|-|-|
|**브랜딩 기능**|**JavaScript 함수**|**설명**|
|Var는 중...||변수 정의|
|사용자 코드 언어|setUserPreferenceLang|인덱스 매핑합니다 # 코드 언어를|
|설정 하 고 쿠키 값을 얻으려면|getCookie, setCookie||
|상속 된 멤버|changeMembersLabel|상속 된 멤버를 확장/축소 합니다.|
|때 SelfBranded = False|onLoad|인쇄 요청 인지 확인 하려면 쿼리 문자열을 읽습니다.  사용자 기본 설정된 탭에 초점을 모든 codesnippets를 설정 합니다.  인쇄 요청 이기 isPrinterFriendly true로 설정 합니다. 고대비 모드를 확인 합니다.|
|코드 조각|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|목록에 모든 축소 가능 컨트롤 개체를 작성 합니다.|
||CA_Click|축소 가능한 영역의 상태에 따라, 어떤 이미지 및 텍스트 표시를 정의 합니다.|
|로고에 대 한 대비 지원|isBlackBackground()|배경을 검정색 인지 확인 하기 위해 호출 됩니다.  정확한 경우에만 고대비 모드에서.|
||isHighContrast()|색이 지정 된 범위를 사용 하 여 고대비 모드를 검색 합니다.|
||onHighContrast(black)|고대비 감지 될 때 호출|
|LST 기능|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|멀티미디어 기능|캡션 (시작, 끝, 텍스트, 스타일)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||subtitle(id)||

**HTM 파일**

브랜드 패키지 콘텐츠 집합은 설치를 설명 하는 섹션 및 항목 수 없는 경우 라는 페이지를 포함 하는 홈 페이지 예를 들어 도움말 콘텐츠 사용자에 게 주요 정보를 통신 하기 위한 시나리오를 지 원하는 HTM 파일 집합을 포함 로컬 항목 집합에서 찾을 수 있습니다. 제품당 이러한 HTM 파일을 수정할 수 있습니다.  ISO 셸 공급 업체 기본 브랜딩 패키지를 가져오고 변경 동작 및 콘텐츠이 페이지의 도구 모음에 요구 사항을 수 있습니다.  이러한 파일 branding.xml 파일에서 해당 콘텐츠를 가져올 브랜딩 태그에 대 한 순서 대로 해당 해당 브랜드 패키지를 참조 하십시오.

||||
|-|-|-|
|**파일**|**사용 하 여**|**콘텐츠 원본 표시**|
|homepage.htm|현재 설치 된 콘텐츠 및 해당 내용에 대 한 사용자에 게 제공 하는 적절 한 다른 메시지를 표시 하는 페이지입니다.  이 파일에 추가 메타 데이터 특성 "Microsoft.Help.Id" 콘텐츠 = "-1"이 콘텐츠는 로컬 콘텐츠 TOC의 맨 위에 있는 배치 합니다.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, tag \<HomePageTitle>|
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.xml, 태그 \<HomePageIntroduction >|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, tag \<HomePageContentInstallText>|
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Branding.xml 태그 섹션 제목\<HomePageInstalledBooks >, 응용 프로그램에서 생성 된 데이터 \<HomePageNoBooksInstalled > 설명서가 없습니다. 설치 된 경우.|
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Branding.xml 태그 섹션 제목 \<HomePageHelpSettings >, 텍스트 섹션 \<HomePageHelpSettingsText >.|
|topiccorrupted.htm|하지만 어떤 이유로 든 표시 될 수 없는 항목 집합을 로컬에 있는 경우 (손상 된 콘텐츠).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, tag \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, tag \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|때 항목에에서 없는 로컬 콘텐츠를 설정 하거나 사용 가능한 온라인||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, tag \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, tag \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, tag \<TopicNotFoundText>|
|contentnotinstalled.htm|제품에 대 한 설치 된 로컬 콘텐츠가 없는 경우.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, tag \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, tag \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, tag \<ContentNotInstalledText>|

**CSS 파일**

Visual Studio 도움말 뷰어 브랜드 패키지는 일관 된 Visual Studio 도움말 콘텐츠 표시를 지원 하기 위해 두 css 파일이 포함 되어 있습니다.

- 위치를 렌더링 하는 것에 대 한 css 요소를 포함 하는 Branding.css-SelfBranded = false

- 위치를 렌더링 하는 것에 대 한 css 요소를 포함 하는 Printer.css-SelfBranded = false

Branding.css 파일에는 Visual Studio 항목 표시에 대 한 정의가 포함 됩니다 (의 branding.css는 Branding_에 포함 되도록 하는 것이 점은\<로캘 >.mshc 패키지 서비스에서 변경 될 수 있습니다).

**그래픽 파일**

Visual Studio 콘텐츠는 다른 그래픽 뿐 아니라 Visual Studio 로고를 표시합니다.  Visual Studio 도움말 뷰어가 브랜드 패키지에 그래픽 파일의 전체 목록은 다음과 같습니다.

||||
|-|-|-|
|**파일**|**사용 하 여**|**예제**|
|clear.gif|축소 가능한 영역을 렌더링 하는 데 사용||
|footer_slice.gif|바닥글 표시||
|info_icon.gif|정보를 표시할 때 사용|고지 사항|
|online_icon.gif|이 아이콘은 온라인 링크를 사용 하 여 연결||
|tabLeftBD.gif|코드 조각 컨테이너를 렌더링 하는 데 사용||
|tabRightBD.gif|코드 조각 컨테이너를 렌더링 하는 데 사용||
|vs_logo_bk.gif|Branding.xml 태그에 정의 된 대로 표준 대비 로고 참조에 대 한 사용 \<LogoFileName >.  Visual Studio 제품, 로고 이름은 vs_logo_bk.gif입니다.||
|vs_logo_wh.gif|Branding.xml 태그에 정의 된 대로 표준 높은 로고 참조에 대 한 사용 \<LogoFileNameHC >.  Visual Studio 제품, 로고 이름은 vs_logo_wh.gif입니다.||
|ccOff.png|선택 캡션 그래픽||
|ccOn.png|선택 캡션 그래픽||
|ImageSprite.png|축소 가능한 영역을 렌더링 하는 데 사용|확장 또는 축소 그래픽|

## <a name="deploy-a-set-of-topics"></a>항목 집합을 배포 합니다.

이 MSHA 파일 및 cab 또는 MSHCs 항목이 들어 있는 집합을 구성 된 도움말 뷰어 콘텐츠 배포 집합을 만드는 쉽고 빠른 자습서입니다. MSHA는 cab 파일의 집합을 설명 하는 XML 파일 또는 MSHC 파일입니다. 도움말 뷰어 (합니다 콘텐츠 목록을 가져오려면 MSHA를 읽을 수 있습니다. CAB 또는 합니다. MSHC 파일) 로컬 설치에 사용할 수 있습니다.

이 매우 기본적인 XML 스키마를 설명 하는 도움말 뷰어 MSHA에 대 한 입문서만입니다.  이 간략 한 개요 및 샘플 HelpContentSetup.msha 아래 예제에서는 구현 방법이 있습니다.

MSHA이이 입문서를 위해 이름이 HelpContentSetup.msha (파일의 이름일 수 있습니다 확장을 사용 하 여 작업 합니다. MSHA)입니다. HelpContentSetup.msha (아래 예제) MSHCs 사용 가능한 cab 파일의 목록을 포함 해야 합니다.  파일 형식 (MSHA 및 CAB 파일 형식의 조합을 지원 하지 않습니다) MSHA 내에서 일치 해야 합니다. 각 CAB 또는 MSHC 없어야는 \<div 클래스 "패키지" = >... \</div > (아래 예제 참조).

참고: 아래 구현은 예제에 포함 했습니다 브랜딩 패키지. 이것이 필요한 Visual Studio 콘텐츠 렌더링 요소 및 콘텐츠 동작을 얻기 위해 포함 하는 데 중요 합니다.

Sample HelpContentSetup.msha file: ("콘텐츠 설정 1 이름" 바꾸기 및 "2" 등 파일 이름 집합 이름을 콘텐츠입니다.)

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1. "C:\SampleContent"와 같은 로컬 폴더를 만듭니다

2. 예를 들어 항목을 포함 하도록 MSHC 파일 사용 합니다.  MSHC를.zip에서 변경 된 파일 확장명을 가진 zip입니다. MSHC 합니다.

3. 만들기를 텍스트 파일로 HelpContentSetup.msha 아래 (메모장 파일을 만드는 데 사용 된) 위의 기록 된 폴더에 저장 하 고 (1 단계 참조).

"브랜드" 존재 하 고 고유한 클래스를 사용 합니다. 설치 된 콘텐츠는 브랜딩, 있고 콘텐츠 동작을 MSHCs에 포함 된 브랜드 패키지에 포함 된 적절 한 지원 요소를 갖습니다 있도록 브랜드 mshc이이 입문서에 포함 됩니다. 이렇게 하지 않으면 시스템은 지원 되지 않는 항목은 복사한 (설치)의 일부에 대 한 콘텐츠 때 오류가 발생 합니다.

패키지를 브랜딩 하는 Visual Studio를 가져오려면 C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ Branding_en US.mshc 파일 작업 폴더에 복사 합니다.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>
```

**요약**

사용 하 고 위의 단계를 확장 Visual Studio 도움말 뷰어에 대 한 해당 콘텐츠 집합을 배포 하는 Vsp 사용 하도록 설정 됩니다.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio Shell (통합 및 격리)에 대 한 도움말 추가

**소개**

이 연습에는 Visual Studio Shell 응용 프로그램에 도움말 콘텐츠를 통합 한 후에 배포 하는 방법을 보여 줍니다.

**요구 사항**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Shell 재배포 가능 패키지를 격리](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**개요**

합니다 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell의 버전이 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 응용 프로그램을 사용할 수 있는 IDE. 이러한 응용 프로그램 격리 셸 확장 사용자가 만든 함께 포함 합니다. 에 포함 된 격리 된 셸 프로젝트 템플릿을 사용 하 여는 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK extensions를 빌드할 수 있습니다.

격리 셸 기반 응용 프로그램 및 해당 도움말을 만들기 위한 기본 단계:

1. 가져오기는 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell 재배포 가능 패키지 (Microsoft 다운로드).

2. Visual Studio에서 기반으로 하는 Isolated Shell을 예를 들어 도움말 확장,이 연습의 뒷부분에서 설명 하는 Contoso 지원 확장을 만듭니다.

3. 확장 및 ISO 셸을 MSI (응용 프로그램 설치) 배포에 재배포 가능 패키지를 래핑하십시오. 이 연습에서는 설치 단계를 포함 하지 않습니다.

Visual Studio 콘텐츠 저장소를 만듭니다. Integrated Shell 시나리오의 경우 제품 카탈로그 이름을 Visual Studio12 다음과 같이 변경 합니다.

- C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 폴더를 만듭니다.

- CatalogType.xml 라는 파일을 만들고 폴더에 추가 합니다. 파일에 다음 코드 줄은 있어야 합니다.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

레지스트리에서 콘텐츠 저장소를 정의 합니다. Integrated Shell에 대 한 VisualStudio15 제품 카탈로그 이름으로 변경 합니다.

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   키: LocationPath 문자열 값입니다. C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   키: CatalogName 문자열 값입니다. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 설명서

**프로젝트 만들기**

격리 셸 확장을 만들려면:

1. Visual Studio에서 아래의 **파일**, 선택 **새 프로젝트**아래에 있는 **기타 프로젝트 형식** 선택 **확장성**를 선택한 다음  **Visual Studio Shell 격리**합니다. 프로젝트 이름을 `ContosoHelpShell`) Visual Studio Isolated Shell 템플릿을 기반으로 하는 확장성 프로젝트를 만듭니다.

2. 솔루션 탐색기에서 리소스 파일 폴더에서 ContosoHelpShellUI 프로젝트에서 ApplicationCommands.vsct를 엽니다. 이 줄 ("No_Help" 검색) 주석 처리 되어 있는지 확인 합니다. `<!-- <define name="No_HelpMenuCommands"/> -->`

3. 컴파일하고 실행 하려면 F5 키 선택 **디버그**합니다. 격리 된 셸 IDE의 실험적 인스턴스를 선택 합니다 **도움말** 메뉴. 있는지 확인 합니다 **도움말 보기**를 **콘텐츠 추가 및 제거 하는 데 도움이**, 및 **도움말 기본 설정 지정** 명령을 표시 합니다.

4. 솔루션 탐색기에서 셸 사용자 지정 폴더에서 ContosHelpShell 프로젝트에서 ContosoHelpShell.pkgdef를 엽니다. Contoso 도움말 카탈로그를 정의 하려면 다음 줄을 추가 합니다.

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. 솔루션 탐색기에서 셸 사용자 지정 폴더에서 ContosHelpShell 프로젝트에서 ContosoHelpShell.Application.pkgdef를 엽니다. F1 도움말을 사용 하려면 다음 줄을 추가 합니다.

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6. 솔루션 탐색기에서 상황에 맞는 메뉴 ContosoHelpShell 솔루션을 선택 합니다 **속성** 메뉴 항목입니다. 아래 **구성 속성**를 선택 **Configuration Manager**합니다. 에 **구성** 열에서 모든 "Debug" 값 "릴리스"로 변경 합니다.

7. 솔루션을 빌드합니다. 다음 섹션에서 사용 되는 릴리스 폴더에 파일의 집합을 만듭니다.

배포 된 것 처럼이 테스트:

1. 컴퓨터에 다운로드 한 ISO 셸 (위)를 설치 하는 Contoso를 배포 하는 합니다.

2. 폴더를 만듭니다 \\\Program Files (x86)\\, 하 고 이름을 `Contoso`입니다.

3. ContosoHelpShell 릴리스 폴더에서 내용을 복사 \\\Program Files (x86) \Contoso\ 폴더입니다.

4. 선택 하 여 레지스트리 편집기를 시작 **실행** 에 **시작** 메뉴 및 입력 `Regedit`합니다. 레지스트리 편집기에서 선택 **파일**를 차례로 **가져오기**합니다. ContosoHelpShell 프로젝트 폴더로 이동 합니다. ContosoHelpShell.reg ContosoHelpShell 하위 폴더를 선택 합니다.

5. 콘텐츠 저장소를 만듭니다.

    ISO-셸용 Contoso 콘텐츠 저장소 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 만들기

    에 대 한 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrated Shell C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 폴더 만들기

6. CatalogType.xml 만들고 포함 하는 콘텐츠 저장소 (이전 단계)를 추가 합니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. 다음 레지스트리 키를 추가 합니다.

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath 문자열 값입니다.

    ISO 셸용:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 통합된 셸:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    키: CatalogName 문자열 값입니다. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 설명서입니다. ISO 셸에 대 한 카탈로그의 이름입니다.

8. (택시 및 MSHC MSHA) 콘텐츠를 로컬 폴더로 복사 합니다.

9. Integrated Shell 명령줄 예 콘텐츠 저장소를 테스트 합니다. ISO 셸에 대 한 제품에 맞게 적절히 카탈로그 및 launchingApp 값을 변경 합니다.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. (Contoso 앱 루트)에서 Contoso 응용 프로그램을 시작 합니다. ISO 셸 내에서 선택는 **도움말** 메뉴 항목을 변경 합니다 **도움말 기본 설정 지정** 에 **사용 하 여 로컬 도움말**합니다.

11. 셸 내에서 선택 합니다 **도움말** 메뉴 항목을 한 다음 **도움말 보기**합니다. 로컬 도움말 뷰어를 시작 해야 합니다. **콘텐츠 관리** 탭을 선택합니다. 아래 **설치 원본**를 선택 합니다 **디스크** 옵션 단추입니다. 선택 된 **...**  단추 및 (위의 단계에서 로컬 폴더로 복사) 하는 Contoso 콘텐츠가 포함 된 로컬 폴더로 이동 합니다. HelpContentSetup.msha를 선택 합니다. Contoso는 이제 책 선택에서 책으로 나타납니다. 선택 **추가**를 선택 합니다 **업데이트** 단추 (오른쪽 아래 모서리).

12. Contoso IDE 내에서 F1 기능을 테스트 하 고 F1 키를 선택 합니다.

## <a name="additional-resources"></a>추가 자료

런타임 API를 참조 하세요 [Windows API 도움말](/previous-versions/windows/desktop/helpapi/helpapi-portal)합니다.

API 도움말을 활용 하는 방법에 대 한 자세한 내용은 참조 하세요. [코드 예제에서는 도움말 뷰어](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)합니다.

에 기능 제안을 제출할 수 있습니다 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)합니다.
