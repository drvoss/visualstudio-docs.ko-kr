---
title: 프로젝트 구성 개체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725834"
---
# <a name="project-configuration-object"></a>프로젝트 구성 개체
프로젝트 구성 개체는 UI에 대 한 구성 정보 표시를 관리 합니다.

 ![Visual Studio 프로젝트 구성](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") 프로젝트 구성 속성 페이지

 프로젝트 구성 공급자는 프로젝트 구성을 관리 합니다. 환경 및 기타 패키지를 사용 하 여 프로젝트 구성에 대 한 정보에 액세스 하 고이에 대 한 정보를 검색 하려면 프로젝트 구성 공급자 개체에 연결 된 인터페이스를 호출 합니다.

> [!NOTE]
> 프로그래밍 방식으로 솔루션 구성 파일을 만들거나 편집할 수 없습니다. @No__t_0를 사용 해야 합니다. 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md) 을 참조 하세요.

 구성 UI에서 사용할 표시 이름을 게시 하려면 프로젝트가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>를 구현 해야 합니다. 환경에서는 환경 UI에 나열 될 구성 및 플랫폼 정보에 대 한 표시 이름을 가져오는 데 사용할 수 있는 `IVsCfg` 포인터 목록을 반환 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>를 호출 합니다. 활성 구성 및 플랫폼은 활성 솔루션 구성에 저장 된 프로젝트의 구성에 따라 결정 됩니다. @No__t_0 메서드를 사용 하 여 활성 프로젝트 구성을 검색할 수 있습니다.

 @No__t_0 개체는 필요에 따라 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> 개체를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 개체에 구현 하 여 정식 프로젝트 구성 이름을 기반으로 `IVsProjectCfg2` 개체를 검색할 수 있습니다.

 프로젝트 구성에 대 한 액세스 권한이 있는 환경 및 기타 프로젝트를 제공 하는 또 다른 방법은 프로젝트에서 하나 이상의 구성 개체를 반환 하는 `IVsCfgProvider2::GetCfgs` 메서드의 구현을 제공 하는 것입니다. 프로젝트는 `IVsProjectCfg`에서 상속 하 고 `IVsCfg`에서 상속 하 여 구성 관련 정보를 제공 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>를 구현할 수도 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>는 플랫폼 및 프로젝트 구성을 추가, 삭제 및 이름 변경 하는 기능을 지원 합니다.

> [!NOTE]
> Visual Studio는 더 이상 두 개의 구성 형식으로 제한 되지 않으므로 구성을 처리 하는 코드는 구성의 수에 대 한 가정을 사용 하 여 작성 하면 안 되며, 프로젝트가 하나만 있는 것으로 가정 하 여 작성 되어서는 안 됩니다. 구성은 반드시 디버그 또는 일반 정품 이어야 합니다. 이렇게 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>를 사용 하 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> 사용 되지 않습니다.

 @No__t_1에서 반환 된 개체에 대 한 `QueryInterface`를 호출 하면 `IVsCfgProvider2` 검색 됩니다. @No__t_2 프로젝트 개체에서 `QueryInterface`를 호출 하 여 `IVsGetCfgProvider`를 찾을 수 없는 경우 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`에 대해 반환 된 개체의 계층 루트 브라우저 개체 또는 구성에 대 한 포인터를 통해 `QueryInterface`를 호출 하 여 구성 공급자 개체에 액세스할 수 있습니다. `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`에 대해 공급자가 반환 되었습니다.

 `IVsProjectCfg2`는 주로 빌드, 디버그 및 배포 관리 개체에 대 한 액세스를 제공 하며 프로젝트에서 출력을 그룹화 할 수 있도록 합니다. @No__t_0 및 `IVsProjectCfg2`의 메서드를 사용 하 여 빌드 프로세스를 관리 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>를 구현 하 고 구성의 출력 그룹에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 포인터를 사용할 수 있습니다.

 그룹에 포함 된 출력 수가 구성에 따라 다를 수 있지만 프로젝트에서 지 원하는 각 구성에 대해 동일한 수의 그룹을 반환 해야 합니다. 또한 그룹은 구성에서 프로젝트 내의 구성으로의 식별자 정보 (정식 이름, 표시 이름 및 그룹 정보)가 동일 해야 합니다. 자세한 내용은 [출력에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)을 참조 하세요.

 디버깅을 사용 하도록 설정 하려면 구성이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>을 구현 해야 합니다. `IVsDebuggableProjectCfg`는 디버거가 구성을 시작할 수 있도록 프로젝트에서 구현 하는 선택적 인터페이스 이며 `IVsCfg` 및 `IVsProjectCfg`를 사용 하 여 구성 개체에서 구현 됩니다. 사용자가 F5 키를 눌러 디버거를 시작 하는 경우 환경에서 호출 합니다.

 `ISpecifyPropertyPages` 및 `IDispatch`는 속성 페이지와 함께 사용 되어 구성에 종속 된 정보를 검색 하 고 사용자에 게 표시 합니다. 자세한 내용은 [속성 페이지](../../extensibility/internals/property-pages.md)를 참조 하세요.

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
- [속성 페이지](../../extensibility/internals/property-pages.md)
- [솔루션 구성](../../extensibility/internals/solution-configuration.md)