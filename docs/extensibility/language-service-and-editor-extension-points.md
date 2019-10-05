---
title: 언어 서비스 및 편집기 확장 지점 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 394ae909121bc2e80dee14506b3c0399956d1b4d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309579"
---
# <a name="language-service-and-editor-extension-points"></a>언어 서비스 및 편집기 확장 지점
편집기에는 대부분의 언어 서비스 기능을 포함 하 여 Framework MEF (Managed Extensibility) 구성 요소 파트로 확장할 수 있는 확장 지점을 제공 합니다. 다음은 이러한 주요 확장 포인트 범주:

- 내용 유형

- 분류 유형 및 분류 형식

- 여백 및 스크롤 막대

- 태그

- 선의 도구 영역

- 마우스 프로세서

- 처리기를 삭제 합니다.

- 옵션

- IntelliSense

## <a name="extend-content-types"></a>콘텐츠 형식 확장
 콘텐츠 유형은 예를 들어 편집기에서 처리 하는 텍스트, "text", "코드" 또는 "CSharp" 종류의 정의입니다. 형식의 변수를 선언 하 여 새 콘텐츠 형식을 정의한 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 및 새 콘텐츠 형식에 고유한 이름을 지정 합니다. 콘텐츠 형식 편집기를 등록 하려면 다음 특성을 함께 내보내기:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 콘텐츠 형식의 이름이입니다.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> 이 콘텐츠 형식 파생 되는 콘텐츠 형식의 이름이입니다. 내용 유형이 다른 여러 콘텐츠 형식에서 상속할 수 있습니다.

  때문에 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 클래스가 봉인 되어 있고, 없는 형식 매개 변수를 사용 하 여 내보낼 수 있습니다.

  다음 예제에서는 콘텐츠 형식 정의에 내보내기 특성을 보여 줍니다.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 콘텐츠 형식은 0 개 이상의 기존 콘텐츠 형식에 기반 할 수 있습니다. 다음은 기본 제공 형식입니다.

- 모든: 기본 콘텐츠 유형입니다. 다른 모든 콘텐츠 형식의 부모입니다.

- 텍스트: 비 프로젝션 콘텐츠에 대 한 기본 형식입니다. "Any"에서 상속 됩니다.

- 일반 텍스트:에 대 한 비 코드 텍스트입니다. "Text"에서 상속 됩니다.

- 코드: 모든 종류의 코드에 대 한 합니다. "Text"에서 상속 됩니다.

- 기호: 모든 유형의 처리에서 텍스트를 제외합니다. 이 콘텐츠 형식의 텍스트에 적용 된 모든 확장을 갖지 않습니다.

- 프로젝션 버퍼의 내용에 대해 프로젝션 합니다. "Any"에서 상속 됩니다.

- Intellisense:에 대 한 IntelliSense의 내용입니다. "Text"에서 상속 됩니다.

- Sighelp: 서명 도움말입니다. "Intellisense"에서 상속 됩니다.

- Sighelp-doc: 서명 도움말 설명서입니다. "Intellisense"에서 상속 됩니다.

  다음은 Visual Studio에서 정의 된 콘텐츠 형식 중 일부와 Visual Studio에서 호스트 되는 언어의 일부입니다.

- Basic

- C/C++

- ConsoleOutput

- CSharp

- CSS

- ENC

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  사용 가능한 콘텐츠 형식의 목록을 검색할 가져오기는 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>를 편집기에 대 한 콘텐츠 형식의 컬렉션을 유지 하는 합니다. 다음 코드는 속성으로이 서비스를 가져옵니다.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 콘텐츠 형식을 파일 이름 확장명을 사용 하 여 연결을 사용 하 여 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>입니다.

> [!NOTE]
> Visual Studio에서 파일 이름 확장명은 사용 하 여 등록을 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> 언어 서비스 패키지에 있습니다. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF content-type이 방식으로 등록 된 파일 이름 확장명을 사용 하 여 연결 합니다.

 파일 이름 확장명에 콘텐츠 형식 정의 내보내려면 다음 특성을 포함 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: 파일 이름 확장명을 지정 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 콘텐츠 형식을 지정 합니다.

  때문에 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 클래스가 봉인 되어 있고, 없는 형식 매개 변수를 사용 하 여 내보낼 수 있습니다.

  다음 예제에서는 콘텐츠 형식 정의를 파일 이름 확장명에 내보내기 특성을 보여 줍니다.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> 파일 이름 확장명 및 콘텐츠 형식 간의 연결을 관리 합니다.

