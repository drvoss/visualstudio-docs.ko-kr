---
title: '연습: 서명 도움말 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202041"
---
# <a name="walkthrough-displaying-signature-help"></a>연습: 서명 도움말 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

서명 도움말 (라고도 *매개 변수 정보*) 매개 변수 목록 시작 문자 (일반적으로 여는 괄호)를 입력 하는 경우 도구 설명에 메서드의 시그니처를 표시 합니다. 매개 변수 및 매개 변수 구분 기호 (쉼표)를 입력 한 도구 설명 굵게 표시 된 다음 매개 변수를 표시 하도록 업데이트 됩니다. 언어 서비스의 컨텍스트에서 시그니처 도움말를 정의할 수 있습니다 또는 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고 바로 해당 형식에 대 한 시그니처 도움말을 표시할 수 있습니다 또는 기존 콘텐츠 형식 (예: "text")에 대 한 시그니처 도움말를 표시할 수 있습니다. 이 연습에서는 "text" 콘텐츠 형식에 대 한 시그니처 도움말을 표시 하는 방법을 보여 줍니다.  
  
 예를 들어, 특정 문자를 입력 하 여 서명 도움말 트리거됩니다 일반적으로 "(" (괄호) 고 예를 들어 다른 문자를 입력 하 여 해제 ")" (닫는 괄호). 키 입력에 대 한 명령 처리기를 사용 하 여 문자를 입력 하 여 트리거되는 IntelliSense 기능을 구현할 수 있습니다 (합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스) 및 구현 하는 처리기 공급자는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 인터페이스입니다. 시그니처 도움말에 참여 하는 서명의 목록인 시그니처 도움말 원본을 만들려면 구현 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 인터페이스와 구현 하는 소스 공급자는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> 인터페이스입니다. 공급자 프레임 워크 MEF (Managed Extensibility) 구성 요소 이며 서비스 및 브로커, 예를 들어, 원본 및 컨트롤러 클래스 내보내기 및 가져오기에 대 한 책임이 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, 텍스트 버퍼에서 탐색할 수 있는 및 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, 시그니처 도움말 세션의 트리거.  
  
 이 연습에는 하드 코드 된 일련의 식별자에 대 한 시그니처 도움말을 구현 하는 방법을 보여 줍니다. 전체 구현에서 언어는 해당 콘텐츠를 제공 하는 일을 담당 합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-mef-project"></a>MEF 프로젝트 만들기  
  
#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면  
  
1. C# VSIX 프로젝트를 만듭니다. (에 **새 프로젝트** 대화 상자에서 **Visual C# / 확장성**, 한 다음 **VSIX 프로젝트**.) 솔루션의 이름을 `SignatureHelpTest`로 지정합니다.  
  
2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
3. 기존 클래스 파일을 삭제합니다.  
  
