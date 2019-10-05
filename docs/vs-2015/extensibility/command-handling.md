---
title: 명령 처리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184369"
---
# <a name="command-handling"></a>명령 처리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기 새 명령을 정의할 수 있습니다. 일반적으로 상황에 맞는 메뉴 또는 도구 모음에 메뉴 명령은 표시 됩니다.  
  
 명령 및 메뉴를 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)합니다.  
  
 어떤 상황에 맞는 메뉴를 차단 하 여 편집기에 표시 됩니다 언어 서비스를 제어할 수는 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 열거형입니다. 또는 표식 당 기준 상황에 맞는 메뉴를 제어할 수 있습니다. 자세한 내용은 참조 [언어 서비스 필터에 대 한 중요 명령](../extensibility/internals/important-commands-for-language-service-filters.md)입니다.  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>편집기 상황에 맞는 메뉴에 명령 추가  
 상황에 맞는 메뉴에 명령을 추가 하려면 먼저 특정 그룹에 속하는 메뉴 명령 집합을 정의 해야 합니다. 다음 예제에서는 연습의 일환으로 생성 되는.vsct 파일에서 가져온 것 [연습: 추가 기능을 사용자 지정 편집기에](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText > CustomEditor 상황에 맞는 메뉴\</ButtonText >  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 텍스트를 사용 하 여 상황에 맞는 메뉴 명령을 추가 하는 위의 텍스트가 **CustomEditor 상황에 맞는 메뉴**합니다. 메뉴 GUID이이 편집기를 사용 하 여 만든 명령 집합의 형식은 "컨텍스트" 있다는 것입니다.  
  
 .Vsct 파일에서 정의 될 필요가 있는 미리 정의 된 명령을 사용할 수도 있습니다. 예를 들어, Visual Studio 패키지 템플릿은에서 생성 한 EditorPane.cs 파일을 검사 하면 찾아야 하는 미리 정의 된 명령 집합을 같은 <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> 정의한 <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, onSelectAll 메서드와 같은 명령 처리기에서 처리 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
