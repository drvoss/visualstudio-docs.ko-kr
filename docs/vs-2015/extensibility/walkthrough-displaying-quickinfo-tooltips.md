---
title: '연습: QuickInfo 도구 설명 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79ce531d36b21ab26cf4c6e6dc76e8c4d98d8763
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58984316"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>연습: QuickInfo 도구 설명 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요약 정보 기능은 IntelliSense 메서드 시그니처를 표시 하는 메서드 이름 위로 포인터를 이동 하는 경우 사용자 설명 하며 QuickInfo 설명을 제공 하려면 식별자를 정의 하 고 콘텐츠를 표시 하는 도구 설명을 만드는 QuickInfo 같은 언어 기반 기능을 구현할 수 있습니다. 언어 서비스의 컨텍스트에서 QuickInfo를 정의할 수 있습니다 또는 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고 바로 해당 형식에 대 한 요약 정보를 표시할 수 있습니다 또는 기존 콘텐츠 형식 (예: "text")에 대 한 요약 정보를 표시할 수 있습니다. 이 연습에서는 "text" 콘텐츠 형식에 대 한 요약 정보를 표시 하는 방법을 보여 줍니다.  
  
 이 연습의 QuickInfo 예제 메서드 이름을 위로 포인터를 이동할 때 도구 설명을 표시 합니다. 이 디자인에서는 이러한 네 가지 인터페이스를 구현 해야 합니다.  
  
- 소스 인터페이스  
  
- 원본 공급자 인터페이스  
  
- 컨트롤러 인터페이스  
  
- 컨트롤러 공급자 인터페이스  
  
  원본 및 컨트롤러 공급자 Framework MEF (Managed Extensibility) 구성 요소 부분으로 된 원본 및 컨트롤러 클래스 내보내기에 대 한 책임이 고 가져오기 서비스 broker와 같은 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, 도구 설명 텍스트를 만듭니다 버퍼 및 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, 작업을 트리거하는 QuickInfo 세션입니다.  
  
  이 예제에서는 QuickInfo 원본 목록을 사용 하 여 하드 코드 된 메서드 이름 및 설명 하지만 전체 구현 언어 서비스 및 언어 설명서에는 해당 콘텐츠를 제공 하는 일을 담당 합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-mef-project"></a>MEF 프로젝트 만들기  
  
#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면  
  
1.  C# VSIX 프로젝트를 만듭니다. (에 **새 프로젝트** 대화 상자에서 **Visual C# / 확장성**, 한 다음 **VSIX 프로젝트**.) 솔루션의 이름을 `QuickInfoTest`로 지정합니다.  
  
2.  편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
3.  기존 클래스 파일을 삭제합니다.  
  
## <a name="implementing-the-quickinfo-source"></a>QuickInfo 소스 구현  
 QuickInfo 소스는 식별자 및 해당 설명의 집합을 수집 하 고 식별자 중 하나가 발생할 때 도구 설명 텍스트 버퍼에 콘텐츠를 추가 하는 일을 담당 합니다. 이 예제에서는 식별자 및 설명과 원본 생성자에 추가 됩니다.  
  
#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo 소스를 구현 하려면  
  
1.  클래스 파일을 추가하고 이름을 `TestQuickInfoSource`로 지정합니다.  
  
2.  Microsoft.VisualStudio.Language.IntelliSense에 대 한 참조를 추가 합니다.  
  
