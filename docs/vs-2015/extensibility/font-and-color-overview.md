---
title: 글꼴 및 색 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204353"
---
# <a name="font-and-color-overview"></a>글꼴 및 색 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 텍스트 글꼴 및 색 설정에 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE)입니다. 범주 및 표시 항목의 개념 소개 하 고 Vspackage 및 핵심 편집기 텍스트 특성을 사용 하는 방법에 대해 설명 합니다.  
  
## <a name="the-fonts-and-colors-property-page"></a>글꼴 및 색 속성 페이지  
 에 표시 된 텍스트의 특성을 관리할 수 있습니다 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 통해 통합된 개발 환경 (IDE)는 **글꼴 및 색** 속성 페이지. 찾으려는 합니다 **글꼴 및 색** 속성 페이지를 **도구** 메뉴에서 클릭 **옵션**합니다. 확장 **환경을**를 클릭 하 고 **글꼴 및 색**합니다.  
  
## <a name="categories-and-display-items"></a>범주 및 표시 항목  
 글꼴 및 색 구조로 **범주** 하 고 **표시 항목**합니다.  
  
- A **범주** 다양 한 기능 또는 논리 컨테이너인 **표시 항목**합니다.  
  
   목록을 **범주** 에 **설정에 대 한 표시** 드롭다운 목록 상자를 **글꼴 및 색** 속성 페이지.  
  
- A **표시 항목** 는 주석, 문자열 또는 표시 하는 경우 색으로 표시 하는 제어 구조와 같은 잘 정의 된 텍스트 엔터티입니다.  
  
  각 **표시 항목** 내에서 고유 하 게 정의 되는 **범주** 해당 항목을 포함 합니다. 따라서 둘 이상의 **범주** 있습니다를 **표시 항목** 동일한 이름을 가진 합니다.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage 컨트롤의 글꼴 및 색  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Vspackage를 허용 합니다.  
  
- 글꼴 및 색을 정의할 **범주**합니다.  
  
- 글꼴 및 색을 나타내는 데 지정할 **표시 항목**합니다.  
  
- 상호 작용 합니다 **글꼴 및 색** 속성 페이지.  
  
- 집계 여러 **범주** 그룹화 합니다.  
  
- 기본 설정에서 변경 내용을 유지 합니다.  
  
  글꼴 및 색 선택 항목과 상호 작용 하는 방법은 두 가지는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]합니다.  
  
- 한 가지 방법은 이라고 *구문 색 지정*합니다. 기존 사용자 지정 하는 VSPackage에서 사용 되 고 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기 언어 서비스를 구현 하 고 소스 편집기를 만듭니다.  
  
   하나만 **범주** namely이 메커니즘을 지원 하면 **텍스트 편집기**합니다.  
  
- 보다 일반적인 대체를 지 원하는 다른 모든 **범주** 및 텍스트를 표시할 때 소스 편집기 이외의 사용자 인터페이스 구성 요소입니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>을 참조하세요.  
  
## <a name="core-editor-text-settings"></a>핵심 편집기 텍스트 설정  
 언어 서비스 개체의 핵심 편집기에 대 한 글꼴 및 색 설정에 의해 제어 됩니다는 **텍스트 EditorCategory** 에 **설정 표시** 드롭다운 목록 상자는 **글꼴 및 색** 속성 페이지.  
  
 편집기에서 작업할 때 특수 한 글꼴 및 색 제어 메커니즘을 제어 하 고 확장 언어 서비스를 제공 하는 사용 해야 합니다 **텍스트 편집기** 설정 합니다. 메커니즘 이라고 *구문 색 지정* 제공 합니다.  
  
- 글꼴 및 색 표시 항목을 관리 하기 위한 간소화 된 기술입니다.  
  
   자세한 내용은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>를 참조하세요.  
  
- 잘 정의 되 고 최적화 된 색 지정 메커니즘입니다.  
  
   자세한 내용은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>을 참조하세요.  
  
- 둘 다 수의 기본 표시 항목을 사용 합니다 **텍스트 EditorCategory** 및 확장 하 고 있습니다.  
  
   자세한 내용은 [방법: 기본 제공 색 항목 사용](../extensibility/internals/how-to-use-built-in-colorable-items.md) 하 고 [사용자 지정 색 항목](../extensibility/internals/custom-colorable-items.md)합니다.  
  
- 현재 모두 기본 제공 상태 및 사용자 지정 자동 지 속성 사용 하 여 항목을 표시 합니다 **텍스트 편집기** 범주입니다.  
  
  구문 참조 색 지정에 대 한 자세한 내용은 [레거시 언어 서비스의 구문 색 지정](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [편집기에서 레거시 인터페이스](../extensibility/legacy-interfaces-in-the-editor.md)   
 [레거시 언어 서비스의 구문 색 지정](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
