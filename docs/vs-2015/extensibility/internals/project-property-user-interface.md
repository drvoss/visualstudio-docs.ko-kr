---
title: 프로젝트 속성 사용자 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31840c40f2a494ffd32f5241e2770938138877e9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704093"
---
# <a name="project-property-user-interface"></a>프로젝트 속성 사용자 인터페이스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 형식 프로젝트에서 항목을 사용할 수 있습니다 **속성 페이지** 대화 상자 기본 프로젝트에서 제공 되기 때문 숨기기 또는 제공 하 고, 읽기 전용 컨트롤 및 전체 페이지를 확인 또는 프로젝트 하위 형식의 특정 페이지를 추가할**속성 페이지** 대화 상자.  
  
## <a name="extending-the-project-property-dialog-box"></a>프로젝트 속성 대화 상자를 확장합니다.  
 프로젝트 하위 형식 automation extender 및 프로젝트 구성 찾아보기 개체를 구현합니다. 이러한 extender 구현 된 <xref:EnvDTE.IFilterProperties> 숨김 또는 읽기 전용으로 특정 속성을 확인 하는 인터페이스입니다. 합니다 **속성 페이지** 기본 프로젝트를 구현한 기본 프로젝트의 대화 상자는 Automation extender가 수행한 필터링 합니다.  
  
 확장 프로세스는 **프로젝트 속성** 아래 설명 된 대화 상자:  
  
- 기본 프로젝트 extender 프로젝트 하위 형식에서 구현 하 여 검색 된 <xref:EnvDTE80.IInternalExtenderProvider> 인터페이스입니다. 찾아보기, 프로젝트 자동화 및 모든 기본 프로젝트의 프로젝트 구성 찾아보기 개체에는이 인터페이스를 구현 합니다.  
  
- 구현의 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 찾아보기 개체 및 프로젝트 자동화 개체에 대리자에 대 한는 <xref:EnvDTE80.IInternalExtenderProvider> 구현의 프로젝트 하위 형식 집계 (즉, `QueryInterface` 에 대 한 <xref:EnvDTE80.IInternalExtenderProvider> 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 프로젝트 개체)입니다.  
  
- 기본 프로젝트 구성 찾아보기 개체도 구현 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 형식 구성 개체에서 Automation Extender에 직접 연결 합니다. 구현에 위임 된 <xref:EnvDTE80.IInternalExtenderProvider> 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스입니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>를 프로젝트 구성 찾아보기 개체를 반환 하 여 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체입니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>에 프로젝트 구성 찾아보기 개체를 반환 하 여 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> 개체입니다.  
  
- 프로젝트 하위 형식이 면 다음을 검색 하 여 런타임 시 기본 프로젝트의 다양 한 확장 가능한 개체에 대 한 적절 한 Catid를 확인할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 값:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  프로젝트 범위에 대 한 Catid를 확인 하려면 프로젝트 하위 형식에 대 한 위의 속성을 검색 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> 에서 `VSITEMID``typedef`합니다. 프로젝트 하위 형식 제어 하는 수도 **속성 페이지** 대화 상자 페이지를 프로젝트에 대해 표시 되 구성 종속 및 독립 구성 합니다. 일부 프로젝트 하위 형식 기본 제공 페이지를 제거 하 고 프로젝트 하위 형식에 대 한 특정 페이지를 추가 해야 합니다. 이 호출 하 여 관리 되는 클라이언트 프로젝트를 사용 하도록 설정 하기 위해는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 다음 속성에 대 한 메서드:  
  
- `VSHPROPID_PropertyPagesCLSIDList` -구성에 관계 없이 속성 페이지의 Clsid 세미콜론으로 구분 된 목록입니다.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` 구성에 종속 된 속성 페이지의 Clsid 목록을 세미콜론으로 구분 합니다.  
  
  프로젝트 하위 집계 형식 때문에 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체를 제어 하는 이러한 속성의 정의 재정의할 수 있습니다 **속성 페이지** 대화 상자가 표시 됩니다. 프로젝트 하위 형식 내부 기본 프로젝트에서 이러한 속성을 검색 하 고 추가 하거나 제거할 수 Clsid 필요에 따라 합니다.  
  
  프로젝트 하위 형식으로 추가 하는 새 속성 페이지에는 기본 프로젝트 구현과에서 프로젝트 구성 찾아보기 개체가 전달 됩니다. 이 프로젝트 구성 찾아보기 개체 Automation Extender를 지원합니다. AutomationExtenders에 대 한 자세한 내용은 참조 하세요. [구현 및 Automation Extender를 사용 하 여](https://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356)입니다. 프로젝트 하위 형식 호출에 의해 구현 된 속성 페이지 <xref:EnvDTE.Project.Extender%2A> 기본 프로젝트의 구성 찾아보기 개체를 확장 하는 자체 프로젝트 하위 형식 구성 찾아보기 개체를 검색 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:EnvDTE.IFilterProperties>   
 [속성 페이지 대화 상자](https://msdn.microsoft.com/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
