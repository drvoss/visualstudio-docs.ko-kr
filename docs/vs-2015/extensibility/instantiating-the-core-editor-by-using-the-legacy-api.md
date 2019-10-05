---
title: 레거시 API를 사용 하 여 핵심 편집기 인스턴스화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203918"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>레거시 API를 사용하여 핵심 편집기 인스턴스화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기는 텍스트 삽입, 삭제, 복사 및 붙여넣기 등의 기능을 편집 합니다. 이러한 함수는 텍스트 색 지정, 들여쓰기 및 IntelliSense 문 완성 등의 언어 서비스와 결합 합니다.  
  
 세 가지 핵심 편집기의 인스턴스를 인스턴스화할 수 있습니다.  
  
- 명시적으로 창의 핵심 인스턴스 편집기를 만듭니다.  
  
- 핵심 편집기의 인스턴스를 반환 하는 편집기 팩터리를 제공 합니다.  
  
- 프로젝트 계층 구조에서 파일을 엽니다.  
  
  다음 섹션에서는 기존 API를 사용 하 여 편집기를 인스턴스화합니다 하는 방법에 설명 합니다.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>핵심 편집기 인스턴스를 명시적으로 열기  
 핵심 편집기의 인스턴스를 가져오는 명시적으로:  
  
- 가져오기는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 편집 중인 문서 데이터 개체를 보유할 합니다.  
  
- 문서 데이터 개체 지향 줄 표현을 만들어 만듭니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 에서 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 인터페이스입니다.  
  
- 설정 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 의 기본 구현 인스턴스에 대 한 문서 데이터 개체로 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 인터페이스를 사용 하 여를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> 메서드.  
  
   호스트는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 의 인스턴스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 인터페이스를 사용 하 여를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> 메서드.  
  
  이 시점에서 표시 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 인터페이스 핵심 편집기의 인스턴스를 포함 하는 창을 제공 합니다.  
  
  그러나이 아니므로 인스턴스를 매우 유용한 바로 가기 키가 하거나 고급 기능에 액세스 하지 않습니다. 바로 가기 키 및 고급 기능에 대 한 액세스를 얻으려면:  
  
- 사용 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 언어 서비스 및 편집기를 사용 하는 문서 데이터 개체에 연결 하는 방법입니다.  
  
- 사용자 고유의 바로 가기 키를 만들거나 설정 하 여 시스템 기본값을 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 개체 속성을 표시 합니다. 이 위해 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 속성입니다.  
  
   을 가져와서 비표준 바로 가기 키를 사용 하 여.vsct 파일을 사용 하 여 생성 합니다. 자세한 내용은 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)을 참조하세요.  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>핵심 편집기를 가져오려고 편집기 팩터리를 사용 하는 방법  
 핵심 편집기를 사용 하 여 편집기 팩터리를 구현 하는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드를 명시적으로 호스트를 이전 섹션에서 설명한 모든 단계를 수행는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 사용 하 여는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 문서 데이터 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 개체입니다.  
  
 텍스트를 표시 하려면 가져올는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 에서 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 개체를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드.  
  
 언어 서비스 편집기를 제공 하려면 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 메서드 내에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드.  
  
 기본 바로 가기 키의 이전 섹션에서 달리 가져오려고 반환한 명령 컨텍스트를 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 핵심 편집기에서 가져올 때 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드.  
  
 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 핵심 편집기의 인스턴스를 자동으로 가져옵니다 기본 바로 가기 키, 텍스트 편집기로 동일한 명령을 GUID를 반환 합니다.  
  
 일반 정보를 참조 하세요. [연습: 핵심 편집기 만들기 및 등록 된 편집기 파일 형식이](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [핵심 편집기 내에서](../extensibility/inside-the-core-editor.md)   
 [열기 및 프로젝트 항목 저장](../extensibility/internals/opening-and-saving-project-items.md)   
 [연습: 코어 편집기 만들기 및 편집기 파일 형식 등록](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
