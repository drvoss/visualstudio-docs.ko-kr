---
title: 글꼴 및 색을 사용 하 여 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177230"
---
# <a name="using-fonts-and-colors"></a>글꼴 및 색 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 글꼴 및 색을 사용 하 여 텍스트를 표시 하는 것에 대 한 지원을 제공 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)  
 텍스트 글꼴 및 색 설정에 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE)입니다. 또한 범주 및 표시 항목의 개념을 소개 하 고 Vspackage 및 핵심 편집기 텍스트 특성을 사용 하는 방법에 대해 설명 합니다.  
  
 [텍스트 색 지정을 위해 글꼴 및 색 정보 가져오기](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 관리 하는 Vspackage의 텍스트 색 지정을 구현 하기 위한 지침을 제공 **범주** 이외의 **텍스트 편집기**합니다.  
  
 [저장된 글꼴 및 색 설정에 액세스](../extensibility/accessing-stored-font-and-color-settings.md)  
 어떻게 현재 글꼴 및 색을 설명 설정 저장, 검색 및 적용할 수 있습니다.  
  
 [사용자 지정 범주 및 표시 항목 구현](../extensibility/implementing-custom-categories-and-display-items.md)  
 사용 되는 창을 만들고 사용할 수 있는 자체의 기본 단계를 설명 **표시 항목** 하 고 **범주** 텍스트 표시를 지원 하 합니다.  
  
 이 접근 방식에서는 구현 하는 VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 인터페이스 및 관련된 인터페이스입니다.  
  
 [방법: 기본 제공 글꼴 및 색 구성표에 액세스](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 정의 기본 제공 글꼴 및 색을 사용 하 여 범주를 등록 하 고 시스템 제공 글꼴 및 색 사용을 시작 하는 방법을 설명 합니다.  
  
## <a name="reference"></a>참조  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 인스턴스를 제공 합니다 `IVsFontAndColorDefaults` 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 에 나열 된 특정 항목에 해당 하는 인터페이스를 **표시 설정에 대 한** 목록에 **글꼴 및 색** 페이지의 **옵션** 대화 상자.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 IDE를 지원 하기 위해 VSPackage를 사용 하도록 설정 **글꼴 및 색** 기본 글꼴 및 색 창 또는 UI 구성 요소를 정의 하 여 페이지입니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 메커니즘을 제공 하는 VSPackage 지원 글꼴 및 색 표시 항목 그룹-둘 이상의 범주의 합집합을 나타내는 상위 범주를 지정할 수는 있습니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 글꼴 및 색 데이터를 검색 또는 레지스트리에 저장 하기 위해 VSPackage를 사용 하도록 설정 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 글꼴 및 색 설정에 변경 내용에 대 한 글꼴 및 색 정보를 사용 하는 Vspackage를에 알립니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 메서드에서 사용 되는 입력 및 출력 데이터를 사용 하 여 작업 하기 위한 도구를 제공 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **글꼴 및 색** 메커니즘입니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 글꼴 및 색 설정의 캐시 제어 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)  
 Vspackage 언어 서비스를 사용 하 여 사용자 지정 하는 방법을 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기입니다.  
  
 [사용자 지정 편집기의 구문 색 지정](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 방법을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기 구문 색 지정을 구현 하기 위해 언어 서비스를 사용 합니다.  
  
 [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 서비스를 사용하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 나머지와 일치하는 UI 요소를 만드는 방법을 설명합니다.
