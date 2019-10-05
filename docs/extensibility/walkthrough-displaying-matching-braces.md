---
title: '연습: 괄호 일치 표시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bbea179eb2140706ee868a8a48215e7f490f57d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312528"
---
# <a name="walkthrough-display-matching-braces"></a>연습: 일치 하는 중괄호를 표시 합니다.
중괄호 일치 하려면 중괄호를 정의 하 고 때 중괄호 중 하나에 캐럿이 여는 중괄호를 텍스트 표식 태그를 추가 하 여 일치 하는 등의 언어 기반 기능을 구현 합니다. 언어의 컨텍스트에서 중괄호를 정의 하 고, 고유한 파일 이름 확장명 및 콘텐츠 형식 정의 하 고, 입력 하거나 기존 콘텐츠 형식 (예: "text")에 태그를 적용 하는 태그를 적용할 수 있습니다. 다음 연습에는 중괄호 일치 하는 "text" 콘텐츠 형식에 대 한 태그를 적용 하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 있습니다 다운로드 센터에서 Visual Studio SDK를 설치 하지 마세요. Visual Studio 설치에서 선택적 기능으로 포함 되어 있습니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Framework MEF (Managed Extensibility) 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. 편집기 분류자 프로젝트를 만듭니다. 솔루션의 이름을 `BraceMatchingTest`로 지정합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.

3. 기존 클래스 파일을 삭제합니다.

## <a name="implement-a-brace-matching-tagger"></a>중괄호 일치 태거 구현
 Visual Studio에서 사용 되는 것을 비슷한 효과 강조 표시 하는 중괄호를 get, 형식의 한 태거 구현 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>합니다. 다음 코드를 모든 중첩 수준에서 중괄호 쌍에 대 한 태거를 정의 하는 방법을 보여 줍니다. 이 예제에서는 중괄호 쌍 및 {} 태거 생성자에서 하지만 관련 중괄호 쌍 언어 사양에 정의 됩니다 전체 언어 구현에서 정의 됩니다.

### <a name="to-implement-a-brace-matching-tagger"></a>태거 일치 하는 중괄호를 구현 하려면

1. 클래스 파일을 추가 하 고 중괄호 이름을 키를 누릅니다.

2. 다음 네임 스페이스를 가져옵니다.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. 클래스를 정의 `BraceMatchingTagger` 에서 상속 되는 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 형식의 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>합니다.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. 텍스트 보기, 소스 버퍼, 현재 스냅숏 시점 및 중괄호 쌍의 집합에 대 한 속성을 추가 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. 태거 생성자에서 속성을 설정 하 고 보기 변경 이벤트를 구독할 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 고 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>입니다. 이 예제에서는 설명을 위해 일치 하는 쌍을 정의 됩니다 생성자에서.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. 일부로 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 구현 TagsChanged 이벤트를 선언 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. 현재 캐럿 위치를 업데이트 하는 이벤트 처리기는 `CurrentChar` 속성과 TagsChanged 이벤트를 발생 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. 구현 된 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 중괄호 또는 이전 문자 경우 Visual Studio와 같이 닫는 중괄호에서 현재 문자가 일치 하도록 메서드의 중괄호 중 하나입니다. 일치 항목이 발견 되 면이 메서드는 두 개의 태그, 여는 중괄호 및 닫는 중괄호에 대 한 하나를 인스턴스화합니다.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. 개인 메서드인 모든 중첩 수준에서 일치 하는 중괄호를 찾습니다. 첫 번째 메서드는 열려 있는 문자를 일치 하는 닫기 문자를 찾습니다.

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. 다음 도우미 메서드는 열려 있는 닫기 문자와 일치 하는 문자를 찾습니다.

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>중괄호 일치 하는 태거 공급자 구현
 한 태거를 구현 하는 것 외에도 구현 하 고 내보내기 태거 공급자도 해야 합니다. 이 경우 콘텐츠 공급자의 형식은 "text"입니다. 따라서 중괄호와 일치 하는 모든 유형의 텍스트 파일에 나타나지만 완전히 구현 중괄호 일치를 특정 콘텐츠 형식에만 적용 됩니다.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>중괄호 일치 하는 태거 공급자를 구현 하려면

1. 상속 되는 태거 공급자를 선언 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>BraceMatchingTaggerProvider, 이름을 고 사용 하 여 내보내기는 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "텍스트" 및 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 의 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>합니다.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. 구현 된 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> BraceMatchingTagger를 인스턴스화하기 위한 메서드를 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>빌드 및 코드를 테스트 합니다.
 이 코드를 테스트 하려면 BraceMatchingTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>빌드 및 BraceMatchingTest 솔루션 테스트

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스를 시작 됩니다.

3. 텍스트 파일을 만들고 일치 하는 중괄호를 포함 하는 일부 텍스트를 입력 합니다.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. 중괄호 앞에 캐럿을 배치 하는 경우 해당 중괄호와 일치 하는 닫는 중괄호 강조 표시 됩니다. 닫는 중괄호 바로 뒤에 커서를 놓습니다는 중괄호와 일치 하는 여는 중괄호는 강조 표시 됩니다.

## <a name="see-also"></a>참고자료
- [연습: 파일 이름 확장명에 콘텐츠 형식 링크](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)