3.  다음 가져오기를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  구현 하는 클래스 선언 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>, 하 고 이름을 `TestQuickInfoSource`입니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  QuickInfo 소스 공급자 및 텍스트 버퍼 메서드 이름 및 메서드 시그니처 집합에 대 한 필드를 추가 합니다. 이 예제에서는 메서드 이름 및 시그니처가 초기화 됩니다는 `TestQuickInfoSource` 생성자입니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  QuickInfo 소스 공급자와 텍스트 버퍼를 설정 하 고 메서드 이름 및 메서드 시그니처 및 설명의 집합을 채우는 생성자를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 메서드를 구현합니다. 이 예제에서는 메서드 커서가 선이나 텍스트 버퍼의 끝에 있는 경우 현재 단어 또는 이전 단어 찾습니다. 단어를 사용 하면 메서드 이름 중 하나인 경우 해당 메서드 이름에 대 한 설명은 QuickInfo 내용에 추가 됩니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  도 구현 해야 dispose () 메서드를 이후에 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> 구현 <xref:System.IDisposable>:  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>QuickInfo 소스 공급자 구현  
 QuickInfo 원본의 공급자 자체 MEF 구성 요소 부분으로 내보내고 QuickInfo 원본을 인스턴스화를 주로 사용 됩니다. MEF 구성 요소 일부 이기 때문에 다른 MEF 구성 요소 파트를 가져오면 합니다.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo 소스 공급자를 구현 하려면  
  
1.  라는 QuickInfo 소스 공급자를 선언 `TestQuickInfoSourceProvider` 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>, 및 사용 하 여 내보내기는 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "원본 QuickInfo 도구 설명"는 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 의 Before = "default" 및 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"입니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  두 개의 편집기 서비스를 가져올 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 하 고 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>의 속성으로 `TestQuickInfoSourceProvider`입니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  구현 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> 새 반환할 `TestQuickInfoSource`합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>QuickInfo 컨트롤러 구현  
 QuickInfo 컨트롤러 QuickInfo 표시할 경우를 결정 합니다. 이 예제에서는 QuickInfo 포인터를 메서드 이름 중 하나에 해당 하는 단어 위로 가져갈 때 표시 됩니다. QuickInfo 컨트롤러 QuickInfo 세션을 트리거하는 마우스 가리키기 이벤트 처리기를 구현 합니다.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo 컨트롤러를 구현 하려면  
  
1.  구현 하는 클래스 선언 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>, 하 고 이름을 `TestQuickInfoController`입니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  텍스트 보기, QuickInfo 세션 QuickInfo 컨트롤러 공급자의 표시 텍스트 버퍼 텍스트 보기에 대 한 전용 필드를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  필드를 설정 하 고 마우스 가리키기 이벤트 처리기를 추가 하는 생성자를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  QuickInfo 세션을 트리거하는 마우스 가리키기 이벤트 처리기를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  구현 된 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> 메서드는 컨트롤러 텍스트 보기에서 분리 되 면 마우스 가리키기 이벤트 처리기를 제거 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  구현 된 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> 메서드 및 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> 예를 빈 메서드로 메서드.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo 컨트롤러 공급자 구현  
 QuickInfo 컨트롤러의 공급자 자체 MEF 구성 요소 부분으로 내보내고 QuickInfo 컨트롤러를 인스턴스화하고에 주로 사용 됩니다. MEF 구성 요소 일부 이기 때문에 다른 MEF 구성 요소 파트를 가져오면 합니다.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo 컨트롤러가 공급자를 구현 하려면  
  
1.  이라는 클래스를 선언 `TestQuickInfoControllerProvider` 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>, 및 사용 하 여 내보내기는 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "도구 설명 QuickInfo 컨트롤러" 및 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>를 속성으로 가져옵니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  구현 된 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> 메서드 QuickInfo 컨트롤러를 인스턴스화합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
 이 코드를 테스트 하려면 QuickInfoTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>빌드 및 QuickInfoTest 솔루션 테스트  
  
1.  솔루션을 빌드합니다.  
  
2.  디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 인스턴스화됩니다.  
  
3.  텍스트 파일 형식 단어를 포함 하는 일부 텍스트 "추가" 및 "제거"를 만듭니다.  
  
4.  "추가"의 항목 중 하나 위로 포인터를 이동 합니다. 서명 및 설명의 `add` 메서드를 표시 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
