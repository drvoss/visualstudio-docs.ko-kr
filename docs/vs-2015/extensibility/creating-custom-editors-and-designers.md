---
title: 사용자 지정 편집기 및 디자이너 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 32
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc94d11a5ed118f0133657ebf5b966623a199d64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197415"
---
# <a name="creating-custom-editors-and-designers"></a>사용자 지정 편집기 및 디자이너 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 통합된 개발 환경 (IDE)는 다양 한 유형의 편집기를 호스팅할 수 있습니다.  
  
- Visual Studio 핵심 편집기  
  
- 사용자 지정 편집기  
  
- 외부 편집기  
  
- 디자이너  
  
  다음 정보를 해야 하는 편집기 유형의 방법을 선택할 수 있습니다.  
  
## <a name="types-of-editor"></a>편집기의 형식  
 Visual Studio 핵심 편집기에 대 한 정보를 참조 하세요 [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)합니다.  
  
##### <a name="custom-editors"></a>사용자 지정 편집기  
 사용자 지정 편집기는 특수 한 환경에서 작동 하도록 설계 되었습니다. 예를 들어, 편집기를 Microsoft Exchange server와 같은 특정 리포지토리에 데이터를 읽고 해당 함수는 만들 수 있습니다. 프로젝트 형식 에서만 작동 하는 편집기 또는 특정 명령에는 편집기를 하려는 경우에 사용자 지정 편집기를 선택 합니다. 단, 사용자는 사용자 지정 편집기를 사용 하 여 표준 편집할 수 없습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트입니다.  
  
 사용자 지정 편집기 편집기 팩터리를 사용 하 고 레지스트리 편집기에 대 한 정보를 추가할 수 있습니다. 그러나 사용자 지정 편집기를 사용 하 여 연결 된 프로젝트 형식에는 다른 방법으로 사용자 지정 편집기를 인스턴스화할 수 있습니다.  
  
 사용자 지정 편집기 뷰를 구현 하려면 문제를 내부 활성화 또는 간소화 된 포함 하는 데 사용할 수 있습니다.  
  
##### <a name="external-editors"></a>외부 편집기  
 외부 편집기는 Microsoft Word, 메모장 또는 Microsoft FrontPage 같은 Visual Studio에 통합 되지 않는 편집기입니다. 이러한 편집기, 예를 들어, 전달 하는 경우 텍스트를 VSPackage에서 호출할 수 있습니다. 외부 편집기 자체를 등록 하 고 Visual Studio 외부에서 사용할 수 있습니다. 외부 편집기를 호출 하 고 호스트 창에 포함 하는 경우 다음 나타나는 IDE의 창. 그렇지 않은 경우 다음 IDE에 대 한 별도 창을 만듭니다.  
  
 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 메서드를 사용 하 여 문서 우선 순위를 설정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거형입니다. 경우는 `DP_External` 값을 지정한 경우 외부 편집기에서 파일을 열 수 있습니다.  
  
## <a name="editor-design-decisions"></a>편집기 디자인 결정  
 다음 디자인 질문에는 응용 프로그램에 적합 한 최상의 편집기의 유형을 선택 하는 데 도움이 됩니다.  
  
- 응용 프로그램 데이터 파일에 저장 여부? 데이터 파일에 저장 됩니다을 하는 경우 사용자 지정 또는 표준 형식으로 될 것인가?  
  
     표준 파일 형식을 사용 하면 프로젝트 외에도 다른 프로젝트 형식의를 열고 데이터를 읽기/쓰기 수 됩니다. 그러나 사용자 지정 파일 형식을 사용 하면 프로젝트 형식에만 열고 데이터를 읽기/쓰기 할 됩니다.  
  
     프로젝트 파일에 사용 하는 경우 다음 사용자 지정 해야 표준 편집기입니다. 프로젝트 파일을 사용 하지 않습니다 하지만 대신 데이터베이스 또는 다른 저장소에 항목을 사용 하는 경우 사용자 지정 편집기를 만들 해야 있습니다.  
  
- 편집기에서 ActiveX 컨트롤을 호스트 해야 하나요?  
  
     편집기에서 ActiveX 컨트롤을 호스트 하는 경우 다음 구현 바로 활성화 편집기에 설명 된 대로 [내부 활성화](../misc/in-place-activation.md)합니다. ActiveX 컨트롤을 호스트 하지 않습니다 하는 경우 다음 간단한 포함 편집기를 사용 하 여 또는 사용자 지정을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 기본 편집기입니다.  
  
- 편집기는 여러 뷰를 지원할? 기본 편집기로 동시에 표시 되도록 편집기의 보기를 하려는 경우에 여러 뷰를 지원 해야 합니다.  
  
     편집기를 여러 뷰를 지원 해야 하는 경우 문서 데이터 및 문서 보기 개체 편집기에 대 한 별도 개체 여야 합니다. 자세한 내용은 [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md)합니다.  
  
     편집기에서는 여러 보기를 수행 하려는 경우 사용 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기의 텍스트 버퍼 구현 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 개체) 문서 데이터 개체에 대 한? 즉, 할까요 프로그램 편집기 보기--함께 지원 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기? 이 작업을 수행 하는 기능은 forms 디자이너의 기본...  
  
- 외부 편집기를 호스트 하는 경우 수 편집기 내에 포함 될 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]?  
  
     를 포함 하는 경우 외부 편집기에 대 한 호스트 창을 만들 하 고 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 집합과 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거형 값 `DP_External`. 편집기를 포함할 수 없는 경우 IDE에 대 한 별도 창을 자동으로 만듭니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)  
 사용자 지정 편집기를 만드는 방법을 설명 합니다.  
  
 [연습: 사용자 지정 편집기에 기능 추가](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 사용자 지정 편집기 기능을 추가 하는 방법에 설명 합니다.  
  
 [디자이너 초기화 및 메타데이터 구성](../extensibility/designer-initialization-and-metadata-configuration.md)  
 디자이너를 초기화 하는 방법을 설명 합니다.  
  
 [디자이너에 실행 취소 지원 제공](../extensibility/supplying-undo-support-to-designers.md)  
 디자이너에 대 한 실행 취소 기능을 제공 하는 방법에 설명 합니다.  
  
 [사용자 지정 편집기의 구문 색 지정](../extensibility/syntax-coloring-in-custom-editors.md)  
 핵심 편집기에 사용자 지정 편집기의 색상을 지정 하는 구문의 차이점을 설명 합니다.  
  
 [사용자 지정 편집기의 문서 데이터 및 문서 보기](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 사용자 지정 편집기의 문서 데이터 및 문서 보기를 구현 하는 방법에 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [편집기의 레거시 인터페이스](../extensibility/legacy-interfaces-in-the-editor.md)  
 기존 API를 사용 하 여 핵심 편집기를 액세스 하는 방법에 설명 합니다.  
  
 [레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)  
 언어 서비스를 구현 하는 방법을 설명 합니다.  
  
 [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)  
 나머지와 일치 하는 UI 요소를 만드는 방법에 설명 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
