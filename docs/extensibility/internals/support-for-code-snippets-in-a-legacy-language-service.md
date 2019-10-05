---
title: 레거시 언어 서비스의 코드 조각에 대 한 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa3bfa86d39bcd430d96c3d71f192e9a69a9400
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322421"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 조각 지원
코드 조각은 소스 파일에 삽입 되는 코드입니다. 코드 조각 자체는 XML 기반 서식 파일 필드 집합이 포함 된 경우 이러한 필드에는 코드 조각이 삽입 되 고 코드 조각 삽입 되는 컨텍스트에 따라 다른 값을 가질 수 후 강조 표시 됩니다. 코드 조각을 삽입 한 후에 즉시 코드 조각 언어 서비스에 서식을 지정할 수 있습니다.

 TAB 키를 사용 하 여 탐색할 수 조각의 필드를 허용 하는 특별 한 편집 모드에서 코드 조각을 삽입 됩니다. 필드는 IntelliSense 스타일 드롭다운 메뉴를 지원할 수 있습니다. 사용자는 ENTER 또는 ESC 키를 입력 하 여 소스 파일에 코드 조각을 커밋합니다. 조각에 대 한 자세한 내용은 참조 하세요 [코드 조각](../../ide/code-snippets.md)합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 자세한 내용을 알아보려면 참조 [연습: 코드 조각 구현](../../extensibility/walkthrough-implementing-code-snippets.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="managed-package-framework-support-for-code-snippets"></a>관리 되는 코드 조각에 대 한 패키지 프레임 워크 지원
 (MPF)에서 관리 되는 패키지 프레임 워크에서 코드 조각을 삽입 하려면 템플릿의 읽을 대부분의 코드 조각 기능을 지원 하 고 편집 모드에 특수 한을 사용 하도록 설정 합니다. 지원을 통해 관리 되는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 클래스입니다.

 경우는 <xref:Microsoft.VisualStudio.Package.Source> 클래스가 인스턴스화되면 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 얻기 위해 호출 됩니다는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 개체 (는 기본 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스는 항상 새 반환 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 각각에 대 한 개체 <xref:Microsoft.VisualStudio.Package.Source> 개체)입니다.

 MPF는 확장 기능을 지원 하지 않습니다. 확장 기능은 코드 조각 템플릿에 포함 된 필드에 배치 될 하나 이상의 값을 반환 하는 명명된 된 함수입니다. 언어에서 반환 된 값은 서비스를 통해 자체는 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 개체입니다. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 개체 확장 기능을 지원 하도록 언어 서비스에 의해 구현 되어야 합니다.

## <a name="providing-support-for-code-snippets"></a>코드 조각에 대 한 지원을 제공합니다.
 코드 조각에 대 한 지원을 사용 하려면 제공 하거나 코드를 설치 해야 하 고 이러한 조각을 삽입 하려면 사용자에 대 한 의미를 제공 해야 합니다. 코드 조각에 대 한 지원을 사용 하도록 설정 하는 방법은 세 가지 단계가 있습니다.

1. 조각 파일을 설치 합니다.

2. 언어 서비스에 대 한 코드 조각을 사용 하도록 설정 합니다.

3. 호출 된 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 개체입니다.

### <a name="installing-the-snippet-files"></a>조각 파일 설치
 언어에 대 한 모든 코드 조각은 파일당 일반적으로 하나의 코드 조각 템플릿 XML 파일에 템플릿으로 저장 됩니다. 코드 조각 템플릿을 사용 하는 XML 스키마에 대 한 내용은 참조 하세요 [코드 조각 스키마 참조](../../ide/code-snippets-schema-reference.md)합니다. 언어 ID를 사용 하 여 각 코드 조각 템플릿은 식별 되며 이 언어 ID 레지스트리에 지정 되 고 배치 됩니다는 `Language` 특성을 \<코드 > 템플릿에 태그입니다.

 코드 조각 템플릿 파일이 저장 되어 있는 두 위치는 일반적으로: 언어를 설치 하는 1) 위치 하 고 2) 사용자의 폴더에 있습니다. 이러한 위치는 레지스트리에 추가 되므로 Visual Studio **코드 조각 관리자** 조각을 찾을 수 있습니다. 사용자의 폴더는 사용자가 만든 조각을 저장 됩니다.

 설치 된 코드 조각 템플릿 파일에 대 한 일반적인 폴더 레이아웃은 다음과 같습니다: *[InstallRoot]* \\ *[TestLanguage]* \Snippets\\ *[LCID*\Snippets 합니다.

 *[InstallRoot]*  언어에 설치 된 폴더입니다.

 *[TestLanguage]*  폴더 이름으로 언어의 이름입니다.

 *[LCID]*  로캘 ID입니다. 이 어떻게 지역화 된 버전의 코드 조각 저장 됩니다. 예를 들어 영어에 대 한 로캘 ID가 1033 이면 따라서 *[LCID]* 1033으로 바뀝니다.

 추가 파일을 제공 해야 하는 인덱스 파일이 며, 일반적으로 SnippetsIndex.xml 또는 ExpansionsIndex.xml (.xml으로 끝나는 유효한 파일을 사용할 수 있음)를 호출 하며 이 파일은 일반적으로에 저장 합니다 *[InstallRoot]* \\ *[TestLanguage]* 폴더 코드 조각 폴더와 언어 ID의 정확한 위치 및 언어의 GUID를 지정 합니다. 코드 조각을 사용 하는 서비스입니다. 인덱스 파일의 정확한 경로 "레지스트리 항목 설치"의 뒷부분에 설명 된 대로 레지스트리에 배치 됩니다. SnippetsIndex.xml 파일의 예는 다음과 같습니다.

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 \<언어 > 언어 ID를 지정 하는 태그 (의 `Lang` 특성) 및 언어 서비스 GUID.

 이 예제에서는 Visual Studio 설치 폴더에 언어 서비스를 설치 했다고 가정 합니다. 사용자의 현재 로캘 id % LCID % 바뀝니다. 여러 \<SnippetDir > 태그를 추가할 수 있습니다 각 로캘과 다른 디렉터리에 대 한 합니다. 또한 코드 조각 폴더 사용 하 여 인덱스 파일에서 식별 된 각 하위 폴더를 포함할 수 있습니다 합니다 \<SnippetSubDir >에 포함 된 태그는 \<SnippetDir > 태그입니다.

 사용자 언어에 대 한 자신의 코드 조각을 만들 수도 있습니다. 이 일반적으로 사용자의 설정 폴더에 저장 예를 들어 *[TestDocs]* \Code 조각\\ *[TestLanguage]* \Test 코드 조각, 여기서 *[TestDocs]* Visual Studio에 대 한 사용자의 설정 폴더의 위치입니다.

 다음 대체 요소에 저장 된 경로에 배치할 수는 \<DirPath > 인덱스 파일의 태그입니다.

|요소|설명|
|-------------|-----------------|
|%LCID%|로캘 id입니다.|
|%InstallRoot%|예를 들어, C:\Program Files\Microsoft Visual Studio 8 Visual Studio에 대 한 루트 설치 폴더입니다.|
|%ProjDir%|현재 프로젝트를 포함 하는 폴더입니다.|
|%ProjItem%|현재 프로젝트 항목을 포함 하는 폴더입니다.|
|%TestDocs%|사용자의 설정 폴더, 예: C:\Documents and Settings 폴더\\ *[username]* documents\visual Studio\8 합니다.|

### <a name="enabling-code-snippets-for-your-language-service"></a>언어 서비스에 대 한 코드 조각 사용
 언어 서비스에 대 한 코드 조각을 추가 하 여 설정할 수 있습니다.는 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> VSPackage 특성 (참조 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md) 세부 정보에 대 한). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> 및 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> 매개 변수는 선택적 이지만 포함 해야 합니다 `SearchPaths` 에 알리기 위해 명명 된 매개 변수를 **코드 조각 관리자** 조각의 위치입니다.

 다음은이 특성을 사용 하는 방법의 예제입니다.

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>확장 공급자를 호출합니다.
 언어 서비스는 삽입이 호출 하는 방식 뿐만 아니라 모든 코드 조각 삽입을 제어 합니다.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>코드 조각에 대 한 확장 공급자를 호출합니다.
 확장 공급자를 호출 하는 방법은 두 가지: 메뉴 명령을 사용 하 여 또는 완성 목록에서 바로 가기를 사용 하 여 합니다.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>메뉴 명령을 사용 하 여 코드 조각 삽입
 메뉴 명령의 사용 하 여 코드 조각을 브라우저를 표시 하려면 메뉴 명령을 추가 하 고이 호출 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 인터페이스는 메뉴 명령에 응답에서 합니다.

