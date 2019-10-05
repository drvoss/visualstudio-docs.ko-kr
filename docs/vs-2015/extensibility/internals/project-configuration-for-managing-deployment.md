---
title: 배포를 관리 하는 것에 대 한 프로젝트 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5b16c3392e9432ba540130d45f6907de15b51ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429953"
---
# <a name="project-configuration-for-managing-deployment"></a>배포 관리를 위한 프로젝트 구성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

배포는 물리적으로 디버깅 및 설치에 대 한 예상 되는 위치를 빌드 프로세스에서 출력 항목을 이동 하는 행위. 예를 들어, 웹 응용 프로그램을 로컬 컴퓨터에서 작성 및 서버에 배치 될 수 있습니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트는 두 가지 방법을 지원 배포에 포함 될 수 있습니다.  
  
- 배포 프로세스의 주체로 합니다.  
  
- 배포 프로세스의 관리자입니다.  
  
  솔루션을 배포할 수 있는 배포 옵션을 구성 하려면 배포 프로젝트를 먼저 추가 해야 합니다. 배포 프로젝트 아직 없는 경우 묻는 경우를 만들려는 하나 선택 하면 **솔루션 배포** 에서 합니다 **빌드** 메뉴 또는 솔루션을 마우스 오른쪽 단추로 클릭 합니다. 클릭 하 **예** 열립니다는 **새 프로젝트 추가** 사용 하 여 대화 상자를 **원격 배포 마법사** 프로젝트를 선택 합니다.  
  
  원격 배포 마법사 (Windows 또는 웹) 응용 프로그램 종류, 프로젝트 출력 그룹을 포함 하도록, 포함 하려는 모든 추가 파일 및 배포 하려는 원격 컴퓨터에 대 한 요청 합니다. 마법사의 마지막 페이지에는 선택한 옵션의 요약이 표시 됩니다.  
  
  프로젝트에 대해서는 배포 프로세스를 다른 환경으로 이동 해야 하는 출력 항목을 생성 합니다. 이러한 출력 항목에 대 한 매개 변수로 설명의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 인터페이스를 해당 주 목적 그룹 출력에는 프로젝트를 허용 하는 경우. 구현에 관련 된 자세한 정보 `IVsProjectCfg2`를 참조 하세요 [출력에 대 한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-output.md)합니다.  
  
  배포 프로세스를 관리 하는 배포 프로젝트는 배포 명령을 사용 하도록 설정 하 고이 명령이 선택 될 때 응답 합니다. 배포 프로젝트를 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 배포를 수행 하 고 호출할 인터페이스를는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> 보고서에 대 한 인터페이스 상태 이벤트를 배포 합니다.  
  
  구성 빌드 또는 배포 작업에 영향을 주는 종속성을 지정할 수 있습니다. 빌드 또는 배포할 종속성은 빌드된 이거나 구성 자체를 작성 또는 배포 후 배포 하는 프로젝트입니다. 프로젝트 간에 빌드 종속성과 함께 설명 됩니다 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 인터페이스를 사용 하 여 종속성을 배포 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 인터페이스입니다. 자세한 내용은 [건물에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [관리 구성 옵션](../../extensibility/internals/managing-configuration-options.md)   
 [빌드에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)   
 [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