## <a name="extend-classification-types-and-classification-formats"></a>분류 형식 및 형식 분류를 확장 합니다.
 다른 처리 (예: 파란색 "키워드" 텍스트와 "주석" 텍스트를 녹색 색 지정)를 제공 하려는 텍스트의 종류를 정의 하는 분류 유형을 사용할 수 있습니다. 형식의 변수를 선언 하 여 새 분류 유형을 정의 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 및 고유 이름을 지정 합니다.

 편집기를 사용 하 여 분류 유형을 등록 하려면 다음 특성을 함께 내보내기:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 분류 형식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>:이 분류 유형을 상속 된 분류 형식의 이름입니다. 모든 분류 형식은 "text"에서 상속 하 고 분류 유형을 다른 여러 분류 형식에서 상속할 수 있습니다.

  때문에 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 클래스가 봉인 되어 있고, 없는 형식 매개 변수를 사용 하 여 내보낼 수 있습니다.

  다음 예제에서는 분류 형식 정의에 내보내기 특성을 보여 줍니다.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> 표준 분류에 대 한 액세스를 제공 합니다. 기본 제공 분류 유형은 다음과 같습니다.

- "text"

- "자연 언어" ("text"에서 파생 됨)

- "형식 언어" ("text"에서 파생 됨)

- "string" ("literal"에서 파생 됨)

- "character" ("literal"에서 파생 됨)

- "숫자" ("literal"에서 파생 됨)

  상속 하는 다른 오류 형식 집합이 <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>합니다. 다음 오류 유형을 포함 합니다.

- "구문 오류"

- "컴파일러 오류"

- "기타 오류"

- "경고"

  사용 가능한 분류 유형 목록을 검색, 가져오기는 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>를 편집기에 대 한 분류 형식의 컬렉션을 유지 하는 합니다. 다음 코드는 속성으로이 서비스를 가져옵니다.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 새 분류 형식에 대 한 분류 형식 정의 정의할 수 있습니다. 클래스를 파생 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> 형식을 사용 하 여 내보내기 및 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>다음 특성을 함께 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 형식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: 형식의 표시 이름입니다.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: 형식에 표시 되는지 여부를 지정 합니다 **글꼴 및 색** 페이지의 **옵션** 대화 상자.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 우선 순위 형식입니다. 유효한 값은 <xref:Microsoft.VisualStudio.Text.Classification.Priority>합니다.

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>:이 형식으로 매핑되는 분류의 이름을 입력 합니다.

  다음 예제에서는 분류 형식 정의에 내보내기 특성을 보여 줍니다.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 사용 가능한 형식 목록을 검색할 가져오기는 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>를 편집기에 대 한 형식의 컬렉션을 유지 하는 합니다. 다음 코드는 속성으로이 서비스를 가져옵니다.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>여백 및 스크롤 막대를 확장 합니다.
 여백 스크롤 막대와 텍스트 뷰 자체 외에도 편집기의 기본 뷰 요소입니다. 임의 개수의 여백 텍스트 뷰 주위에 표시 된 표준 여백 외에도 제공할 수 있습니다.

 구현 된 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> 여백을 정의 하는 인터페이스입니다. 도 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 여백을 만드는 인터페이스입니다.

 편집기 여백 공급자를 등록 하려면 다음 특성을 함께 공급자를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 여백의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>:는 여백 표시 되는 순서를 다른 여백을 기준으로 합니다.

   다음은 기본 제공 여백입니다.

  - "Wpf 가로 스크롤 막대"

  - "Wpf 세로 스크롤 막대"

  - "Wpf 줄 번호 여백을"

    순서 특성에 있는 가로 여백을 `After="Wpf Horizontal Scrollbar"` 기본 제공 여백과의 순서 특성에 있는 가로 여백 아래에 표시 됩니다 `Before ="Wpf Horizontal Scrollbar"` 기본 여백 위에 표시 됩니다. 오른쪽의 순서 특성에 있는 세로 여백을 `After="Wpf Vertical Scrollbar"` 스크롤 막대의 오른쪽에 표시 됩니다. 왼쪽의 순서 특성에 있는 세로 여백을 `After="Wpf Line Number Margin"` (표시 됨) 하는 경우 줄 번호 여백의 왼쪽에 나타납니다.

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: 여백 (왼쪽, 오른쪽, 위쪽 또는 아래쪽)의 종류입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 콘텐츠 (예: "text" 또는 "code")의 종류에 여백 유효 합니다.

  다음 예제에서는 줄 번호 여백 오른쪽에 표시 되는 여백에 대 한 여백 공급자에서 내보내기 특성을 보여 줍니다.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>태그 확장
 태그는 다른 종류의 텍스트를 사용 하 여 데이터를 연결 하는 방법입니다. 대부분의 경우에서 연결 된 데이터는 시각 효과로 표시 됩니다 했지만 모든 태그를 시각적 표시 합니다. 구현 하 여 사용자 고유의 종류의 태그를 정의할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>합니다. 도 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 지정된 된 텍스트 범위 집합에 대 한 태그를 제공 및 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 태거를 제공 합니다. 다음 특성을 함께 태거 공급자를 내보내기를 수행 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 태그 유효 콘텐츠 (예: "text" 또는 "code")의 종류입니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: 태그의 종류입니다.

  다음 예제에서는 태거 공급자에서 내보내기 특성을 보여 줍니다.

