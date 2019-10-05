---
title: 레거시 API를 사용 하 여 언어 서비스 컨텍스트에서 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193878"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>레거시 API를 사용하여 언어 서비스 컨텍스트 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

두 가지 옵션을 사용 하 여 사용자 컨텍스트를 제공 하는 언어 서비스는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기: 텍스트 표식 컨텍스트를 제공 하거나 모든 사용자 컨텍스트를 제공 합니다. 여기에 각 간의 차이점 요약 되어 있습니다.  
  
 사용자 고유의 편집기에 연결 된 언어 서비스에 대 한 컨텍스트를 제공 하는 방법은 참조 하세요. [방법: 편집기에 대 한 컨텍스트를 제공](../extensibility/how-to-provide-context-for-editors.md)합니다.  
  
## <a name="provide-text-marker-context-to-the-editor"></a>편집기 텍스트 표식 컨텍스트를 제공 합니다.  
 텍스트 표식으로 표시 하는 컴파일러 오류에 대 한 컨텍스트를 제공 하는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기를 구현 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 인터페이스입니다. 이 시나리오에서는 텍스트 마커에 커서가 있는 경우에 언어 서비스 컨텍스트를 제공 합니다. 이렇게 하면 편집기에서 커서를 키워드를 제공 하는 **동적 도움말** 특성이 없는 창입니다.  
  
## <a name="provide-all-user-context-to-the-editor"></a>편집기로 모든 사용자 컨텍스트를 제공 합니다.  
 언어 서비스를 만들 하 고 사용 하는 경우를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기를 구현할 수 있습니다 다음 핵심는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 언어 서비스에 대 한 컨텍스트를 제공 하는 인터페이스입니다.  
  
 구현의 `IVsLanguageContextProvider`, 컨텍스트 모음 (컬렉션) 컨텍스트 모음 업데이트를 담당 하는 편집기에 연결 됩니다. 경우는 **동적 도움말** 창 호출은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> 컨텍스트 모음 유휴 시간에이 컨텍스트 모음 인터페이스는 업데이트에 대 한 편집기를 쿼리 합니다. 편집기에 알립니다 언어 서비스 편집기를 업데이트 해야 하 고 상황에 맞는 모음에 대 한 포인터를 전달 합니다. 호출 하 여 이렇게를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> 편집기에서 언어 서비스 방법입니다. 컨텍스트 모음에 대 한 포인터 사용 언어 서비스 이제 추가 및 제거할 수는 특성과 키워드가 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>을 참조하세요.  
  
 구현 하는 방법에 두 가지가 `IVsLanguageContextProvider`:  
  
- 컨텍스트 모음에 키워드를 제공 합니다.  
  
   편집기 상황에 맞는 모음 업데이트 호출 되 면 적절 한 키워드 및 특성을 전달 하 고 반환 `S_OK`합니다. 반환 값이 편집기에는 커서를 상황에 맞는 모음에서 키워드를 제공 하는 것이 아니라 키워드 및 특성 컨텍스트를 유지 하도록 지시 합니다.  
  
- 커서 위치에 키워드에서 키워드를 가져오려면  
  
   편집기 상황에 맞는 모음 업데이트 호출 되 면 적절 한 특성을 전달 하 고 반환 `E_FAIL`합니다. 이 반환 값 편집기 상황에 맞는 모음에서 특성을 유지 하지만 커서 위치에 키워드를 사용 하 여 상황에 맞는 모음 업데이트에 지시 합니다.  
  
  다음 다이어그램은 구현 하는 언어 서비스에 대 한 상황에 맞는 제공 하는 방법을 보여 줍니다. `IVsLanguageContextProvider`합니다.  
  
  ![LangServiceImplementation2 그래픽](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  언어 서비스에 대 한 컨텍스트  
  
  다이어그램에서 알 수 있듯이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 텍스트 편집기에 연결 하는 상황에 맞는 모음입니다. 이 컨텍스트 모음 세 가지 별도 하위 컨텍스트의 모음을 가리킵니다: 언어 서비스 및 기본 편집기 텍스트 표식입니다. 언어 서비스 및 텍스트 표식 하위 컨텍스트의 모음 특성과 키워드 언어 서비스를 포함 하는 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 인터페이스가 구현 된 및 텍스트 마커 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 인터페이스 구현 됩니다. 이러한 인터페이스를 구현 하지 편집기 기본 편집기 하위 컨텍스트의 모음에 커서 위치에 키워드에 대 한 상황에 맞는 제공 합니다.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>편집기 및 디자이너에 대 한 상황에 맞는 지침  
 디자이너와 편집기 편집기 또는 디자이너 창에 대 한 일반 키워드를 제공 해야 합니다. 이 수행 되 면 f1 키를 누를 때 디자이너 또는 편집기에 대 한 도움말 항목을 일반, 하지만 적절 하 게 표시 됩니다. 편집기 해야 합니다이 외에도 현재 커서 위치에 키워드를 제공 하거나 현재 선택에 따라 키 용어를 제공 합니다. 텍스트 또는 UI 요소에 대 한 도움말 항목을 가리키는 하거나 f1 키를 누를 때 표시를 선택한 않도록 수행 됩니다. 디자이너를 폼에 단추와 같은 디자이너에서 선택한 항목에 대 한 컨텍스트를 제공 합니다. 편집기 및 디자이너 해야에 설명 된 대로 언어 서비스에 연결할 수도 [레거시 언어 서비스 필수 항목](../extensibility/internals/legacy-language-service-essentials.md)합니다.
