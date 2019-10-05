---
title: '연습: 문 완성 표시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f117209c8e1d57c64ab53df608fe55ae27f0cff0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312402"
---
# <a name="walkthrough-display-statement-completion"></a>연습: 문 완성 표시
완성 기능을 제공 하려는 식별자를 정의 하 고 다음 완료 세션을 트리거 언어 기반 문 완성을 구현할 수 있습니다. 언어 서비스의 컨텍스트에서 문 완성을 정의 하 고, 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고, 해당 형식만 완성 표시 수 있습니다. 또는 기존 콘텐츠 형식에 대 한 완료를 트리거할 수 있습니다-예를 들어 일반 "텍스트"입니다. 이 연습에서는 텍스트 파일의 콘텐츠 형식인 "일반 텍스트" 콘텐츠 형식에 대 한 문 완성을 트리거하는 방법을 보여 줍니다. "Text" 콘텐츠 형식은 코드 및 XML 파일을 포함 하 여 모든 콘텐츠 형식, 상위 항목입니다.

 문 완성은 일반적으로 특정 문자를 입력 하 여 트리거됩니다-예를 들어, "using"와 같은 식별자의 시작 부분을 입력 하 여 합니다. 가 일반적으로 키를 눌러 해제 합니다 **스페이스바**, **탭**, 또는 **Enter** 커밋을 선택 키입니다. 키 입력에 대 한 명령 처리기를 사용 하 여 문자를 입력할 때 트리거하는 IntelliSense 기능을 구현할 수 있습니다 (합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스) 및 구현 하는 처리기 공급자는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 인터페이스입니다. 구현 완료에 참여 하는 식별자의 목록인 완료 소스를 만드는 데는 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 인터페이스와 완료 원본 공급자 (의 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 인터페이스). 공급자는 프레임 워크 MEF (Managed Extensibility) 구성 요소 파트. 서비스 및 브로커는 원본 및 컨트롤러 클래스 내보내기 및 가져오기에 대 한 책임이-예를 들어 합니다 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, 텍스트 버퍼에 대 한 탐색을 사용 하도록 설정 하는 및 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, 완료 세션의 트리거.

 이 연습에는 하드 코드 된 일련의 식별자 문 완성을 구현 하는 방법을 보여 줍니다. 전체 구현에서 언어 서비스 및 언어 설명서는 해당 콘텐츠를 제공 하는 일을 담당 합니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 있습니다 다운로드 센터에서 Visual Studio SDK를 설치 하지 마세요. Visual Studio 설치에서 선택적 기능으로 포함 되어 있습니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. C# VSIX 프로젝트를 만듭니다. (에 **새 프로젝트** 대화 상자에서 **Visual C# / 확장성**, 한 다음 **VSIX 프로젝트**.) 솔루션의 이름을 `CompletionTest`로 지정합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.

3. 기존 클래스 파일을 삭제합니다.

