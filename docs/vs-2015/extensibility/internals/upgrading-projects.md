---
title: 프로젝트 업그레이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441247"
---
# <a name="upgrading-projects"></a>프로젝트 업그레이드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 모델의 버전 간에 변경 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다음 해야 최신 버전에서 실행할 수 있도록 프로젝트 및 솔루션 업그레이드 됩니다. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 지원을 구현 하기 위해 업그레이드 자체 프로젝트에서 사용할 수 있는 인터페이스를 제공 합니다.  
  
## <a name="upgrade-strategies"></a>업그레이드 전략  
 업그레이드를 지원 하기 위해 프로젝트 시스템 구현을 정의 하 고 업그레이드 전략을 구현 해야 합니다. 전략을 결정 하는 데,--나란히 (SxS) 백업, 복사 백업 중 하나 또는 둘 다 지원 하기 위해 선택할 수 있습니다.  
  
- SxS 백업 프로젝트를 직접 업그레이드에 적합 한 파일 이름 접미사를 예를 들어 추가 ".old" 해야 하는 파일만 복사를 의미 합니다.  
  
- 복사 백업 프로젝트를 사용자가 제공한 백업 위치에 모든 프로젝트 항목을 복사 하는 것을 의미 합니다. 원래 프로젝트 위치에서 관련 파일을 업그레이드 한 다음 됩니다.  
  
## <a name="how-upgrade-works"></a>업그레이드가 작동 하는 방법  
 이전 버전에서 만든 솔루션 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 최신 버전으로 업그레이드 해야 하는지 여부를 결정 하는 솔루션 파일 IDE 검사에서 열립니다. 업그레이드 하는 것이 필요 합니다 **업그레이드 마법사** 업그레이드 프로세스를 통해 사용자를 자동으로 시작 됩니다.  
  
 솔루션에서 업그레이드 필요한 경우 각 프로젝트 팩터리 해당 업그레이드 전략에 대해 쿼리 합니다. 전략은 프로젝트 팩터리 복사본 또는 SxS 백업 지원 하는지 여부를 결정 합니다. 정보를 보낼 합니다 **업그레이드 마법사**, 백업에 필요한 정보를 수집 하 고 사용자에 게 해당 옵션을 제공 합니다.  
  
### <a name="multi-project-solutions"></a>다중 프로젝트 솔루션  
 솔루션에 여러 프로젝트가 포함 되어 경우와 같이 업그레이드 전략 다를 경우는 C++ 만 지 원하는 SxS 백업 및 웹 프로젝트는 지원 복사본 백업만 프로젝트, 프로젝트 팩터리 업그레이드 전략을 협상 해야 합니다.  
  
 솔루션에 대 한 각 프로젝트 팩터리 쿼리 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>합니다. 그런 다음 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> 전역 프로젝트 파일에 업그레이드 해야 하는지 확인 하 고 지원 되는 업그레이드 전략을 확인할 수 있습니다. 합니다 **업그레이드 마법사** 후 호출 됩니다.  
  
 사용자가 마법사를 완료 한 후 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 실제 업그레이드를 수행 하려면 각 프로젝트 팩터리에서 라고 합니다. 백업을 용이 하 게 하려면 IVsProjectUpgradeViaFactory 메서드를 제공 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 서비스 업그레이드 프로세스의 세부 정보를 기록 합니다. 이 서비스를 캐시할 수 없습니다.  
  
 관련 된 모든 전역 파일을 업데이트 한 후 각 프로젝트 팩터리 프로젝트를 인스턴스화할 수 있습니다. 프로젝트 지원 되어야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 모든 관련 프로젝트 항목 업그레이드 메서드가 호출 됩니다.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드 SVsUpgradeLogger 서비스를 제공 하지 않습니다. 이 서비스를 호출 하 여 얻을 수 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>합니다.  
  
## <a name="best-practices"></a>모범 사례  
 사용 된 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 를 편집 하기 전에 파일을 편집할 수를 저장 하기 전에 저장할 수를 확인 하는 서비스입니다. 이렇게 하면 백업 및 소스 제어에서 프로젝트 파일, 권한 부족 등을 사용 하 여 파일을 처리 하는 업그레이드 구현 합니다.  
  
 사용 된 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 백업의 모든 단계 서비스 및 업그레이드 프로세스의 성공 여부에 대 한 정보를 업그레이드 합니다.  
  
 백업 및 프로젝트를 업그레이드 하는 방법에 대 한 자세한 내용은 IVsProjectUpgrade 주석을 vsshell2.idl에서 참조 하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트](../../extensibility/internals/projects.md)   
 [사용자 지정 프로젝트 업그레이드](../../misc/upgrading-custom-projects.md)   
 [프로젝트 항목 업그레이드](../../misc/upgrading-project-items.md)
