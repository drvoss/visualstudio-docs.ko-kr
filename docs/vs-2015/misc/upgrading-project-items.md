---
title: 프로젝트 항목 업그레이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698694"
---
# <a name="upgrading-project-items"></a>프로젝트 항목 업그레이드
를 추가 하거나 구현 하지 않는 프로젝트 시스템 내에서 항목을 관리 하는 경우 프로젝트 업그레이드 프로세스에 참여 해야 합니다. Crystal Reports은 프로젝트 시스템에 추가할 수 있는 항목의 예입니다.  
  
 일반적으로 프로젝트 항목 구현자는 어떤 프로젝트 참조 및 기타 프로젝트 속성 있습니다 업그레이드 결정을 내리는 데 알아야 하므로 이미 완전히 인스턴스화된 및 업그레이드 된 프로젝트를 활용 하려고 합니다.  
  
### <a name="to-get-the-project-upgrade-notification"></a>프로젝트 업그레이드 알림을 가져올  
  
1. 설정 된 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> 프로젝트 항목 구현에서 플래그 (vsshell80.idl에 정의 됨). 이렇게 하면 프로젝트 항목이 자동으로 VSPackage 시 로드를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 셸 프로젝트 시스템 업그레이드 중임을 확인 합니다.  
  
2. Advise 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 인터페이스를 통해를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> 메서드.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 인터페이스 프로젝트 시스템 구현을 업그레이드 작업을 완료 하 고 새 업그레이드 된 프로젝트가 만들어진 후 발생 합니다. 시나리오에 따라를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 인터페이스 후 발생 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> 메서드.  
  
### <a name="to-upgrade-the-project-item-files"></a>프로젝트 항목 파일을 업그레이드 하려면  
  
1. 프로젝트 항목 구현에서 파일 백업 프로세스를 신중 하 게 관리 해야 합니다. Side-by-side-백업에 대 한 특히 적용이 위치는 `fUpgradeFlag` 의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 방법은로 설정 되어 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>".old"으로 지정 된 클라이언트측 파일에 따라 백업 된 파일 위치, 합니다. 시퀀스 번호가 오래 되어 프로젝트를 업그레이드 하는 경우 시스템 시간 보다 오래 된 백업된 파일을 지정할 수 있습니다. 또한 이러한이 방지 하기 위한 특정 단계를 수행 하지 않으면 덮어쓸 수 있습니다.  
  
2. 프로젝트 항목의 프로젝트 업그레이드에 대 한 알림을 가져옵니다 시점에는 **Visual Studio 변환 마법사** 계속 표시 됩니다. 메서드를 사용 해야 하므로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 마법사 UI 업그레이드 메시지를 제공 하는 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 변환 마법사](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [사용자 지정 프로젝트 업그레이드](../misc/upgrading-custom-projects.md)