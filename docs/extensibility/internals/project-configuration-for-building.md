---
title: 프로젝트 빌드에 대 한 구성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd9464105d777c0d488175ad67e1481022caa2d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328531"
---
# <a name="project-configuration-for-building"></a>빌드를 위한 프로젝트 구성
지정된 된 솔루션에 솔루션 구성 목록은 솔루션 구성 대화 상자에서 관리 됩니다.

 사용자 자신의 고유 이름을 사용 하 여 각 추가 솔루션 구성을 만들 수 있습니다. 사용자가 새 솔루션 구성을 만든 경우 IDE는 기본값으로 프로젝트 또는 디버그의 해당 구성 이름은 해당 이름이 없는 경우. 사용자는 필요한 경우 특정 요구 사항에 맞게 선택 영역을 변경할 수 있습니다. 프로젝트에 새 솔루션 구성의 이름과 일치 하는 구성을 지원 하는 경우이 동작에만 예외가입니다. 예를 들어, Project1 및 Project2를 솔루션에 포함 되어 있습니다. Project1에 디버그, 소매 및 MyConfig1 프로젝트 구성이 있습니다. Project2에 디버그, 소매 및 MyConfig2 프로젝트 구성이 있습니다.

 사용자가 만든 MyConfig2 이라는 새 솔루션 구성을 Project1는 기본적으로 디버그 구성을 솔루션 구성에 바인딩합니다. 또한 Project2 기본적으로 해당 MyConfig2 구성을 솔루션 구성에 바인딩합니다.

> [!NOTE]
> 바인딩은 대/소문자입니다.

 사용자가 선택 하는 경우는 **다중 선택** 항목 환경 구성 드롭다운 목록에서 사용 가능한 구성의 목록을 제공 하는 대화 상자를 표시 합니다.

 ![여러 구성을](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") 여러 구성

 이 대화 상자에서 사용자가 하나 이상의 구성 선택할 수 있습니다. 선택 하면 속성 페이지 대화 상자에 표시 되는 속성 값을 선택한 구성에 대 한 값의 교집합을 반영 합니다.

 참조 [솔루션 구성](../../extensibility/internals/solution-configuration.md) 추가 및 솔루션 및 프로젝트에 대 한 구성 이름 바꾸기와 관련 된 정보에 대 한 합니다.

 프로젝트 종속성 및 빌드 순서는 독립 솔루션 구성: 즉, 설정할 수 있습니다만 모든 솔루션의 프로젝트에 대 한 종속성 트리를 구성 합니다. 솔루션 또는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 하는 **프로젝트 종속성** 또는 **프로젝트 빌드 순서** 열립니다 옵션을 **프로젝트 종속성** 대화 상자. 열 수도 있습니다는 **프로젝트** 메뉴.

 ![프로젝트 종속성](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") 프로젝트 종속성

 프로젝트 종속성 프로젝트는 빌드 순서를 결정 합니다. 솔루션 내의 프로젝트 빌드는 및 빌드 순서를 수정 하려면 종속성 탭을 사용 하 여 정확한 순서를 확인 대화 상자에서 빌드 순서 탭을 사용 합니다.

> [!NOTE]
> 확인란이 선택 되어 있지만 흐리게 표시 되 면 목록에서 프로젝트를 지정 하는 명시적 종속성으로 인해 환경에서 추가한 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> , 인터페이스 및 변경할 수 없습니다. 예를 들어에서 프로젝트 참조에 추가 된 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 다른 프로젝트에 프로젝트 참조를 삭제 하 여만 제거할 수 있는 빌드 종속성이 자동으로 추가 합니다. 이렇게 종속성 루프를 만들 것 때문에 해당 확인란의 선택을 취소 되며 흐리게 표시 되 면 프로젝트를 선택할 수 없습니다 (예를 들어 Project1 Project2에 종속 됩니다 및 Project2 Project1에 종속 됩니다.)는 빌드가 중단 됩니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 빌드 프로세스는 일반적인 컴파일 및 단일 빌드 명령을 사용 하 여 호출 되는 링크 작업을 포함 합니다. 다른 두 개의 빌드 프로세스 지원 될 수 있습니다: 이전 빌드 및 구성의 출력 항목 변경 되었는지 여부를 확인 하려면 최신 검사에서 모든 출력 항목을 삭제할 정리 작업을 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 해당 개체를 반환 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (에서 반환 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) 빌드 프로세스를 관리 합니다. 를 실행 하는 동안 빌드 작업의 상태를 보고 하려면 구성 하 여 호출할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, 환경에서 구현 된 인터페이스 및 빌드 상태 이벤트에 관심이 있는 다른 모든 개체입니다.

 작성 되 면 구성 설정은 디버거 제어 실행할 수 있는지 여부를 확인 하려면 사용할 수 있습니다. 구성을 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 디버깅을 지원할 수 있습니다.

 프로젝트 종속성을를 구현한 후 자동화 모델을 통해 종속성을 프로그래밍 방식으로 조작할 수 있습니다. 호출 <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> 자동화 모델에서입니다. 솔루션 빌드 관리자 구성 및 해당 속성을 직접 조작 허용 하는 사용 가능한 VSIP API 수준 인터페이스가 없는 있습니다.

 또한 프로젝트 종속성 창에 표를 제공할 수 있습니다. 자세한 내용은 [속성 눈금 표시](../../extensibility/internals/properties-display-grid.md)합니다.

## <a name="see-also"></a>참고 항목
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [배포 관리를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)