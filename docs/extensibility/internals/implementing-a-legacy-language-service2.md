---
title: 레거시 언어 Service2 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6105f46740dc854f4c498adad5bbd5fe675b41f6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335137"
---
# <a name="implementing-a-legacy-language-service"></a>레거시 언어 서비스 구현
MPF ()에서 관리 되는 패키지 프레임 워크를 사용 하 여 언어 서비스 구현에서 클래스를 파생 해야 합니다는 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 및 다음 추상 메서드 및 속성을 구현 합니다.

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 속성

  이러한 메서드 및 속성의 구현에 대 한 자세한 내용은 아래 해당 섹션을 참조 하십시오.

  추가 기능을 지원 하려면 언어 서비스는 MPF 언어 서비스 클래스 중 하나에서 클래스를 파생 해야 할 수 있습니다. 예를 들어 추가 메뉴 명령을 지원 하기 위해 파생 시켜야에서 클래스를 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스를 재정의 하는 다양 한 메서드를 처리 명령 (참조 <xref:Microsoft.VisualStudio.Package.ViewFilter> 세부 정보에 대 한). <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스는 다양 한 다양 한 클래스의 새 인스턴스를 만드는 호출 되는 메서드를 제공 하며 클래스의 인스턴스를 제공 하려면 적절 한 만들기 메서드를 재정의 합니다. 재정의 해야 하는 예를 들어 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> 의 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 자신만의 인스턴스를 반환 하는 클래스 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스. 자세한 내용은 "사용자 지정 클래스 인스턴스화" 섹션을 참조 하세요.

  언어 서비스는 여러 위치에서 사용 되는 자체 아이콘을 제공할 수도 있습니다. 예를 들어 IntelliSense 완성 목록이 표시 되 면 목록의 각 항목에 연결 된 메서드, 클래스, 네임 스페이스, 속성, 항목을 표시 하는 아이콘 있을 수 있습니다 또는 무엇이 든 해당 언어에 대해 필요한 합니다. 이러한 아이콘을 사용 하는 모든 IntelliSense 목록에는 **탐색 모음**, 및는 **오류 목록** 작업 창. 자세한 내용은 아래 "언어 서비스 이미지" 섹션을 참조 하세요.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences 메서드
 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 의 동일한 인스턴스를 항상 반환 하는 메서드를 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스입니다. 기본을 사용할 수 있습니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 언어 서비스에 대 한 추가 기본 설정을 수행 해야 하는 경우 클래스입니다. MPF 언어 서비스 클래스를 하나 이상 있는지를 가정 자료 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스입니다.

### <a name="example"></a>예제
 일반적인 구현을 보여 주는이 예제는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 메서드. 이 예제에서는 기본 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스입니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>GetScanner 메서드
 인스턴스를 반환 하는이 메서드는 <xref:Microsoft.VisualStudio.Package.IScanner> 줄 기반 파서 또는 토큰 및 해당 형식 및 트리거를 가져오는 데 사용 되는 스캐너를 구현 하는 개체입니다. 이 스캐너는는 <xref:Microsoft.VisualStudio.Package.Colorizer> 더 복잡 한 구문 분석 작업에 궁금할 토큰 유형 및 트리거를 가져오기 위한 스캐너도 사용할 수 있지만 색 지정에 대 한 클래스입니다. 구현 하는 클래스를 제공 해야 합니다 <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스 이므로에서 모든 메서드를 구현 해야 합니다는 <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스입니다.

### <a name="example"></a>예제
 일반적인 구현을 보여 주는이 예제는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드. 합니다 `TestScanner` 구현 클래스는 <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스 (표시 되지 않음).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>ParseSource 메서드
 여러 가지 이유로 수에 따라 소스 파일을 구문 분석 합니다. 이 메서드는 지정 된 된 <xref:Microsoft.VisualStudio.Package.ParseRequest> 특정 구문 분석 작업에서 예상 되는 결과 설명 하는 개체입니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드 토큰 기능 및 범위를 결정 하는 더 복잡 한 파서를 호출 합니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드 중괄호 일치 뿐만 아니라 IntelliSense 작업에 대 한 지원에서 사용 됩니다. 이러한 고급 작업을 지원 하지 않는 경우에 여전히 반환 해야 올바른 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체에 구현 하는 클래스를 만드는 데 필요 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 인터페이스 및 해당 인터페이스의 모든 메서드를 구현 합니다. 모든 메서드에서 null 값을 반환할 수 있지만 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체 자체에 null 값을 아니어야 합니다.

