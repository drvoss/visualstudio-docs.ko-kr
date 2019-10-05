---
title: 사용자 지정 사용자 인터페이스 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f03713213ec2e54ed8d82d7528dae12cefab7ebc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154984"
---
# <a name="custom-user-interface-source-control-vspackage"></a>사용자 지정 사용자 인터페이스(소스 제어 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage는 Visual Studio 명령 테이블 (.vsct) 파일을 통해 해당 메뉴 항목 및 기본 상태로 선언합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE)는 VSPackage가 로드 될 때까지 기본 상태로 메뉴 항목을 표시 합니다. 이후에 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메뉴 항목을 사용할지 여부를 호출 합니다.  
  
 VSPackage 명령 사용자 인터페이스 (UI) 컨텍스트에 따라 VSPackage를 자동으로 로드할 수 있도록 레지스트리 키를 설정할 수 있습니다, 그리고 방금 특정 UI 컨텍스트로 전환 하는 대신 요청 시 VSPackage가 로드 되지만 일반적으로 소스 제어 합니다. AutoLoadPackages 레지스트리 키에 대 한 자세한 내용은 참조 하세요. [관리 Vspackage](../../extensibility/managing-vspackages.md)합니다.  
  
## <a name="vspackage-ui"></a>VSPackage UI  
 소스 제어 패키지를 VSPackage로 구현 되 고 모든 UI를 사용 하지 않는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 각 소스 제어 VSPackage는 소스 제어 VSPackage에 옵션을 특정 설정에 대 한 메뉴 항목, 메뉴 그룹, 도구 창, 도구 모음 및 모든 필수 UI와 같은 자체 UI 요소를 지정 해야 합니다. 정적 또는 동적으로 이러한 UI 요소를 사용할 수 있습니다. 정적 UI 요소.vsct 파일에서 정의 되 고 여부는 VSPackage가 로드 하는지 여부를 표시 됩니다. 동적 UI 요소와 같은 특정 명령 UI 컨텍스트의 따라 표시 될 수 있습니다 <xref:EnvDTE.Constants.vsContextNoSolution>, 또는 호출의 결과로 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드. 동적 UI 요소의 표시 유형을 Vspackage의 지연된 로드를 위한 전략을 준수합니다.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>소스 제어 Vspackage에 대 한 UI 제약 조건  
 로드 된 후에 IDE에서 소스 제어 VSPackage를 제거할 수 없습니다, 때문에 VSPackage 비활성 상태가 있어야 합니다. VSPackage는 것이 더 이상 활성 알림을 받으면 VSPackage는 UI를 사용 하지 않도록 설정 하 고 모든 외부 IDE 상호 작용을 무시 합니다. VSPackage의 구현의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드 VSPackage 비활성 상태일 때 명령을 숨겨야 합니다.  
  
 모든 소스 제어 VSPackage 구현 해야 합니다는 `IVsSccProvider` 인터페이스입니다. 인터페이스에서 두 개의 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, VSPackage 구현 해야 합니다.  
  
 소스 제어 VSPackage에 의해 구현 되는 다양 한 IDE 이벤트를 구독 했을 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>등입니다. 또한 VSPackage 있습니다 구현한 레지스트리 사용 하도록 설정 하는 콜백 인터페이스와 같은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>합니다. 이러한 모든 무시 해야 비활성 상태일 때.  
  
 다음은 소스 제어 VSPackage의 활성 상태에 영향을 받는 인터페이스를 보여 줍니다.  
  
- 프로젝트 문서 이벤트를 추적 합니다.  
  
- 솔루션 이벤트입니다.  
  
- 솔루션 지 속성 인터페이스입니다. 비활성 상태일 때 패키지.sln 및.suo 파일에 작성 되지 해야 합니다.  
  
- Extender 속성입니다.  
  
  필수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, 또한 소스 컨트롤과 연결 된 모든 선택적 인터페이스 호출 되지 않습니다 때 소스 제어 VSPackage 활성 상태가 아닙니다.  
  
  경우는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 시작 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 명령 UI 컨텍스트의 현재 기본 소스 제어 VSPackage id입니다. ID로 설정 이렇게 하면 현재 소스 제어 VSPackage를 실제로 로드 하지 않고 IDE에 표시 하기 위해 VSPackage의 정적 UI. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage 등록에 대 한 일시 중지 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 를 통해를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage에 대 한 모든 호출 하기 전에 합니다.  
  
  다음 표에서 방법에 대 한 특정 세부 정보를 설명 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 다른 UI 항목을 숨깁니다.  
  
|UI 항목|설명|  
|-------------|-----------------|  
|메뉴 및 도구 모음|소스 제어 패키지에서 원본 제어 패키지 ID를 초기 메뉴 및 도구 모음 표시 상태를 설정 해야 합니다 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct 파일의 섹션입니다. 그러면 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage를 로드 하 고의 구현을 호출 하지 않고 메뉴 항목의 상태를 적절 하 게 설정 하는 IDE를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드.|  
|도구 창|소스 제어 VSPackage 비활성 만들어질 경우 소유 하 고 있는 모든 도구 창을 숨깁니다.|  
|소스 제어 VSPackage 별 옵션 페이지|레지스트리 키 HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts VSPackage를 해당 옵션 페이지가 표시 되도록이 필요로 하는 컨텍스트를 설정할 수 있습니다. 이 키에서 레지스트리 항목을 소스 제어 서비스의 ID (SID) 서비스를 사용 하 여 1의 DWORD 값을 할당 하 여 만들 수 것입니다. VSPackage는 UI 이벤트가 발생할 때마다 컨텍스트에서 소스 제어 VSPackage 등록 된 활성 상태인 경우 호출 됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [VSPackage 관리](../../extensibility/managing-vspackages.md)
