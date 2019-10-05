---
title: '검사 목록: 레거시 언어 서비스 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b79afe64aafac473d4fe5d22464998d0c2f0537
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437620"
---
# <a name="checklist-creating-a-legacy-language-service"></a>검사 목록: 레거시 언어 서비스 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음 검사 목록에 대 한 언어 서비스를 만들기 위해 수행 해야 하는 기본 단계를 요약 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 핵심 편집기입니다. 언어 서비스를 통합 하 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 디버그 식 계산기를 만들어야 합니다. 자세한 내용은 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) 에 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)합니다.  
  
## <a name="steps-for-creating-a-language-service"></a>언어 서비스를 만들기 위한 단계  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 인터페이스를 구현합니다.  
  
    - VSPackage, 구현 된 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 언어 서비스를 제공 하는 인터페이스입니다.  
  
    - 언어 서비스를 통합된 개발 환경 (IDE)에 사용할 수 있도록 프로그램 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 구현 합니다.  
  
2. 구현 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 주 언어 서비스 클래스의 인터페이스입니다.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 인터페이스는 핵심 편집기 및 언어 서비스 간의 상호 작용의 시작 지점입니다.  
  
### <a name="optional-features"></a>선택적 기능  
 다음 기능은 선택적 이며 순서에 관계 없이 구현할 수 있습니다. 이러한 기능에는 언어 서비스의 기능을 늘립니다.  
  
- 구문 색 지정  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 인터페이스를 구현합니다. 이 인터페이스의 구현 된 적절 한 색 정보를 반환할 파서 정보가 표시 됩니다.  
  
   합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 메서드가 반환 되는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 인터페이스입니다. 구현 해야 하므로 각 텍스트 버퍼에 대 한 별도 colorizer 인스턴스 만들어집니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 별도로 인터페이스입니다. 자세한 내용은 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)합니다.  
  
- 코드 창  
  
   구현 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 인터페이스는 새 코드 창 만들어질 때 알림을 받을 수 있도록 언어 서비스를 사용 하도록 설정 합니다.  
  
   합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 메서드가 반환 되는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 인터페이스입니다. 언어 서비스를 추가할 수 특수 UI 있는 코드 창을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>합니다. 언어 서비스에 텍스트 뷰 필터를 추가 하는 등 특별 한 처리를 수행할 수도 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>합니다.  
  
- 텍스트 뷰 필터  
  
   언어 서비스의 IntelliSense 문 완성을 제공 하려면 텍스트 뷰 처리할 수 있는 명령 중 일부를 가로채 해야 합니다. 이러한 명령은 가로챌, 다음 단계를 수행 합니다.  
  
  - 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 핸들 편집기 명령과 명령 체인에에서 참여할 수 있습니다.  
  
  - 호출 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 메서드 및 전달에 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 구현 합니다.  
  
  - 호출 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> 메서드를 이러한 명령은 더 이상 전달 되도록 보기에서 분리 하는 경우.  
  
    처리 해야 하는 명령을 제공 되는 서비스에 따라 달라 집니다. 자세한 내용은 [언어 서비스 필터에 대 한 중요 명령](../../extensibility/internals/important-commands-for-language-service-filters.md)입니다.  
  
  > [!NOTE]
  > 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 동일한 개체에서 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스입니다.  
  
- 문 완성   
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 인터페이스를 구현합니다.  
  
   문 완성 명령을 지원 (즉, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 에서 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 인터페이스를 전달는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 인터페이스. 자세한 내용은 [레거시 언어 서비스에서 문 완성](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)합니다.  
  
- 메서드 팁  
  
   구현 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 메서드 팁 창에 대 한 데이터를 제공 하는 인터페이스입니다.  
  
   메서드 데이터 팁 창에 표시할 시기를 파악할 수 있도록 명령을 적절 하 게 처리 하도록 텍스트 뷰 필터를 설치 합니다. 자세한 내용은 [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)합니다.  
  
- 오류 표식  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스를 구현합니다.  
  
   오류를 구현 하는 표식 개체를 만들를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 메서드를 전달를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 오류 표식 개체의 인터페이스.  
  
   일반적으로 각 오류 표식 작업 목록 창에서 항목을 관리합니다.  
  
- 작업 목록 항목  
  
   구현 된 작업 항목 클래스를 제공 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> 인터페이스입니다.  
  
   구현 된 작업 공급자 클래스를 제공 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> 인터페이스 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> 인터페이스입니다.  
  
   구현 된 작업 열거자 클래스를 제공 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> 인터페이스입니다.  
  
   작업 목록에 작업 공급자를 등록 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> 메서드.  
  
   가져올는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 서비스 GUID 사용 하 여 언어 서비스의 서비스 공급자를 호출 하 여 인터페이스 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>합니다.  
  
   작업 항목 개체를 만들고 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> 의 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 있더라도 새 인터페이스 또는 작업을 업데이트 합니다.  
  
- 주석 작업 항목  
  
   사용 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> 인터페이스 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 주석 작업 토큰을 얻기 위해 인터페이스입니다.  
  
   가져올는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> 에서 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> 서비스입니다.  
  
   가져올는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 에서 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> 메서드.  
  
   구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> 토큰 목록에 변경 내용을 수신 대기 하는 인터페이스입니다.  
  
- 개요  
  
   여러 가지 방법으로 개요 표시 지원 합니다. 예를 들어, 지원할 수 있습니다 합니다 **정의 부분만 보이기** 명령, 편집기 제어 개요 영역을 제공 하거나 클라이언트 제어 영역을 지원 합니다. 자세한 내용은 [방법: 레거시 언어 서비스의 확장된 개요 표시 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)합니다.  
  
- 언어 서비스 등록  
  
   언어 서비스를 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md) 하 고 [관리 Vspackage](../../extensibility/managing-vspackages.md)합니다.  
  
- 상황에 맞는 도움말  
  
   다음 방법 중 하나로 편집기 컨텍스트를 제공 합니다.  
  
  - 구현 하 여 텍스트 표식에 대 한 컨텍스트를 제공 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 인터페이스입니다.  
  
  구현 하 여 모든 사용자 컨텍스트를 제공 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
