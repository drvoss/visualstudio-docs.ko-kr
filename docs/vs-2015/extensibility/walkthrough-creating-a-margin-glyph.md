---
title: '연습: 여백 모양 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148854"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>연습: 여백 문자 모양 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 편집기 확장을 사용 하 여 편집기 여백의 모양을 사용자 지정할 수 있습니다. 이 연습에서는 "todo" 라는 단어 코드 주석 안에 나타날 때마다 표시기 여백에 사용자 지정 문자 모양을 배치 합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-mef-project"></a>MEF 프로젝트 만들기  
  
1. C# VSIX 프로젝트를 만듭니다. (에 **새 프로젝트** 대화 상자에서 **Visual C# / 확장성**, 한 다음 **VSIX 프로젝트**.) 솔루션의 이름을 `TodoGlyphTest`로 지정합니다.  
  
2. 편집기 분류자 프로젝트 항목을 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
3. 기존 클래스 파일을 삭제합니다.  
  
## <a name="defining-the-glyph"></a>문자 모양 정의  
 문자 모양을 구현 하 여 정의 된 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 인터페이스입니다.  
  
#### <a name="to-define-the-glyph"></a>문자 모양을 정의 하려면  
  
1. 클래스 파일을 추가하고 이름을 `TodoGlyphFactory`로 지정합니다.  
  
2. 다음 추가 선언을 사용 하 여 합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. 라는 클래스를 추가 `TodoGlyphFactory` 구현 하는 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. 기호의 크기를 정의 하는 개인 필드를 추가 합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. 구현 `GenerateGlyph` 문자 모양 사용자 인터페이스 (UI) 요소를 정의 하 여 합니다. `TodoTag` 이 연습의 뒷부분에서 정의 됩니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. 라는 클래스를 추가 `TodoGlyphFactoryProvider` 구현 하는 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>합니다. 이 클래스를 내보낼을 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph"의 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> VsTextMarker 후의 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "코드" 및 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag의 합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. 구현 된 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 인스턴스화하여 메서드는 `TodoGlyphFactory`합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Todo 태그 및 태거 정의  
 태그 형식 및 태거를 만들고 태거 공급자를 사용 하 여 내보내기 하 여 이전 단계에서 정의한 UI 요소와 표시기 여백 사이의 관계를 정의 합니다.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Todo 태그 및 태거를 정의 하려면  
  
1. 새 클래스 파일을 프로젝트에 추가 하 고 이름을 `TodoTagger`입니다.  
  
2. 다음 가져오기를 추가 합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. 라는 클래스를 추가 `TodoTag`합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. 라는 클래스를 수정 `TodoTagger` 구현 하는 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 형식의 `TodoTag`합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. 에 `TodoTagger` 클래스를 private 필드에 대 한 추가 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 분류에서 찾을 텍스트에 대 한 확장 및 합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. 분류자를 설정 하는 생성자를 추가 합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. 구현 된 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 분류를 검색 하 여 메서드 이름에 포함 된 단어 "comment" 및 검색 텍스트를 포함 하는 텍스트가 포함 됩니다. 검색 텍스트가 발견 되 때마다 새 다시 생성 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 형식의 `TodoTag`합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. 선언 된 `TagsChanged` 이벤트입니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. 라는 클래스를 추가 `TodoTaggerProvider` 구현 하는 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, 및 사용 하 여 내보내기는 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "코드"와 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag의 합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. 가져오기는 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. 구현 된 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 인스턴스화하여 메서드는 `TodoTagger`합니다.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
 이 코드를 테스트 하려면 TodoGlyphTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>빌드 및 TodoGlyphTest 솔루션 테스트  
  
1. 솔루션을 빌드합니다.  
  
2. F5 키를 눌러 프로젝트를 실행 합니다. Visual Studio의 두 번째 인스턴스가 인스턴스화됩니다.  
  
3. 표시기 여백 표시 되어 있는지 확인 합니다. (에 **도구** 메뉴에서 클릭 **옵션**합니다. 에 **텍스트 편집기** 페이지에서 확인 **표시기 여백** 을 선택 합니다.)  
  
4. 주석이 있는 코드 파일을 엽니다. 주석 섹션 중 하나에 "todo" 라는 단어를 추가 합니다.  
  
5. 표시기 여백 코드 창의 왼쪽에 진한 파란색 윤곽선으로 밝은 파란색 원을 표시 됩니다.