1. .Vsct 파일에 명령 및 단추를 추가 합니다. 작업을 수행 하는 지침을 찾을 수 있습니다 [메뉴 명령을 사용 하 여 확장을 만드는](../../extensibility/creating-an-extension-with-a-menu-command.md)합니다.

2. 클래스를 파생 합니다 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스를 재정의 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> 메서드 새 메뉴 명령에 대 한 지원을 나타냅니다. 이 예에서는 메뉴 명령에 항상 사용 하도록 설정 합니다.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. 재정의 <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.ViewFilter> 가져오려고 클래스는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 개체와 호출을 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 개체에서 메서드.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     다음 메서드는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 클래스는 지정 된 순서 대로 Visual Studio에서 코드 조각을 삽입 하는 동안 호출 됩니다.

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     후 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> 메서드가 호출 되 면 코드 조각 삽입 된 및 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 개체는 방금 삽입 된 코드 조각을 수정 하는 데는 특별 한 편집 모드입니다.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>바로 가기를 사용 하 여 코드 조각 삽입
 완성 목록에서 바로 가기의 구현은 메뉴 명령 구현 보다 훨씬 더 복잡 합니다. 먼저 코드 조각 바로 가기 IntelliSense 단어 완성 목록에 추가 해야 합니다. 다음 코드 조각 바로 가기 이름을 완성 결과로 삽입 경우을 검색 해야 합니다. 조각 제목 및 바로 가기 이름을 사용 하 여 경로 가져오려면 해당 정보를 전달 하며는 마지막으로, 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 메서드.

 코드 조각 바로 가기 단어 완성 목록에 추가 하려면 추가할 합니다 <xref:Microsoft.VisualStudio.Package.Declarations> 개체에 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스입니다. 코드 조각 이름으로 바로 가기의 식별할 수 있는지 확인 해야 합니다. 예제를 보려면 [연습: 코드 조각 (레거시 구현)를 설치 목록을 가져오는](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)합니다.

 코드 조각 바로 가기 삽입을 검색할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스입니다. 코드 조각 이름을 소스 파일에 이미 삽입, 때문에 확장을 삽입할 때 제거 해야 합니다. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 메서드는 코드 조각을 삽입 지점에 설명 하는 범위; 소스 파일의 전체 코드 조각 이름을 포함 하는 범위, 해당 이름의 코드 조각으로 대체 됩니다.

 다음은의 버전을 <xref:Microsoft.VisualStudio.Package.Declarations> 바로 가기 이름을 지정 하는 코드 조각 삽입을 처리 하는 클래스입니다. 다른 메서드는 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스 명확성을 위해 생략 되었습니다. 이 클래스의 생성자는 한 <xref:Microsoft.VisualStudio.Package.LanguageService> 개체입니다. 이 버전에서 전달할 수 있습니다는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체 (의 구현 예를 들어 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스 걸릴 수 있습니다를 <xref:Microsoft.VisualStudio.Package.LanguageService> 생성자에서 개체 및 해당 개체에 전달에 `TestDeclarations` 클래스 생성자).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 언어 서비스의 바로 가기 이름을 가져오면 호출한는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> 파일 이름 및 코드 조각 제목을 가져오는 방법입니다. 언어 서비스를 호출 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 의 메서드를 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 코드 조각을 삽입 하는 클래스입니다. 지정 된 순서 대로 Visual Studio에서 다음 방법 이라고는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 코드 조각을 삽입 하는 프로세스 중 클래스:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   언어 서비스에 대해 설치 된 코드 조각 목록 가져오기에 대 한 자세한 내용은 참조 하세요. [연습: 코드 조각 (레거시 구현)를 설치 목록을 가져오는](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)합니다.

## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction 클래스 구현
 확장 기능은 코드 조각 템플릿에 포함 된 필드에 배치 될 하나 이상의 값을 반환 하는 명명된 된 함수입니다. 언어 서비스에서 확장 함수를 지원 하기 위해 클래스에서 파생 해야 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 클래스 및 구현 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> 메서드. 다음 재정의 해야 합니다는 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> 의 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 버전의 새 인스턴스를 반환 하는 클래스는 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 지 원하는 각 확장 함수에 대 한 클래스입니다. 확장 함수에서 가능한 값 목록을 지 원하는 경우 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> 의 메서드는 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 해당 값의 목록을 반환 하는 클래스입니다.

 확장 공급자 초기화 되지 않았습니다. 완전히 확장 함수를 호출 하는 시간을 기준으로 하는 대로 인수를 사용 하거나 다른 필드에 액세스 해야 하는 확장 함수를 편집 가능한 필드를 사용 하 여 연결 되지 않아야 합니다. 결과적으로, 확장 함수 인수 또는 다른 필드의 값을 가져올 수 없는 합니다.

### <a name="example"></a>예제
 간단한 확장 함수를 호출 하는 방법의 예로 `GetName` 구현할 수 있습니다. 이 확장 함수 번호를 추가 하는 기본 클래스 이름을 확장 함수를 인스턴스화할 때마다 (삽입은 각 시간에 해당 하는 관련된 코드 조각).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [코드 조각](../../ide/code-snippets.md)
- [연습: 설치된 코드 조각 목록 가져오기(레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)