---
title: 속성 페이지 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a45e4a98326fe829b8f87a4ecfce669118cd9d0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205757"
---
# <a name="property-pages"></a>속성 페이지
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자가 보고 하 고 속성 페이지를 사용 하 여 프로젝트 구성에 종속 된와-속성을 변경할 수 있습니다. A **속성 페이지** 에서 단추를 사용할 수는 **속성** 창 또는 선택한 개체의 속성 페이지 보기를 제공 하는 개체에 대 한 솔루션 탐색기 도구 모음입니다. 속성 페이지 환경에서 생성 되 고 솔루션 및 프로젝트에 사용할 수 있습니다. 그러나도 사용할 수는 구성에 종속 된 속성을 사용 하는 프로젝트 항목에 대 한 사용 가능 합니다. 프로젝트 내에서 파일 올바르게 다른 컴파일러 스위치 설정이 필요한 경우에이 기능을 사용할 수 있습니다.  
  
## <a name="using-property-pages"></a>속성 페이지를 사용 하 여  
 속성 페이지를 이미 표시 하 고 새 선택 영역에 대 한 속성을 표시 하려면 페이지 변경 내용을 표시 되는 정보 (예를 들어 솔루션에서 프로젝트를) 선택 영역이 변경 합니다. 개체의 속성 페이지를 지 원하는 속성의 경우에 속성 페이지가 비어 있습니다.  
  
 여러 개체를 선택 하는 경우 속성 페이지는 선택한 모든 항목에 대 한 속성의 교차 부분을 표시 합니다. 선택한 항목에 구성에 종속 된 속성이 포함 되지 않습니다 및 **속성 페이지** 솔루션 탐색기 도구 모음 단추를 클릭 하면, 속성 창에 포커스를 변경 합니다. 속성 창 및 선택과 관련 한 자세한 내용은 [확장 속성](../../extensibility/internals/extending-properties.md)합니다.  
  
 여러 개체에 대 한 속성이 표시 됩니다. 속성 페이지에서 값을 변경 하면을 처음에 다른 것 및 개별 개체의 속성이 표시 된 페이지가 비어 있는 경우에 새 값으로 설정 됩니다 모든 개체에 대 한 값.  
  
 두 가지 일반 유형의 가지 **ProjectProperty 페이지** 대화 상자에서 사용할 수 있는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. Visual Basic 프로젝트에 대 한 첫 번째 예를 들어, 속성 페이지 표시 됩니다는 필드 형식을 사용 하 여 다음 스크린샷에 표시 된 대로. 두 번째는 뒷부분에 나오는이 섹션에서는 속성 페이지 호스트 속성 표에서 속성 창에 있는 비슷합니다.  
  
 ![Visual Basic 속성 페이지](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
필드 형식 및 트리 구조를 사용 하 여 프로젝트 속성 페이지 대화 상자  
  
 속성 페이지 대화 상자에서 트리 구조를 사용 하 여 빌드되지는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>합니다. 환경 이름을 기반으로 수준으로 전달 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> 인터페이스를 빌드합니다.  
  
 사용할 수 있는 두 개의 최상위 범주는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 속성 페이지:  
  
- 선택한 개체 또는 개체에 대 한 구성에 관계 없이 정보를 표시 하는 공용 속성입니다. 결과적으로, 공용 속성 하위 범주 중 하나를 선택 하면 대화 상자의 위쪽 구성, 플랫폼 및 Configuration Manager 옵션을 사용할 수 없습니다.  
  
- 디버깅, 최적화 및 빌드 매개 변수 솔루션이 나 프로젝트와 관련 된 구성에 종속 된 정보를 포함 하는 구성 속성.  
  
  모든 추가 최상위 범주를 만들 수는 없지만 구현에서 둘 중 하나를 표시 하지 않도록 선택할 수 있습니다 `IVsPropertyPage`합니다. 예를 들어 없는 모든 구성에 관계 없이 속성을 개체에 대 한 표시를 하는 경우에 공용 속성 범주를 표시할 필요가 선택할 수 있습니다. 경우 공용 속성을 표시할 `ISpecifyPropertyPages` 구현 하는 경우 구성 속성 및 항목의 찾아보기 개체에서 구현 됩니다 `ISpecifyPropertyPages` 구성 개체에서 (구현 하는 개체 `IVsCfg`, `IVsProjectCfg`, 관련 인터페이스)입니다.  
  
  최상위 범주 아래에 표시 하는 각 범주는 별도 속성 페이지를 나타냅니다. Category 및 subcategory 사용할 수 있는 항목 대화 상자에서의 구현에 따라 결정 됩니다 `ISpecifyPropertyPages` 고 `IVsPropertyPage`입니다.  
  
  `IDispatch` 선택 컨테이너의 속성 페이지 구현에 표시 되는 속성이 있는 항목에 대 한 개체 `ISpecifyPropertyPages` 클래스 Id의 목록을 열거 합니다. 클래스 Id를 변수로 전달 된 `ISpecifyPropertyPages` 및 속성 페이지를 인스턴스화하는 데 사용 됩니다. 클래스 Id 목록에 전달 됩니다 `IVsPropertyPage` 대화 상자의 왼쪽의 트리 구조를 만들려고 합니다. 속성 페이지를 통과 정보 다시 합니다 `IDispatch` 를 구현 하는 개체 `ISpecifyPropertyPages` 각 페이지에 대 한 정보를 입력 합니다.  
  
  찾아보기 개체의 속성을 검색 하 여 `IDispatch` 선택 컨테이너에서 각 개체에 대 한 합니다.  
  
  구현 `Help::DisplayTopicFromF1Keyword` VSPackage의 도움말 단추에 대 한 기능을 제공 합니다.  
  
  자세한 내용은 참조 하세요. `IDispatch` 고 `ISpecifyPropertyPages`MSDN 라이브러리에서.  
  
  두 번째 유형의 속성 페이지 표시 샘플 호스트의 속성 표 형태의 다음 스크린샷에 표시 된 대로 합니다.  
  
  ![VC 속성 페이지](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  속성 표를 사용 하 여 속성 페이지 대화 상자  
  
  인터페이스 `IVSMDPropertyBrowser` 및 `IVSMDPropertyGrid` (vsmanaged.h에서 선언 됨)를 만들고 대화 상자 또는 창 내에서 속성 그리드를 채우는 사용 됩니다.  
  
  프로젝트의 아키텍처는 이전 버전의에서 크게 변경 되었습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 특히, 프로젝트의 개념은 현재 변경 되었습니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 활성 프로젝트의 개념이 없습니다. 이전 개발 환경에 현재 프로젝트 빌드 및 배포 명령을 프로젝트 컨텍스트에 관계 없이 기본적으로 했습니다. 이제 솔루션을 제어 하 고는 빌드 및 배포 명령을 조정 되는 프로젝트에 적용 합니다.  
  
  던 활성 프로젝트를 이전에 필드가 이제 세 가지 방법 중 하나에 캡처됩니다.  
  
- 시작 프로젝트  
  
   프로젝트 또는 F5 키를 누르거나 빌드 메뉴에서 실행을 선택 하는 경우 시작 하는 솔루션의 속성 페이지에서 프로젝트를 지정할 수 있습니다. 굵은 글꼴을 사용 하 여 솔루션 탐색기에서 해당 이름이 표시 됩니다는 점에서 이전 활성 프로젝트에 비슷한 방식으로 작동 합니다.  
  
   시작 프로젝트를 호출 하 여 자동화 모델의 속성으로 검색할 수 있습니다 `DTE.Solution.SolutionBuild.StartupProjects`합니다. VSPackage에서 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 메서드. `IVsSolutionBuildManager` 사용 하 여 서비스 제품은 `QueryService` SID_SVsSolutionBuildManager에 있습니다. 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md) 하 고 [솔루션 구성](../../extensibility/internals/solution-configuration.md)합니다.  
  
- 활성 솔루션 빌드 구성  
  
   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 구현 하 여 자동화 모델에서 사용할 수 있는 활성 솔루션 구성이 `DTE.Solution.SolutionBuild.ActiveConfiguration`합니다. 솔루션 구성은 솔루션 (각 프로젝트는 여러 구성 서로 다른 이름 사용 하 여 여러 플랫폼에서 가질 수 있음)의 각 프로젝트에 대 한 하나의 프로젝트 구성을 포함 하는 컬렉션입니다. 솔루션의 속성 페이지와 관련 된 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)합니다.  
  
- 현재 선택 된 프로젝트  
  
   구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 프로젝트 계층 구조 및 프로젝트 항목 또는 선택한 항목을 검색 하는 방법입니다. DTE에서 사용 된 `SelectedItems.SelectedItem.Project` 고 `SelectedItems.SelectedItem.ProjectItem` 메서드. 핵심에 해당 머리글 아래에 있는 샘플 코드가 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 문서.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [관리 구성 옵션](../../extensibility/internals/managing-configuration-options.md)   
 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)   
 [솔루션 구성](../../extensibility/internals/solution-configuration.md)
