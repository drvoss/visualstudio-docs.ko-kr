---
title: 프로젝트 하위 형식에서 속성 및 메서드 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20892d50afc529b410e8e0bdfa3c4b52fdc1b9b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154119"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>프로젝트 하위 형식에 의해 확장된 속성 및 메서드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 형식에 전력을 많이 소모 되므로 기본 프로젝트의 집계로 생성 된 프로젝트의 동작에 영향을 줍니다. 이 섹션에서는 프로젝트 하위 형식에 의해 수정 되거나 향상 될 수 있는 기능 중 일부를 요약 합니다.  
  
## <a name="features-gained-by-aggregation"></a>집계를 통해 얻은 기능  
 다음 표에서 여러 집계에는 프로젝트 하위 형식 기본 프로젝트에서 재정의할 수 있도록 하는 메서드.  
  
|집계에 의해 재정의 메서드|프로젝트 하위 형식|  
|---------------------------------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|프로젝트 하위 형식에 사용 하도록 설정<br /><br /> 캡션 및 아이콘 프로젝트 노드를 변경 합니다.<br />-프로젝트 완전히 재정의 `Browse` 개체입니다.<br />-프로젝트 이름을 바꿀 수 있는지 여부를 제어 합니다.<br />정렬 순서를 제어 합니다.<br />동적 도움말에 대 한 사용자 컨텍스트를 제어 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|프로젝트 하위 형식을 상황에 맞는 서비스 디자이너와 편집기에 제공 됩니다 제어할 수 있습니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|프로젝트 하위 형식에 사용 하도록 설정<br /><br /> -프로젝트 명령에 대 한 명령 라우팅에 참여 합니다.<br />추가, 제거 또는 앰비언트 명령은 프로젝트와 활성 명령이 솔루션 탐색기를 사용 하지 않도록 설정 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|프로젝트 하위 형식에서 사용자에 게 무엇을 필터링 할 수 있도록 합니다 **새 항목 추가** 대화 상자.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|프로젝트 하위 형식에 사용 하도록 설정<br /><br /> -파일 확장명을 지정 하면 기본 생성기를 결정 합니다.<br />-COM 개체를 사람이 읽을 수 있는 생성기 이름이 매핑됩니다.|  
  
## <a name="properties-used-by-project-subtypes"></a>프로젝트 하위 형식에서 사용 되는 속성  
 환경 및 기본 프로젝트 시스템에서 속성을 사용할 수 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> 고 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> 프로젝트 시스템의 다양 한 기능을 제어 하는 프로젝트 하위 형식을 사용 하도록 설정 하려면 다음 표에서 자세히 설명 하는 열거형입니다.  
  
|VSHPROPID 속성|프로젝트 하위 형식|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|프로젝트 하위 형식의 내용을 제어를 허용 합니다 **항목 추가** 대화 상자. 프로젝트 하위 형식 템플릿 디렉터리의 새 사양을 제공, 항목의 새 종류를 추가, 기존 항목을 제거 하는 기본 프로젝트에 있는 항목의 하위 집합을 다시 구성 **항목 추가** 대화 상자.|  
|`PropertyPagesCLSIDList`|프로젝트 하위 형식을 구성에 관계 없이 속성 페이지를 추가 하거나 제거할 수 있습니다.|  
|`CfgPropertyPagesCLSIDList`|프로젝트 하위 형식을 구성에 종속 된 속성 페이지를 추가 하거나 제거할 수 있습니다.|  
|`ExtObjectCATID`|개체를 제공 하는 Automation Extender 프로젝트 또는 프로젝트 항목의 Extender CATID를 파악 하 여 프로젝트 하위 형식을 수 있습니다. 프로젝트 하위 형식에서 사용자 지정을 제공할 수는 예를 들어 `Project.Extender("<subtype>")` 개체입니다.|  
|`BrowseObjectCATID`|프로젝트 하위 형식에 대 한 Automation Extender 수 있도록 허용 합니다 `Browse` 개체의 Extender CATID를 파악 하 여 합니다. 예를 들어, 프로젝트 하위 형식에 추가 속성을를 추가할 수는 <xref:EnvDTE.Project.Properties%2A> 컬렉션입니다.|  
|`CfgBrowseObjectCATID`|프로젝트 하위 형식을 프로젝트 구성 찾아보기 개체에 대 한 Automation Extender를 제공할 수 있습니다. 예를 들어, 프로젝트 하위 형식에 추가 속성을를 추가할 수는 <xref:EnvDTE.Configuration.Properties%2A> 컬렉션입니다.|  
|`CfgExtObjectCATID`|프로젝트 하위 형식을 구성 개체에 대 한 Automation Extender를 제공할 수 있습니다.|  
|`DefaultPlatformName`|프로젝트 하위를 프로젝트의 구성 개체에 대 한 플랫폼 이름을 확인할 수 있습니다.|  
  
 기본 프로젝트에는 위의 속성의 기본 구현을 제공합니다. 호출 하 여 이러한 기본 프로젝트 가져옵니다 `QueryInterface` 에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 가장 바깥쪽 프로젝트 하위 형식 있으므로 속성 구현을 재정의 하는 프로젝트 하위 형식입니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 하위 형식 디자인](../../extensibility/internals/project-subtypes-design.md)