4. 프로젝트에 다음 참조를 추가 하 고 있는지 확인 하십시오 **CopyLocal** 로 설정 된 `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>구현 완료 원본
 완료 원본이 식별자 집합을 수집 하 고 사용자 식별자의 첫 번째 문자 등 완료 트리거에 때 완료 창에 콘텐츠를 추가 하는 일을 담당 합니다. 이 예제에서는 식별자 및 설명과 하드 코드 된 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 메서드. 대부분의 실제 사용 시 언어의 파서 완성 목록을 채우는 데 토큰을 가져오기 위해 사용할 수 있습니다.

### <a name="to-implement-the-completion-source"></a>완료 소스를 구현 하려면

1. 클래스 파일을 추가하고 이름을 `TestCompletionSource`로 지정합니다.

2. 이러한 가져오기를 추가 합니다.

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. 에 대 한 클래스 선언을 수정할 `TestCompletionSource` 구현 되도록 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Private 필드의 목록 및 텍스트 버퍼를 사용 하는, 소스 공급자 추가 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 개체 (완료 세션에 참가할 식별자에 해당):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. 소스 공급자 및 버퍼를 설정 하는 생성자를 추가 합니다. `TestCompletionSourceProvider` 클래스는 이후 단계에서 정의 됩니다.

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. 구현 된 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 컨텍스트에서 제공 하려는 메서드를 완성을 포함 하는 완료 집합을 추가 하 여 합니다. 각 완료 집합의 집합을 포함 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 완성, 탭 완성 창에 해당 합니다. (Visual Basic 프로젝트에서 완료 창 탭 이름은 **일반적인** 하 고 **모든**.) `FindTokenSpanAtPosition` 메서드는 다음 단계에서 정의됩니다.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. 다음 메서드는 커서의 위치에서 현재 단어를 찾는 데 사용 됩니다.

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. 구현 된 `Dispose()` 메서드:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>구현 완료 원본 공급자
 완료 원본 공급자에는 완료 소스를 인스턴스화하는 MEF 구성 요소 부분입니다.

### <a name="to-implement-the-completion-source-provider"></a>완료 소스 공급자를 구현 하려면

1. 라는 클래스를 추가 `TestCompletionSourceProvider` 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>합니다. 이 클래스를 내보낼을 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "일반"텍스트의 및 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "테스트 완료"입니다.

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. 가져오기는 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, 완료 소스에서 현재 단어를 찾습니다는 합니다.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. 구현 된 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 완료 원본을 인스턴스화 방법입니다.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>완료 명령 처리기 공급자 구현
 완료 명령 처리기 공급자에서 파생 되는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, 텍스트 뷰 생성 이벤트를 수신 하는 뷰를 변환 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>-Visual Studio shell의 명령 체인 명령 추가할 수 있습니다-를 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. 이 클래스는 MEF 내보내기를 이기 때문에 자체 명령 처리기에 필요한 서비스를 가져오는 사용할 수 있습니다.

#### <a name="to-implement-the-completion-command-handler-provider"></a>완료 명령 처리기 공급자를 구현 하려면

1. 이라는 파일을 추가 `TestCompletionCommandHandler`합니다.

2. 다음 using 문을 추가 합니다.

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. 라는 클래스를 추가 `TestCompletionHandlerProvider` 구현 하는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>합니다. 이 클래스를 내보낼를 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "토큰 완료 처리기"는 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "일반 텍스트"의 및 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 의 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. 가져오기는 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>를 변환할 수 있습니다를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 에 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, 및 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 표준 Visual Studio 서비스에 액세스할 수 있는 합니다.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. 구현 된 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 명령 처리기를 인스턴스화하기 위한 메서드를 합니다.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>완료 명령 처리기를 구현 합니다.
 구현 해야 하므로 문 완성 키 입력에 의해 트리거될는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 받고 트리거, 커밋 및 완료 세션을 해제 하는 키 입력을 처리 하는 인터페이스입니다.

#### <a name="to-implement-the-completion-command-handler"></a>완료 명령 처리기를 구현 하려면

1. 라는 클래스를 추가 `TestCompletionCommandHandler` 구현 하는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. 다음 명령 처리기 (하려는 전달할 명령), 텍스트 뷰 (이 통해 다양 한 서비스에 대 한 액세스) 명령 처리기 공급자를 개인 필드를 추가 및 완료 세션:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. 텍스트 뷰 및 공급자 필드를 설정 하 고 명령 체인에 명령을 추가 하는 생성자를 추가 합니다.

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. 구현 된 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 따라 명령을 전달 하 여 메서드:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드를 구현합니다. 이 메서드는 키 입력을 받으면 이러한 작업 중 하나를 수행 해야 합니다.

   - 문자 버퍼에 쓸 수 및 트리거해야 하거나 완료를 필터링 할 수 있습니다. (인쇄 문자가 작업을 수행 합니다.)

   - 가 완료 되 면 커밋 있지만 버퍼에 쓸 문자를 허용 하지 마십시오. (공백 **탭**, 및 **Enter** 완료 세션 표시 되 면이 작업을 수행 합니다.)

   - 명령 다음 처리기에 전달할 수 있습니다. (모든 기타 명령입니다.)

     이 메서드는 UI를 표시할 수 있으므로 호출 <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> automation 컨텍스트에서 호출 되지 않습니다 있도록 합니다.

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. 다음이 코드는 완료 세션을 트리거하는 전용 메서드입니다.

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. 다음 예제에서 구독을 취소 하는 개인 메서드는는 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> 이벤트:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>빌드 및 코드를 테스트 합니다.
 이 코드를 테스트 하려면 CompletionTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.

#### <a name="to-build-and-test-the-completiontest-solution"></a>빌드 및 CompletionTest 솔루션 테스트

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스를 시작 됩니다.

3. 텍스트 파일을 만들고 "추가" 단어가 포함 된 일부 텍스트를 입력 합니다.

4. 입력할 때 먼저 "a"와 "d" 다음 "addition" 및 "조정"를 포함 하는 목록이 표시 됩니다. 또한 선택 되어 있는지 확인 합니다. 다른 "d"를 입력 하면만 "추가"가 이제 선택 목록에 포함 해야 합니다. 키를 눌러 "addition"을 커밋할 수 있습니다 합니다 **스페이스바**를 **탭**, 또는 **Enter** 키 또는 Esc 키 또는 다른 키를 입력 하 여 목록 해제 합니다.

## <a name="see-also"></a>참고자료
- [연습: 파일 이름 확장명에 콘텐츠 형식 링크](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)