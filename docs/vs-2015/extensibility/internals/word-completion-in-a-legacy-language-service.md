---
title: 레거시 언어 서비스의 완료를 word | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8b4449a30119d925b167213141c3ba577ce42609
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439887"
---
# <a name="word-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 단어 완성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

단어 완성 단어를 부분적으로 입력 한 후에 누락 된 문자를 채웁니다. 하나의 가능한 완료의 경우 단어 완성 문자 입력 되 면 완료 됩니다. 한 부분 단어에 둘 이상의 가능성 일치 하는 경우 가능한 완성 목록이 표시 됩니다. 완성 문자는 식별자에 대 한 사용 되지 않는 모든 문자를 수 있습니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)합니다.  
  
> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
## <a name="implementation-steps"></a>구현 단계  
  
1. 사용자가 선택 하는 경우 **단어 자동 완성** 에서 합니다 **IntelliSense** 메뉴는 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 명령 언어 서비스로 전송 됩니다.  
  
2. <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스 명령 및 호출을 catch 합니다 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 메서드를 구문 분석 <xref:Microsoft.VisualStudio.Package.ParseReason>합니다.  
  
3. <xref:Microsoft.VisualStudio.Package.Source> 호출을 다음 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 가능한 단어 완성 및 도구 설명에 있는 단어를 사용 하 여 목록을 표시 하는 목록을 가져오기 위한 메서드를를 <xref:Microsoft.VisualStudio.Package.CompletionSet> 클래스입니다.  
  
    하나의 일치 하는 word, 없는 경우는 <xref:Microsoft.VisualStudio.Package.Source> 는 단어를 완성 하는 클래스입니다.  
  
   또는 스캐너 트리거 값을 반환 하는 경우 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 식별자의 첫 번째 문자를 입력할 때 합니다 <xref:Microsoft.VisualStudio.Package.Source> 클래스는이 검색 하 고 호출 합니다 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 메서드를 구문 분석 <xref:Microsoft.VisualStudio.Package.ParseReason>합니다. 이 경우 파서에서 문자를 멤버 선택의 존재를 검색 하 고 멤버의 목록을 제공 해야 합니다.  
  
## <a name="enabling-support-for-the-complete-word"></a>단어 자동 완성에 대 한 지원을 사용 하도록 설정  
 단어 완성 집합에 대 한 지원을 사용 하도록 설정 합니다 `CodeSense` 명명 된 매개 변수를 전달 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 언어 패키지와 관련 된 사용자 특성입니다. 이 설정의 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 속성에는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스입니다.  
  
 프로그램 파서 선언의 목록을 응답을 구문 분석 이유 값을 반환 해야 합니다 <xref:Microsoft.VisualStudio.Package.ParseReason>를 작동 하는 단어 완성에 대 한 합니다.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>단어 자동 완성 ParseSource 메서드 구현  
 단어 완성에 대 한 합니다 <xref:Microsoft.VisualStudio.Package.Source> 클래스를 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 가능한 단어 일치 항목의 목록을 구하는 클래스. 목록에서 파생 된 클래스에서 구현 해야 합니다는 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스입니다. 참조 된 <xref:Microsoft.VisualStudio.Package.Declarations> 구현 해야 하는 방법에 대 한 세부 정보에 대 한 클래스입니다.  
  
 목록에 한 단어를 포함 하는 경우 해당 <xref:Microsoft.VisualStudio.Package.Source> 클래스 부분 단어 대신 해당 단어를 자동으로 삽입 합니다. 목록에 둘 이상의 단어를 <xref:Microsoft.VisualStudio.Package.Source> 클래스에는 사용자에 맞게 선택할 수 있는 도구 팁 목록을 보여 줍니다.  
  
 예를 살펴볼 수도 <xref:Microsoft.VisualStudio.Package.Declarations> 에서 클래스 구현을 [레거시 언어 서비스의 멤버 완성](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
