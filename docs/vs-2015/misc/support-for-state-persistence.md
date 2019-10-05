---
title: 상태 지 속성에 대 한 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434321"
---
# <a name="support-for-state-persistence"></a>상태 지속성 지원
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 공통 개체의 상태를 유지할 수 있습니다. 예를 들어, 솔루션 및 프로젝트 속성에 저장 되며 솔루션 및 프로젝트 파일에서 복원 됩니다. 사용자 설정을 내보내고 설정 파일에서 가져올 수 있습니다.  
  
 Vspackage는 일반적으로 시스템 레지스트리 또는 현재 사용자 또는 컴퓨터에 대 한 응용 프로그램 데이터 폴더에서 로컬 저장소에 의존 합니다. 정수 및 문자열과 같은 저장소에 대 한 약간의 공간을 필요로 하는 값은 일반적으로 시스템 레지스트리에 저장 됩니다. 비트맵을 같은 저장소에 대 한 많은 공간을 필요로 하는 값은 파일에 저장 됩니다. 파일의 경로 자체 시스템 레지스트리에 저장 수 있습니다. 지 속성 메커니즘에는 로컬 저장소에 액세스할 수 있는 권한이 있어야 합니다.  
  
## <a name="support-for-locating-local-storage"></a>로컬 저장소를 찾기 위한 지원  
 <xref:Microsoft.VisualStudio.Shell.Package> 클래스는 현재 사용자 또는 컴퓨터에 대 한 시스템 레지스트리 또는 응용 프로그램 데이터 폴더에 상태 정보를 찾기 위한 지원을 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 에 대 한 로컬 컴퓨터의 레지스트리 루트의 경로 반환 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 예를 들어 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0Exp 합니다.  
  
 가져온 로컬 레지스트리 루트를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 서비스입니다. 가져올 때 사용할 수 없는 경우는 <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> VSPackage의 특성입니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 현재 사용자 (컴퓨터당)의 경로 반환에 대 한 레지스트리 루트 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 예를 들어 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp 합니다.  
  
 가져온 로컬 레지스트리 루트를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 서비스입니다. 사용할 수 없는 경우 VSPackage의 DefaultLocalRegistryRoot 특성에서 가져옵니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 에 대 한 공용 리포지토리로 사용 되는 디렉터리의 경로 반환 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 데이터는 현재 로밍 사용자에 대 한 예: C:\Documents and Settings\\*YourAccountName*\application VisualStudio\8.0Exp 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 에 대 한 공용 리포지토리로 사용 되는 디렉터리의 경로 반환 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 데이터는 현재 로밍하지 않은 사용자에 대 한 예: C:\Documents and Settings\\*YourAccountName*settings\application Data\Microsoft\VisualStudio\8.0Exp 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [VSPackage 상태](../misc/vspackage-state.md)