\<CodeContentPlaceHolder > 8</CodeContentPlaceHolder> 태그는 다음과 같은 기본 제공 됩니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: 연결 된는 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>합니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: 연결 된 오류 유형입니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: adornment와 사용 하 여 연결 합니다.

  > [!NOTE]
  > 예는 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>에서 HighlightWordTag 정의 [연습: 텍스트를 강조 표시](../extensibility/walkthrough-highlighting-text.md)합니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: 확장 하거나 개요에서 축소할 수 있는 영역을 사용 하 여 연결 합니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: 텍스트 뷰에서 adornment 차지 하는 공간을 정의 합니다. 장식 공간 협상에 대 한 자세한 내용은 다음 섹션을 참조 하세요.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: 자동 간격 및 장식에 대 한 크기 조정을 제공 합니다.

  찾고 버퍼 및 뷰에 대 한 태그를 사용 하 여 가져오기의 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> 또는 <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>를 제공 하는 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 요청 된 형식의 합니다. 다음 코드는 속성으로이 서비스를 가져옵니다.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>태그 및 MarkerFormatDefinitions
 확장할 수 있습니다는 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 태그의 모양을 정의 하는 클래스입니다. 클래스를 내보내야 (으로 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) 다음과 같은 특성을 사용 하 여:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:이 형식 참조에 사용 되는 이름

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>:이 인해 UI에 표시 하는 형식

  생성자 표시 이름 및 태그의 모양을 정의합니다. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 채우기 색을 정의 하 고 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> 테두리 색을 정의 합니다. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> 지역화할 수 있는 형식 정의의 이름입니다.

  다음은 형식 정의 예입니다.

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 이 형식 정의 태그를 적용 하려면 클래스 (표시 이름 아님)의 이름 특성에 설정 이름을 참조 합니다.

> [!NOTE]
> 예는 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>에서 HighlightWordFormatDefinition 클래스 참조 [연습: 텍스트를 강조 표시](../extensibility/walkthrough-highlighting-text.md)합니다.

