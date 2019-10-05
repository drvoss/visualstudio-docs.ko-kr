---
title: '연습: 텍스트를 강조 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d398164e910f7700645c01d26afbc631b1d434bc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693330"
---
# <a name="walkthrough-highlighting-text"></a>연습: 텍스트 강조 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Managed Extensibility Framework (MEF) 구성 요소 파트를 만들어 편집기로 다양 한 시각 효과 추가할 수 있습니다. 이 연습에서는 텍스트 파일에서 현재 단어의 모든 발생을 강조 표시 하는 방법을 보여 줍니다. 단어 텍스트 파일에서 한 번 이상 발생 하 고 한 번에 캐럿을 배치 하는 경우 모든 강조 표시 됩니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-mef-project"></a>MEF 프로젝트 만들기  
  
1. C# VSIX 프로젝트를 만듭니다. (에 **새 프로젝트** 대화 상자에서 **Visual C# / 확장성**, 한 다음 **VSIX 프로젝트**.) 솔루션의 이름을 `HighlightWordTest`로 지정합니다.  
  
2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
3. 기존 클래스 파일을 삭제합니다.  
  
## <a name="defining-a-textmarkertag"></a>TextMarkerTag 정의  
 하위 텍스트를 강조 표시 하는 첫 번째 단계는 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 모양을 정의 합니다.  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>TextMarkerTag 및 MarkerFormatDefinition를 정의 하려면  
  
1. 클래스 파일을 추가 하 고 이름을 **HighlightWordTag**합니다.  
  
2. 다음 참조를 추가 합니다.  
  
    1. Microsoft.VisualStudio.CoreUtility  
  
    2. Microsoft.VisualStudio.Text.Data  
  
    3. Microsoft.VisualStudio.Text.Logic  
  
    4. Microsoft.VisualStudio.Text.UI  
  
    5. Microsoft.VisualStudio.Text.UI.Wpf  
  
    6. System.ComponentModel.Composition  
  
    7. Presentation.Core  
  
    8. Presentation.Framework  
  
3. 다음 네임 스페이스를 가져옵니다.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4. 상속 되는 클래스를 만듭니다 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 하 고 이름을 `HighlightWordTag`입니다.  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5. 상속 되는 두 번째 클래스를 만들고 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, HighlightWordFormatDefinition 이라는 이름을 지정 합니다. 이 형식 정의 태그를 사용 하려면 다음과 같은 특성을 사용 하 여 내보내기 해야 합니다.  
  
    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 태그를 사용 하 여이이 형식 참조  
  
    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>:이 인해 UI에 표시 하는 형식  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6. HighlightWordFormatDefinition에 대 한 생성자에서 해당 표시 이름 및 모양을 정의 합니다. Background 속성이 Foreground 속성 테두리 색을 정의 하는 동안 채우기 색을 정의 합니다.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7. HighlightWordTag에 대 한 생성자에서 방금 만든 형식 정의 이름을 전달 합니다.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>ITagger 구현  
 다음 단계를 구현 하는 것은 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 인터페이스입니다. 이 인터페이스는 다른 시각 효과 지정 된 텍스트 버퍼, 텍스트 강조 표시를 제공 하는 태그를 할당 합니다.  
  
#### <a name="to-implement-a-tagger"></a>태거를 구현 하려면  
  
1. 구현 하는 클래스를 만듭니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 형식의 `HighlightWordTag`, 하 고 이름을 `HighlightWordTagger`입니다.  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2. 클래스에 다음 private 필드 및 속성을 추가 합니다.  
  
    - <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, 현재 텍스트 보기에 해당 합니다.  
  
    - <xref:Microsoft.VisualStudio.Text.ITextBuffer>, 텍스트 뷰의 기반이 되는 텍스트 버퍼에 해당 합니다.  
  
    - <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, 텍스트를 찾기 위해 사용 되는 합니다.  
  
    - <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, 텍스트 범위 내에서 탐색 하기 위한 메서드가입니다.  
  
    - <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>를 강조 표시 하는 단어 집합을 포함 하는 합니다.  
  
    - <xref:Microsoft.VisualStudio.Text.SnapshotSpan>을 현재 단어에 해당 합니다.  
  
    - <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, 캐럿의 현재 위치에 해당 합니다.  
  
    - 잠금 개체입니다.  
  
    ```csharp  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3. 앞에 나열 된 속성을 초기화 하 고 추가 하는 생성자를 추가 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 고 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 이벤트 처리기입니다.  
  
    ```csharp  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4. 둘 다 호출 하는 이벤트 처리기는 `UpdateAtCaretPosition` 메서드.  
  
    ```csharp  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5. 추가 해야는 `TagsChanged` update 메서드에서 호출 되는 이벤트입니다.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs#10)]
     [!code-vb[VSSDKHighlightWordTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb#10)]  
  
6. 합니다 `UpdateAtCaretPosition()` 메서드는 커서 위치가 않았고 목록을 생성 단어와 동일한 텍스트 버퍼의 모든 단어를 찾습니다 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 단어의 발생 횟수에 해당 하는 개체입니다. 그런 다음 호출 `SynchronousUpdate`를 발생 시키는 `TagsChanged` 이벤트입니다.  
  
    ```csharp  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7. `SynchronousUpdate` 에서 동기 업데이트를 수행 합니다 `WordSpans` 및 `CurrentWord` 속성 및 발생을 `TagsChanged` 이벤트.  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8. 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 메서드. 이 메서드는 컬렉션 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 개체 및 태그 범위의 열거형을 반환 합니다.  
  
     C#에서 태그의 지연 계산 (즉, 개별 항목을 액세스 하는 경우에 집합이 평가)을 사용 하도록 설정 하는 yield 반복기로이 메서드를 구현 합니다. Visual basic의 경우 목록에 태그를 추가 하 고 목록을 반환 합니다.  
  
     메서드가 반환 되는 여기를 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> "blue"를 가진 개체를 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, 파란색 배경을 제공 하는 합니다.  
  
    ```csharp  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>태거 공급자 만들기  
 구현 해야 하 태거를 만들려면를 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>입니다. 이 클래스는 MEF 구성 요소 부분 이므로이 확장을 인식할 수 있도록 올바른 특성을 설정 해야 합니다.  
  
> [!NOTE]
> MEF에 대 한 자세한 내용은 참조 하세요. [Framework MEF (Managed Extensibility)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)합니다.  
  
#### <a name="to-create-a-tagger-provider"></a>태거 공급자를 만들려면  
  
1. 라는 클래스를 만듭니다 `HighlightWordTaggerProvider` 구현 하는 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, 및 사용 하 여 내보내기는 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"와 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 의 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>합니다.  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2. 두 개의 편집기 서비스를 가져와야 합니다 <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> 및 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, 태거를 인스턴스화할 수입니다.  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3. 구현 된 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 의 인스턴스를 반환 하는 방법 `HighlightWordTagger`합니다.  
  
    ```csharp  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
 이 코드를 테스트 하려면 HighlightWordTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>빌드 및 HighlightWordTest 솔루션 테스트  
  
1. 솔루션을 빌드합니다.  
  
2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 인스턴스화됩니다.  
  
3. 텍스트 파일을 만들고 예를 들어, "hello hello hello" 단어 반복 되는 일부 텍스트를 입력 합니다.  
  
4. "Hello"의 항목 중 하나를 사용 하는 커서를 이동 합니다. 모든 파란색에서 강조 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
