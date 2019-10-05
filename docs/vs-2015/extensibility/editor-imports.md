---
title: 편집기 가져오기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1fc32d0126d912acab104ecefe3cb62d80b8513f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690311"
---
# <a name="editor-imports"></a>편집기 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기 서비스, 팩터리 및 핵심 편집기를 다양 한 종류의 액세스를 사용 하 여 확장을 제공 하는 브로커의 숫자를 가져올 수 있습니다. 예를 들어, 가져올 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 을 제공 하기는 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 지정된 된 콘텐츠 형식에 대 한 합니다. (이 검색기 허용 텍스트 버퍼에서 다른 유형의 검색을 수행 합니다.)  
  
 편집기 가져오기를 사용 하려면 가져올 있습니다 필드 또는 Managed Extensibility Framework 구성 요소 파트를 내보내는 클래스의 속성으로.  
  
> [!NOTE]
> Managed Extensibility Framework에 대 한 자세한 내용은 참조 하세요. [Framework MEF (Managed Extensibility)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)합니다.  
  
## <a name="import-syntax"></a>가져오기 구문  
 다음 예제에서는 편집기를 가져오는 방법 옵션 팩터리 서비스를 보여 줍니다.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 필드와 속성이 아니라 서비스를 가져오려는 경우 설정 해야 `null` 없습니다 변수에 할당 하는 방법에 대 한 컴파일러 경고가 표시 되지 않도록 하기 위해 선언에서:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 가져오기를 사용 하 여 더 많은 예제를 다음 연습을 참조 합니다.  
  
 [연습: 여백 문자 모양 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [연습: 텍스트 보기 사용자 지정](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [연습: 텍스트 강조 표시](../extensibility/walkthrough-highlighting-text.md)  
  
 [연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [연습: 시그니처 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [연습: 스마트 태그 표시](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>서비스 공급자 가져오기  
 가져올 수도 있습니다는 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (Microsoft.VisualStudio.Shell.Immutable.10.0 어셈블리에 있음) Visual Studio 서비스에 액세스 하는 동일한 방식으로:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 [연습: 편집기 확장에서 DTE 개체 액세스](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) 자세한 내용은 합니다.  
  
## <a name="services"></a>서비스  
 편집기 서비스는 서비스를 제공 하 고 여러 구성 요소 간에 공유 되는 일반적으로 단일 엔터티입니다.  
  
|가져오기|제공|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|파일 확장명 간의 관계 및 <xref:Microsoft.VisualStudio.Utilities.IContentType> 개체입니다.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 개체의 컬렉션입니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> 개체|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|많은 편집기 어댑터 개체:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> 지정 된 텍스트 보기에 대 한 개체입니다.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>입니다.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>입니다.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> 차이점입니다.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> 차이점입니다.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> 요소나 <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> 집합이 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 개체입니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 에 대 한는 <xref:Microsoft.VisualStudio.Text.ITextBuffer>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|컬렉션을 유지 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 개체입니다.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 텍스트 버퍼에 대 한 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 텍스트 보기에 대 한 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> 지정된 된 범위에 대 한 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> 텍스트 보기에 대 한 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|자동 들여쓰기를 가져옵니다는 <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> 개체입니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|관리 하는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>입니다.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|스냅숏 범위의 집합에서 RTF 서식 있는 텍스트를 생성합니다.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|<xref:System.Windows.Media.TextFormatting.TextParagraphProperties> 뷰의 텍스트 줄의 서식을 지정 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> 개체는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|텍스트 스냅숏을 검색합니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 에 대 한는 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 여 <xref:Microsoft.VisualStudio.Utilities.IContentType>입니다.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> 텍스트 보기에 대 한 합니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|문자 모양의 표준 집합입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|추적 키보드 처리 합니다.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|표준 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 개체입니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|텍스트 버퍼 간에 관계를 유지 관리 및 <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> 개체입니다.|  
  
## <a name="other-imports"></a>다른 가져오기  
 공급자 팩터리 및 브로커는 일반적으로 여러 구성 요소에서 여러 인스턴스를 가질 수 있는 엔터티입니다.  
  
|가져오기|제공|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> 형식의 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) 지정된 된 버퍼에 대 한 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|텍스트 마커 태거 (한 <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> 형식의 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> 에 지정 된 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>합니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
