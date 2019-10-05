---
title: VSPackage 구조 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68206004"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 구조(소스 제어 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어 패키지 SDK를 사용 하 여 자신의 소스 제어 기능을 통합 하는 원본 제어 구현자를 허용 하는 VSPackage를 만들기 위한 지침 제공을 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 환경입니다. VSPackage는 일반적으로 하 여 요청 시 로드 되는 COM 구성 요소는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 해당 레지스트리 항목에서 패키지를 통해 보급 되는 서비스를 기반으로 한 통합된 개발 환경 (IDE)입니다. 모든 VSPackage 구현 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>합니다. 제공 하는 서비스를 일반적으로 사용 하는 VSPackage는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE proffers 자체의 일부 서비스 및 합니다.  
  
 VSPackage는 해당 메뉴 항목을 선언 하 고.vsct 파일을 통해 기본 항목 상태를 설정 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE는 VSPackage가 로드 될 때까지이 상태에서 메뉴 항목을 표시 합니다. 이후에 VSPackage 구현 된 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드는 메뉴 항목을 사용할지 여부를 합니다.  
  
## <a name="source-control-package-characteristics"></a>원본 제어 패키지 특성  
 VSPackage에 긴밀히 통합 되는 소스 제어 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]입니다.  
  
 VSPackage 의미 체계는 다음과 같습니다.  
  
- VSPackage 기능 구현 될 인터페이스 (의 `IVsPackage` 인터페이스)  
  
- UI 명령을 구현 (.vsct 파일 및 구현의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스)  
  
- 사용 하 여 VSPackage의 등록 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
  소스 제어 VSPackage와 통신 해야 이러한 다른 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 엔터티:  
  
- 프로젝트  
  
- 편집기  
  
- 솔루션  
  
- Windows  
  
- 실행 중인 문서 테이블  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>사용 될 수 있는 visual Studio 환경 서비스  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider 서비스  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP 인터페이스 구현 및 호출  
 소스 제어 패키지를 VSPackage로 이며 등록 된 다른 Vspackage 직접 상호 작용 하 여 따라서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 전체 범위의 소스 제어 기능을 제공 하기 위해 소스 제어 VSPackage 처리할 수 인터페이스 프로젝트 또는 셸에서에서 제공 합니다.  
  
 모든 프로젝트 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 구현 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 내에서 프로젝트를로 인식 되도록 하려면는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. 그러나이 인터페이스는 특수화 된 하지 소스 제어에 적합 합니다. 프로젝트 소스 아래에 있는 것으로 예상 되는 제어 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>합니다. 이 인터페이스는 사용 하 여 소스 제어 VSPackage 그 내용에 대해 프로젝트를 쿼리 하 고 문자 모양 및 바인딩 정보 (정보 아래에 있는 프로젝트의 디스크 위치와 서버 위치 간의 연결을 설정 하는 데 필요한 입력 소스 제어)입니다.  
  
 소스 제어 VSPackage 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, 다시 프로젝트를 소스 제어에 대 한 자체를 등록 하 고 해당 상태 문자 모양을 검색할 수 있습니다.  
  
 소스 제어 VSPackage를 고려해 야 하는 인터페이스의 전체 목록은 참조 하세요 [관련 서비스 및 인터페이스](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [관련 서비스 및 인터페이스](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
