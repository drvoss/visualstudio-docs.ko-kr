---
title: 언어를 포함 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184285"
---
# <a name="contained-languages"></a>포함된 언어
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*언어 포함* 은 다른 언어에 포함 된 언어입니다. 예를 들어, HTML [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 페이지에 포함 될 수 있습니다 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 스크립트입니다. 이중 언어 아키텍처는 HTML 및 스크립팅 언어에 대 한 IntelliSense, 색 지정 및 다른 편집 기능을 제공 하는.aspx 파일 편집기 필요 합니다.  
  
## <a name="implementation"></a>구현  
 포함 된 언어에 대 한 구현 해야 할 가장 중요 한 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 인터페이스입니다. 이 인터페이스는 주 언어 내에서 호스팅될 수 있는 모든 언어에서 구현 됩니다. 언어 서비스의 colorizer, 텍스트 보기 필터 및 기본 언어 서비스 ID에 액세스 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> 만들 수 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 인터페이스입니다. 다음 단계를 포함 된 언어를 구현 하는 방법을 보여 줍니다.  
  
1. 사용 하 여 `QueryService()` 의 인터페이스 ID와 서비스 ID는 언어는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>합니다.  
  
2. 호출 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> 메서드를는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 인터페이스입니다. 전달 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 인터페이스를 하나 이상의 [항목 Id](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> 인터페이스입니다.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> 인터페이스는 텍스트 버퍼 coordinator 개체인 보조 언어의 버퍼에 주 파일의 위치를 매핑하는 데 필요한 기본 서비스를 제공 합니다.  
  
     예를 들어, 단일.aspx 파일에 주 파일에는 ASP, HTML 및 포함 된 모든 코드가 포함 됩니다. 그러나 보조 버퍼에 포함 된 코드를 보조 버퍼를 올바른 코드 파일을 만들기 위해 모든 클래스 정의 함께 포함 됩니다. 버퍼 코디네이터 다른 하나의 버퍼에서 편집을 조정 하는 작업을 처리 합니다.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> 해당 버퍼 내에서 텍스트의 해당 텍스트를 보조 버퍼에 매핑되는 기본 언어는 메서드를가 버퍼 코디네이터 알려 줍니다. 합니다.  
  
     언어의 배열로 전달 된 <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> 구조를 포함 하는 현재 주 복제본 및 보조 범위입니다.  
  
5. 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> 메서드 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> 메서드 보조 버퍼를 반대로 하는 기본에서 매핑을 제공 합니다.
