---
title: 레거시 언어 서비스의 요약 정보 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc8bfff0903d2ed1554cfd8b3d5b1dcf5cf0fa8a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436651"
---
# <a name="quick-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 빠른 정보
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자 중 하나는 식별자에 캐럿을 배치 하 고 선택 하는 경우 IntelliSense 요약 정보 소스에서 식별자에 대 한 정보를 표시 **요약 정보** 에서 합니다 **IntelliSense** 메뉴 또는 마우스를 보유 합니다. 식별자 위로 커서입니다. 이렇게 하면 식별자에 대 한 정보를 사용 하 여 표시할 도구 설명 합니다. 이 정보는 일반적으로 식별자 형식으로 구성 됩니다. 디버그 엔진 활성 상태인 경우이 정보는 현재 값을 포함할 수 있습니다. 언어 서비스 식별자만 처리 하는 동안 디버그 엔진은 식 값을 제공 합니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 자세한 내용을 알아보려면 참조 [연습: QuickInfo 도구 설명 표시](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)합니다.  
  
> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
 관리 되는 패키지 프레임 워크 (MPF) 언어 서비스 클래스 IntelliSense 요약 정보 도구 설명을 표시 하는 것에 대 한 전체 지원을 제공 합니다. 표시 될 요약 정보 기능을 사용 하는 텍스트를 입력 하면 됩니다.  
  
 호출 하 여 표시할 텍스트를 가져옵니다 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 구문 분석 이유 값을 사용 하 여 메서드 파서 <xref:Microsoft.VisualStudio.Package.ParseReason>합니다. 이 따라서 형식 정보 (또는 빠른 정보 도구 설명에 표시할 적절 한 무엇이)을 가져오려고 파서에 지시 식별자에서 지정한 위치에는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체입니다. 합니다 <xref:Microsoft.VisualStudio.Package.ParseRequest> 에 전달 된 개체가 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드.  
  
 위치까지 모든 파서는 구문 분석 해야 합니다는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 모든 식별자의 형식을 확인할 개체입니다. 그런 다음 파서가 구문 분석 요청 위치 식별자를 가져와야 합니다. 마지막으로, 파서를 해당 식별자를 가진 연결 된 도구 설명 데이터를 전달 해야 합니다는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 해당 개체의 텍스트를 반환할 수 있도록 개체를 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 메서드.  
  
## <a name="enabling-the-quick-info-feature"></a>요약 정보 기능을 사용 하도록 설정  
 설정 요약 정보 기능을 사용 해야 합니다는 `CodeSense` 및 `QuickInfo` 명명 된의 매개 변수는 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>합니다. 이러한 특성을 설정 합니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 고 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> 속성입니다.  
  
## <a name="implementing-the-quick-info-feature"></a>요약 정보 기능은 구현  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스 IntelliSense 요약 정보 작업을 처리 합니다. 때를 <xref:Microsoft.VisualStudio.Package.ViewFilter> 받은 클래스를 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 명령, 클래스를 호출 하 여는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드를 구문 분석 <xref:Microsoft.VisualStudio.Package.ParseReason> 시 캐럿의 위치를 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 명령을 보냈습니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드 파서 다음 지정된 된 위치까지 원본 구문 분석 하 고 다음 요약 정보 도구 설명에 표시할 무엇 인지 확인 하려면 지정된 된 위치에 대 한 식별자를 구문 분석 합니다.  
  
 대부분의 파서 전체 소스 파일의 초기를 구문 분석을 수행 및 결과 구문 분석 트리에 저장 합니다. 전체 구문 분석 될 때 수행 됩니다 <xref:Microsoft.VisualStudio.Package.ParseReason> 넘어갑니다 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드. 다른 유형의 구문 분석은 원하는 정보를 얻으려면 구문 분석 트리를 사용할 수 있습니다.  
  
 예를 들어, 구문 분석 이유 값 <xref:Microsoft.VisualStudio.Package.ParseReason> 형식 정보를 가져오기 위한 구문 분석 트리에 조회 및 원본 위치에서 식별자를 찾을 수 있습니다. 이 형식 정보 전달 되어는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스 및에서 반환 되는 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 메서드.
