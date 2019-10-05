---
title: 레거시 API를 사용 하 여 코드 Windows를 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62556145"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>레거시 API를 사용 하 여 사용자 지정 코드 Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 창에는 하나 이상의 텍스트 뷰를 지 원하는 문서 창 개체입니다. 코드 창의 정확한 기능 관련 된 언어 서비스에 따라 달라 집니다. (MDI) 다중 문서 인터페이스 모드로 코드 MDI 자식 프레임입니다.  
  
 각 언어 서비스에서는 고유한 코드 창 관리자를 제공할 수 있습니다 및 코드 windows 언어 서비스에 의해 제어 됩니다. 이 언어 서비스를 자체 장식을 물결선, 색 지정 등 코드 창에 추가할 수 있습니다. Core 창을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [레거시 API는 편집기에서 사용 하 여 Core 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)합니다.  
  
 코드 창이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 텍스트 뷰 및 개체에 있는 장식을 포함 하는 개체입니다. 코드 창 핵심 프로그램 인스턴스화하는 동안 편집기를 만들면 언어 서비스에 연결할 수는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 코드 창에 다음 그림과에서 같이으로 합니다.  
  
 ![CodeWindow 그래픽](../extensibility/media/vscodewindow.gif "vscodewindow")  
코드 창  
  
 언어 서비스는 코드 창 관리자를 구현 하 고는 드롭다운 표시줄과 같은 프로그램을 관리 합니다. 코드 창 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 코드 창 초기화 하는 동안 메서드. 이 호출 되 면 드롭다운 가로 막대 또는 단추 표시줄 언어 서비스를 추가할 수 (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>)의 코드 창입니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 `Customizing Code Windows by Using the Legacy API`  
 기존 API를 사용 하 여 코드 창을 사용자 지정 하는 방법에 설명 합니다.  
  
 [방법: 다른 편집기에서 편집기 호스트](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 편집기 창 내에서 두 번째 편집기를 호스트 하는 방법에 설명 합니다.  
  
 [방법: 편집기에서 포커스를 잃을 때 이벤트 발생](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 문서 보기 문서 데이터 개체를 연결 하는 방법에 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [레거시 API를 사용 하 여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [레거시 API를 사용하여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