### <a name="example"></a>예제
 최소 구현을 보여 주는이 예제는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드 및 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스를 컴파일하고 실제로 더 많은 고급 기능 중 하나를 지원 하지 않고 함수 언어 서비스를 허용 하는 데 충분 합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Name 속성
 이 속성에는 언어 서비스의 이름을 반환합니다. 언어 서비스 등록 되었을 때 지정 된 동일한 이름 이어야 합니다. 이 이름은 다양 한 위치는 가장 두드러진는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 이름을 레지스트리에 액세스할 수 있는 사용 되는 클래스입니다. 레지스트리 항목 및 키의 이름은 레지스트리의 사용 되므로이 속성에서 반환한 이름을 지역화 되지 해야 합니다.

### <a name="example"></a>예제
 가능한 한 가지 구현을 보여 주는이 예제는 <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 속성입니다. 여기서 이름을 하드 코드 된는: 언어 서비스를 등록 하는 중에 사용할 수 있도록 리소스 파일에서 가져올 실제 이름 (참조 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>사용자 지정 클래스 인스턴스화
 각 클래스의 고유한 버전의 인스턴스를 제공 하는 지정 된 클래스의 다음 메서드를 재정의할 수 있습니다.

### <a name="in-the-languageservice-class"></a>LanguageService 클래스

|메서드|반환 된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|텍스트 보기에 대 한 사용자 지정 추가 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|사용자 지정 문서 속성을 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|지원 합니다 **탐색 모음**합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|코드 조각 서식 파일에서 함수를 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|코드 조각 (이 방법을 일반적으로 재정의 되지 않은)를 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|사용자 지정을 지원 하기는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 구조 (이 방법을 일반적으로 재정의 되지 않은).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|주석 문자를 지정 하 고 메서드 시그니처를 사용자 지정 서식 지정 소스 코드를 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|추가 메뉴 명령을 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|구문 강조 (이 방법을 일반적으로 재정의 되지 않은)를 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|언어 기본 설정에 대 한 액세스를 지원 하 합니다. 이 메서드를 구현 해야 하지만 기본 클래스의 인스턴스를 반환할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|줄에는 토큰의 형식을 식별 하는 데 사용 하는 파서를 제공 합니다. 이 메서드를 구현 해야 하 고 <xref:Microsoft.VisualStudio.Package.IScanner> 에서 파생 되어야 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|기능 및 전체 소스 파일을 전체 범위를 식별 하는 데 사용 하는 파서를 제공 합니다. 이 메서드를 구현 해야 하 고 버전의 인스턴스를 반환 해야 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스입니다. 모든 지원 하려는 경우 구문 강조 표시 됩니다 (필요는 <xref:Microsoft.VisualStudio.Package.IScanner> 에서 반환 된 파서를 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드), 반환 아닌이 방법의 경우 nothing 버전을 수행할 수 있습니다를 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 해당 메서드는 모두 null 값을 반환 하는 클래스.|

### <a name="in-the-source-class"></a>원본 클래스

|메서드|반환 된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|(이 방법을 일반적으로 재정의 되지 않은) IntelliSense 완성 목록 표시를 사용자 지정 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|오류 목록에서 마커를 지원 하기 위한 작업 목록입니다. 특히 지원을 사용 하 여 파일을 열고 오류를 일으킨 줄으로 이동 하는 것 보다 더 뛰어난 기능에 대 한 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense 매개 변수 정보 도구 설명의 표시를 사용자 지정 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|코드 주석 처리를 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|구문 분석 작업 동안 정보를 수집 합니다.|

### <a name="in-the-authoringscope-class"></a>AuthoringScope 클래스

|메서드|반환 된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|예: 멤버 또는 형식 선언의 목록을 제공합니다. 이 메서드를 구현 해야 하지만 null 값을 반환할 수 있습니다. 이 메서드는 유효한 개체를 반환 하는 경우 개체 인스턴스여야 버전의는 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스입니다.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|지정 된 컨텍스트에 대해 메서드 서명의 목록이 표시 됩니다. 이 메서드를 구현 해야 하지만 null 값을 반환할 수 있습니다. 이 메서드는 유효한 개체를 반환 하는 경우 개체 인스턴스여야 버전의는 <xref:Microsoft.VisualStudio.Package.Methods> 클래스입니다.|

## <a name="language-service-images"></a>언어 서비스 이미지
 언어 서비스에서 사용할 수 있도록 아이콘의 목록이 제공 하려면 재정의 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 돌아와 클래스는 <xref:System.Windows.Forms.ImageList> 아이콘을 포함 하 합니다. 기본 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 아이콘의 기본 집합을 로드 합니다. 아이콘을 해야 하는 해당 위치에서 정확한 이미지 인덱스를 지정 하므로 전적으로 사용자는 사용자 고유의 이미지 목록을 정렬 하는 방법입니다.

### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense 완성 목록에 사용 되는 이미지
 IntelliSense 완성 목록에 대 한 이미지 인덱스를 각 항목에 대해 지정 합니다 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 메서드의 <xref:Microsoft.VisualStudio.Package.Declarations> 이미지 인덱스를 제공 하려는 경우 재정의 해야 하는 클래스입니다. 반환 되는 값을 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 메서드를 제공 하는 이미지 목록 인덱스는를 <xref:Microsoft.VisualStudio.Package.CompletionSet> 클래스 생성자 및 즉 동일한 이미지 목록에서 반환 되는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 (변경할 수 있습니다 이미지 목록을 에 대 한 사용 합니다 <xref:Microsoft.VisualStudio.Package.CompletionSet> 재정의 하는 경우는 <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.Source> 다른 이미지 목록을 제공 하는 클래스).

### <a name="images-used-in-the-navigation-bar"></a>탐색 모음에서 사용 되는 이미지
 합니다 **탐색 모음** 형식과 멤버의 목록을 표시 하 고는 빠른 탐색 아이콘을 표시할 수에 대 한 합니다. 이러한 아이콘을 가져오는 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 의 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 및 맞게 재정의할 수 없습니다는 **탐색 모음**합니다. 콤보 상자를 나타내는 목록이 채워지는 때 콤보 상자의 각 항목에 사용 되는 인덱스를 지정 합니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 의 메서드를 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 클래스 (참조 [레거시언어서비스의탐색모음에대한지원](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). 이러한 이미지 인덱스의 버전을 통해 일반적으로 언어 구문 분석기에서 했거나 가져온는 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스입니다. 인덱스를 가져오는 방법을 하는 것은 전적으로 있습니다.

### <a name="images-used-in-the-error-list-task-window"></a>오류 목록 작업 창에서 사용 되는 이미지
 때마다 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드 파서 (참조 [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) 오류가 발생 하 고 해당 오류를 전달 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 클래스 합니다 오류가보고됩니다 **오류 목록** 작업 창. 아이콘 작업 창에 표시 되는 각 항목에 연결할 수 있습니다 및 아이콘에서 반환 된 동일한 이미지 목록에서 제공 되는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스. MPF 클래스의 기본 동작은 오류 메시지를 사용 하 여 이미지를 표시 하지 않으려면입니다. 클래스를 파생 시켜이 동작을 재정의할 수는 있지만 합니다 <xref:Microsoft.VisualStudio.Package.Source> 클래스는 <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> 메서드. 해당 메서드에서 새로 만든 <xref:Microsoft.VisualStudio.Package.DocumentTask> 개체입니다. 해당 개체를 반환 하기 전에 사용할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> 속성에는 <xref:Microsoft.VisualStudio.Package.DocumentTask> 이미지 인덱스를 설정 하는 개체입니다. 다음 예제와 유사한 결과가 표시 됩니다. `TestIconImageIndex` 은 모든 아이콘을 나열 하는이 예제에 해당 하는 열거형입니다. 언어 서비스에서 아이콘을 식별 하는 다른 방식으로 할 수 있습니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>언어 서비스에 대 한 기본 이미지 목록
 기본 MPF 언어 서비스 클래스를 사용 하 여 제공 하는 기본 이미지 목록 보다 일반적인 언어 요소와 연결 된 아이콘의 수를 포함 합니다. 이러한 아이콘 중 대량 내부 공용, 친구, protected, private 및 바로 가기의 액세스 개념에 해당 하는 6 개의 변형 집합이 정렬 됩니다. 예를 들어, public, protected 또는 private 인지에 따라 메서드에 대 한 서로 다른 아이콘이 있습니다.

 다음 열거형 각 아이콘 집합에 대 한 일반적인 이름을 지정 하 고 연결된 된 인덱스를 지정 합니다. 예를 들어 열거형에 따라 지정할 수 있습니다으로 보호 된 메서드에 대 한 이미지 인덱스 `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`합니다. 필요에 따라이 열거형의 이름을 변경할 수 있습니다.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)