## <a name="extend-adornments"></a>선의 도구 영역 확장
 장식은 텍스트 보기에 표시 되는 텍스트에 추가할 수 있습니다 또는 텍스트 자체를 볼 수 있는 시각 효과 정의 합니다. 모든 형식으로 사용자 고유의 adornment를 정의할 수 있습니다 <xref:System.Windows.UIElement>합니다.

 Adornment 클래스에서 선언 해야 합니다는 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>합니다. Adornment 계층에 등록 하려면 다음 특성을 함께 내보내기:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 이름 장식입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: adornment 레이어가 관련 하 여 장식의 순서입니다. 클래스 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 네 가지 기본 계층을 정의 합니다. 선택 영역, 개요, 캐럿을 및 텍스트입니다.

  다음 예제에서는 adornment 계층 정의 내보내기 특성을 보여 줍니다.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 구현 하는 두 번째 클래스를 만들어야 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 처리 하 고 해당 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 장식을 인스턴스화하여 이벤트입니다. 이 클래스는 다음과 같은 특성이 함께 내보내기를 수행 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 콘텐츠 (예: "text" 또는 "code")의 종류는 장식 유효 합니다.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>:이 adornment 유효 텍스트 뷰의 종류입니다. 클래스 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 에 미리 정의 된 텍스트 보기 역할 집합이 있습니다. 예를 들어 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 파일의 텍스트 보기에 주로 사용 됩니다. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 텍스트 뷰는 사용자가 편집 하거나 마우스 및 키보드를 사용 하 여 탐색할 수 있습니다에 사용 됩니다. 예가 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 뷰는 편집기 텍스트 뷰 및 **출력** 창입니다.

  다음 예제에서는 adornment 공급자에 내보내기 특성을 보여 줍니다.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 공간 협상 adornment 텍스트와 동일한 수준에서 공간을 차지 하는 하나입니다. 이 유형의 adornment 만들려면 태그 클래스에서 상속 되는 정의 해야 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, 장식 차지 하는 공간의 크기를 정의 하는 합니다.

 모든 프로그램에서와 마찬가지로 adornment 계층 정의 내보내야 합니다.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 공간 협상 adornment 인스턴스화를 구현 하는 클래스를 만들어야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>를 구현 하는 클래스 외에도 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (다른 유형의 장식와 마찬가지로).

 태거 공급자를 등록 하려면 다음 특성을 함께 내보내기 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 콘텐츠 (예: "text" 또는 "code")의 종류에 adornment 유효 합니다.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: 텍스트 뷰는이 유형의 태그 또는 adornment 유효 합니다. 클래스 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 에 미리 정의 된 텍스트 보기 역할 집합이 있습니다. 예를 들어 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 파일의 텍스트 보기에 주로 사용 됩니다. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 텍스트 뷰는 사용자가 편집 하거나 마우스 및 키보드를 사용 하 여 탐색할 수 있습니다에 사용 됩니다. 예가 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 뷰는 편집기 텍스트 뷰 및 **출력** 창입니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: 태그 또는 사용자가 정의한 adornment의 종류입니다. 두 번째를 추가 해야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 에 대 한 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>합니다.

  다음 예에서는 공간 협상 장식 태그 태거 공급자에 내보내기 특성을 보여 줍니다.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>마우스 프로세서를 확장합니다.
 마우스 입력에 대 한 특수 처리를 추가할 수 있습니다. 상속 되는 클래스를 만들고 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> 처리 하려는 입력에 대 한 마우스 이벤트를 재정의 합니다. 도 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> 의 두 번째 클래스와 함께 내보내야를 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 마우스 처리기 유효 콘텐츠 (예: "text" 또는 "code")의 종류를 지정 하는 합니다.

 다음 예제에서는 마우스 프로세서 공급자에서 내보내기 특성을 보여 줍니다.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>드롭다운 처리기 확장
 구현 하는 클래스를 만들어 특정 종류의 텍스트에 대 한 drop 처리기의 동작을 사용자 지정할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> 하 고 구현 하는 두 번째 클래스 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> 놓기 처리기를 만듭니다. 다음 특성을 함께 놓기 처리기를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>:이 드롭다운 처리기 유효 텍스트 형식입니다. 다음 형식으로 순위가 가장 높은 우선 순위 순서로 처리 됩니다.

  1. 사용자 지정 형식

  2. FileDrop

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. Dif

  7. 로캘

  8. 색상표

  9. PenData

  10. 직렬화 가능

  11. SymbolicLink

  12. Xaml

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. HTML 형식으로

  21. UnicodeText

  22. OEMText

  23. 텍스트

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 놓기 처리기의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 기본 놓기 처리기 전후 놓기 처리기의 순서입니다. Visual Studio에 대 한 기본 놓기 처리기 "DefaultFileDropHandler" 이라고 합니다.

  다음 예제에서는 놓기 처리기 공급자에서 내보내기 특성을 보여 줍니다.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>편집기 옵션 확장
 텍스트 보기에서 특정 범위에서 예를 들어 에서만 유효 하는 옵션을 정의할 수 있습니다. 이 미리 정의 된 옵션이 집합을 제공 하는 편집기: 편집기 옵션, 보기 옵션 및 Windows Presentation Foundation (WPF) 보기 옵션입니다. 이러한 옵션을 확인할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>하십시오 <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, 및 <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>합니다.

 새 옵션을 추가 하려면 이러한 옵션 정의 클래스 중 하나에서 클래스를 파생 합니다.

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  다음 예에서는 부울 값이 있는 옵션 정의 내보내는 방법을 보여 줍니다.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>IntelliSense 확장
 IntelliSense는 구조화 된 텍스트에 대 한 정보를 제공 하는 기능 그룹에 대 한 일반 용어 및 문 완성에 대 한 경우 이러한 기능에는 문 완성, 시그니처 도움말, 요약 정보 및 밖에 light bulbs 포함 됩니다. 문 완성 하면 언어 키워드 또는 멤버 이름을 올바르게 입력 합니다. 서명 도움말 서명 또는 사용자가 방금 입력 메서드에 대 한 시그니처를 표시 합니다. 요약 정보 위에 마우스를 놓을 때 형식 또는 멤버 이름에 대 한 전체 시그니처를 표시 합니다. 전구 번 이름이 변경 된 후 모든 변수의 이름 바꾸기 예를 들어, 특정 컨텍스트에서 특정 식별자에 대 한 추가 작업을 제공 합니다.

 IntelliSense 기능을 디자인은 항상에서 거의 동일 합니다.