4. 프로젝트에 다음 참조를 추가 하 고 있는지 **CopyLocal** 로 설정 된 `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>서명 구현 서명 및 매개 변수 도움말  
 시그니처 도움말 소스는 서명을 기반으로 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>를 구현 하는 매개 변수를 포함 하는 각 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>합니다. 전체 구현에서 언어 설명서에서이 정보를 가져올 수는 있지만이 예제에서는 시그니처는 하드 코드 된.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>시그니처 도움말 서명 및 매개 변수를 구현 하려면  
  
1. 클래스 파일을 추가하고 이름을 `SignatureHelpSource`로 지정합니다.  
  
2. 다음 가져오기를 추가 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. 라는 클래스를 추가 `TestParameter` 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. 모든 속성을 설정 하는 생성자를 추가 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. 속성을 추가 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. 라는 클래스를 추가 `TestSignature` 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. 일부 개인 필드를 추가 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. 필드를 설정 하 고 구독 하는 생성자를 추가 합니다 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 이벤트입니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. 선언 된 `CurrentParameterChanged` 이벤트입니다. 이 이벤트는 서명에서 매개 변수 중 하나에서 사용자가 입력할 때 발생 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. 구현 된 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> 속성을 발생 시킵니다는 `CurrentParameterChanged` 속성 값이 변경 될 때 이벤트.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. 발생 하는 메서드를 추가 합니다 `CurrentParameterChanged` 이벤트입니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. 쉼표 수를 비교 하 여 현재 매개 변수를 계산 하는 메서드를 추가 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 시그니처에서 쉼표 수에 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. 에 대 한 이벤트 처리기를 추가 합니다 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 를 호출 하는 이벤트를 `ComputeCurrentParameter()` 메서드.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 속성을 구현합니다. 이 속성에 저장 된 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 서명을 적용 되는 버퍼에서 텍스트의 범위에 해당 하는 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. 다른 매개 변수를 구현 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>서명 도움말 소스 구현  
 시그니처 도움말 원본이 서명 정보를 제공 하는 집합을 사용 합니다.  
  
#### <a name="to-implement-the-signature-help-source"></a>시그니처 도움말 소스를 구현 하려면  
  
1. 라는 클래스를 추가 `TestSignatureHelpSource` 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. 텍스트 버퍼에 대 한 참조를 추가 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. 텍스트 버퍼 및 시그니처 도움말 소스 공급자를 설정 하는 생성자를 추가 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 메서드를 구현합니다. 이 예제에서는 시그니처는 하드 코드 하지만 전체 구현에서 언어 설명서에서이 정보를 가져오는 경우 있습니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. 도우미 메서드 `CreateSignature()` 단지 설명을 위해 제공 됩니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 메서드를 구현합니다. 이 예제에서는 두 가지 서명, 각각 2 개의 매개 변수가 있습니다. 따라서이 메서드가 필요 하지 않습니다. 둘 이상의 시그니처 도움말 소스를를 사용할 수 있는 완전히 구현에서이 메서드는 우선 순위가 가장 높은 시그니처 도움말 소스 일치 하는 서명이 제공할 수 있는지 여부를 결정 하려면 사용 됩니다. 수 없으면 메서드가 null을 반환 하 고-우선 순위가 가장 높은 원본 일치 항목을 제공 하 라는 메시지가 표시 됩니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Dispose () 메서드를 구현 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>서명 도움말 소스 공급자를 구현합니다.  
 시그니처 도움말 소스 공급자는 프레임 워크 MEF (Managed Extensibility) 구성 요소 파트 내보내기 및 시그니처 도움말 원본을 인스턴스화.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>시그니처 도움말 소스 공급자를 구현 하려면  
  
1. 라는 클래스를 추가 `TestSignatureHelpSourceProvider` 구현 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, 및 사용 하 여 내보내기는 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "텍스트" 및 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 의 Before = "default"입니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. 구현 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> 인스턴스화하여는 `TestSignatureHelpSource`합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>명령 처리기를 구현합니다.  
 시그니처 도움말에 의해 트리거되면 일반적으로 (문자와에서 해제 된는) 문자입니다. 구현 하 여 이러한 키 입력을 처리할 수 있습니다를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 을 받으면 시그니처 도움말 세션을 (알려진된 메서드 이름 앞에 문자와 받으면 세션을 해제는) 문자.  
  
#### <a name="to-implement-the-command-handler"></a>명령 처리기를 구현 하려면  
  
1. 라는 클래스를 추가 `TestSignatureHelpCommand` 구현 하는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. 개인 필드를 추가 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 어댑터 (명령 처리기 체인의 명령 처리기를 추가할 수 있습니다), 텍스트 뷰, 시그니처 도움말 브로커 및 세션을 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, 및 다음 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. 이러한 필드를 초기화 하 고 명령 필터 체인의 명령 필터를 추가 하는 생성자를 추가 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. 구현을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드 시그니처 도움말 세션 명령을 필터를 받을 때 트리거를 (후 받으면 세션을 해제 하 고 알려진된 메서드 이름의 문자는) 세션이 여전히 활성 상태인 동안 문자입니다. 모든 경우에 명령을 전달 됩니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. 구현 된 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드는 항상 명령을 전달 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>서명 도움말 명령을 공급자 구현  
 시그니처 도움말 명령을 구현 하 여 제공할 수 있습니다는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 텍스트 뷰를 만들 때 명령 처리기를 인스턴스화할 수 있습니다.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>시그니처 도움말 명령을 공급자를 구현 하려면  
  
1. 라는 클래스를 추가 `TestSignatureHelpController` 구현 하는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 사용 하 여 내보내기 및 합니다 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>를 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, 및 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. 가져오기는 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (가져오는 데는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>지정는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 개체), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (현재 단어를 찾는 사용), 및 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (시그니처 도움말 세션을 트리거)를 합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. 구현 된 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 인스턴스화하여 메서드는 `TestSignatureCommandHandler`합니다.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
 이 코드를 테스트 하려면 SignatureHelpTest 솔루션 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>빌드 및 SignatureHelpTest 솔루션 테스트  
  
1. 솔루션을 빌드합니다.  
  
2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 인스턴스화됩니다.  
  
3. 텍스트 파일 및 형식 "추가" 단어가 포함 된 일부 텍스트를 여는 괄호를 만듭니다.  
  
4. 여는 괄호를 입력 한 후에 대 한 두 개의 서명의 목록을 표시 하는 도구 설명이 표시 됩니다는 `add()` 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
