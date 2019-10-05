---
title: 드롭다운 표시줄 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204664"
---
# <a name="drop-down-bar"></a>드롭다운 표시줄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

드롭다운 표시줄 코드 창의 맨 위에 있는 제공 되 고 두 개의 드롭다운 목록이 포함 되어 있습니다.  
  
## <a name="drop-down-bar-interfaces"></a>드롭다운 표시줄 인터페이스  
 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], 드롭다운 막대로 목록을 포함 하는 예를 들어 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 항목 및 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 다음 그림에 나와 있는 것 처럼 항목 멤버 함수입니다.  
  
 ![삭제&#45;아래쪽 막대](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
드롭다운 표시줄  
  
 드롭다운 표시줄을 구현할 때 가지 주 중요도의 네 가지 인터페이스가 있습니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     드롭다운 표시줄의 콘텐츠를 삽입 하려면이 인터페이스를 구현 합니다. 일반 텍스트 또는 고급 텍스트 각 드롭 다운 조합을 포함할 수 있습니다 (굵게, 기울임꼴 또는 밑줄), 창 텍스트 글꼴 색 지정 또는 회색된 글꼴 색 지정, 있을 수 있으며 드롭다운 목록 항목 옆에 작은 비트맵을 선택적으로 제공할 수 있습니다. 비슷합니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 인터페이스 이미지 목록의 비트맵 이미지를 제공 합니다. 각 드롭 다운 조합 다른 이미지 목록을; 있습니다. 그러나 각 이미지 목록 같은 높이의 이미지를 포함 해야 합니다. 또한를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> 메서드를 각 조합에 대 한 도구 설명을 제공할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     만들거나 코드 창에 대 한 드롭다운 메뉴 모음을 삭제 하려면이 인터페이스를 호출 합니다. 이 인터페이스 드롭다운 막대로 연결 되는지 여부를 이미 코드 창에 호출 하 여 확인을 사용할 수도 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> 메서드. 호출 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 에 대 한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> 에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>합니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     드롭다운 표시줄와 직접 통신 하기 위해이 인터페이스를 호출 합니다. 이 인터페이스를 사용 하 여 드롭다운 목록 새로 고침을 강제 하 콘텐츠 모음이 나 목록 상자 중 하나에서 선택 항목을 변경 합니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     등록 한 경우는 `ShowDropdownBarOption` 언어 서비스 레지스트리 키에 다음 코드 창 관리자에 게 모니터링 해야이 이벤트는 드롭다운 표시줄을 표시 해야 하는지 여부에 대 한 사용자 기본 설정을 사용 하 여 동기화를 합니다. 언어 서비스 키를 사용 하 여이 옵션을 등록 하지 않은 경우에 드롭다운 표시줄 표시 / 숨기기 하는 옵션은 사용 하지 않도록 설정 합니다 **옵션** 메뉴.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>드롭다운 표시줄 코드 창에 연결  
 드롭다운 표시줄에 연결 하려면 코드 창 만들어질 때 언어 서비스는 드롭다운 목록에 연결 해야 경우 막대는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 메서드가 호출 됩니다. 호출 하는 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> 메서드는 드롭다운 막대로 존재 다음 호출 되어 있지 않습니다 나타냅니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>합니다. 액세스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> 인터페이스를 호출 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 포인터를 반환에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 구현 된 연결입니다.  
  
## <a name="see-also"></a>관련 항목  
 [레거시 API를 사용 하 여 사용자 지정 코드 Windows](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [레거시 언어 서비스의 탐색 모음 지원](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