- IntelliSense *broker* 전체 프로세스를 담당 합니다.

- IntelliSense *세션* 프레 젠 터와 커밋 또는 선택 취소 트리거에 사이의 이벤트 시퀀스를 나타냅니다. 세션은 일반적으로 일부 사용자 제스처에서 트리거됩니다.

- IntelliSense *컨트롤러* 세션을 시작 및 종료 하는 경우 결정을 담당 합니다. 또한 정보 커밋되어야 때 및 세션을 취소 해야 하는 경우 결정 합니다.

- IntelliSense *원본* 콘텐츠를 제공 하 고 가장 일치 하는 결정 합니다.

- IntelliSense *프레 젠 터* 는 콘텐츠를 표시 하는 일을 담당 합니다.

  대부분의 경우에서 하나 이상의 원본 및 컨트롤러를 제공 하는 것이 좋습니다. 표시를 사용자 지정 하려는 경우에 프레 젠 터를 제공할 수 있습니다.

### <a name="implement-an-intellisense-source"></a>IntelliSense 소스를 구현 합니다.
 소스를 사용자 지정 하려면 다음 원본 인터페이스 중 하나 (또는 이상)를 구현 해야 합니다.

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 위해 되지 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>합니다.

 또한 같은 종류의 공급자를 구현 해야 합니다.

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 위해 되지 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>합니다.

 다음 특성을 함께 공급자를 내보내기를 수행 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:는 원본의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 원본 적용 되는 콘텐츠 (예: "text" 또는 "code")의 종류입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 순서 (다른 원본)에 대해 원본 나타납니다.

- 다음 예제에서는 완료 원본 공급자에 내보내기 특성을 보여 줍니다.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 IntelliSense 원본 구현에 대 한 자세한 내용은 다음 연습을 참조 하세요.

- [연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)

- [연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>IntelliSense 컨트롤러를 구현 합니다.
 컨트롤러를 사용자 지정 하려면 구현 해야 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> 인터페이스입니다. 또한 다음과 같은 특성을 컨트롤러 공급자를 구현 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 컨트롤러의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 컨트롤러 적용 되는 콘텐츠 (예: "text" 또는 "code")의 종류입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 컨트롤러 해야 (다른 컨트롤러)에 대해 표시 되는 순서입니다.

  다음 예제에서는 완료 컨트롤러 공급자에서 내보내기 특성을 보여 줍니다.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 IntelliSense 컨트롤러를 사용 하는 방법에 대 한 자세한 내용은 다음 연습을 참조 하세요.

- [연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)