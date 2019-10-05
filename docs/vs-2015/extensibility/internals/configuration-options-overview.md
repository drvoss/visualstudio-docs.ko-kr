---
title: 구성 옵션 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b37d93adbd2accb7a12fb176ab15aafc6914190
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441518"
---
# <a name="configuration-options-overview"></a>구성 옵션 개요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 여러 구성을 빌드할 수 있는, 디버깅, 실행 및/또는 배포를 지원할 수 있습니다. 구성에는 명명된 된 집합의 속성, 일반적으로 컴파일러 스위치 및 파일 위치를 사용 하 여 설명 된 빌드 형식입니다. 기본적으로 새 솔루션 디버그 및 릴리스 구성을 포함 합니다. 이러한 구성은 특정 솔루션 및/또는 프로젝트 요구 사항에 맞게 수정 또는 해당 기본 설정을 사용 하 여 적용할 수 있습니다. 일부 패키지는 두 가지 방법으로 빌드할 수 있습니다: ActiveX 편집기 또는 내부 구성 요소로 합니다. 그러나 여러 구성을 지원 하기 위해 프로젝트 필요가 없습니다. 사용 가능한 하나의 구성만 있으면 해당 구성은 모든 솔루션 구성에 매핑됩니다.  
  
 일반적으로 두 부분 구성에 이루어진-구성 이름 (예: 디버그 또는 릴리스) 및 플랫폼 설정 합니다. 구성의 플랫폼 이름은 API와 같은 경우 구성 대상에 설정 된 환경 또는 운영 체제 플랫폼을 식별 합니다. 사용자의 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ; 플랫폼을 만들 수 없습니다. 허용 하는 VSPackage 프로젝트 중에서 선택 해야 합니다. 패키지 작성자에 의해 설정 된 모든 조건에 따라 때 패키지의 개발 중에 만들어진 배달 플랫폼 사용자 설치 VSPackage로 원하는 모든 플랫폼 이름을 발생할 수 있습니다. 사용자 속성 페이지에서 인스턴스화되는 VSPackage를 통해 사용할 수 있게 하는 플랫폼 목록에서 선택한 수 있습니다.  
  
 일부 프로젝트 플랫폼의 개념을 지원 하므로 플랫폼 이름은 선택적입니다. 구성에 플랫폼 이름이 없는 경우 "해당 없음" 문자열은 UI에 표시 됩니다.  
  
 각 솔루션에 고유한 집합이 구성 하는 중에서 하나만 한 번에 활성화 될 수 있습니다. 솔루션 구성에는 각 프로젝트에서 둘 이상의 구성 집합이 있습니다. "개" 규정 솔루션 구성에서 프로젝트를 제외할 옵션 되었기 때문입니다. 사용자가 자신의 사용자 지정 솔루션 구성을 만들 수 있습니다.  
  
 다음 표에서 프로젝트에 대 한 일반적인 구성을 설치 합니다. 행 구성 이름과 플랫폼 이름 가진 열을 사용 하 여 레이블이 지정 됩니다.  
  
|구성 이름|플랫폼, Win32|플랫폼-Win64|  
|------------------------|----------------------|----------------------|  
|디버그|\<디버그 Win32 설정 >|\<디버그 Win64 설정 >|  
|Release|\<릴리스 Win32 설정 >|\<릴리스 Win64 설정 >|  
|MyConfig|N/A|\<MyConfig Win64 settings>|  
  
> [!NOTE]
> "Win32" 플랫폼을 대상으로 하는 프로젝트에서 Win32를 지원 하지 않는 한 제외 하는 "MyConfig" 솔루션 구성을 만들 수 없습니다.  
  
 솔루션에 대 한 활성 구성을 변경 해당 솔루션의 빌드, 실행, 디버깅 또는 배포할 프로젝트 구성 집합을 선택 합니다. 예를 들어, 릴리스 활성 솔루션 구성을 디버그로 변경 하면 해당 솔루션 내 모든 프로젝트가 솔루션의 디버그 구성에 표시 된 프로젝트의 구성을 사용 하 여 자동으로 작성 됩니다. 프로젝트의 구성도 일반적으로 명명 된 디버그 하지 않은 경우 사용자가 수동으로 변경한 내용은 환경의 Configuration Manager에서.  
  
 각 프로젝트에 대해 저장 된 솔루션 구성 속성을 프로젝트 이름, 프로젝트 구성 이름, 표시 여부를 작성 하거나 배포 하기 위해 플래그 및 플랫폼 이름을 포함 합니다. 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)합니다.  
  
 사용자 확인 하 고 계층 (솔루션 탐색기)에서 솔루션을 선택 하 여 속성 페이지를 열고 솔루션 구성 매개 변수를 설정할 수 있습니다. 마찬가지로, 볼 수 있으며 해당 프로젝트에 대 한 속성 페이지를 연 솔루션 탐색기에서 프로젝트를 선택 하 여 프로젝트 구성 매개 변수를 설정.  
  
 사용자는 필요한 경우 릴리스 구성 설정 및 나머지 모든 디버그 구성 설정으로 사용 하는 한 프로젝트를 빌드할 수도 있습니다. 자세한 내용은 [건물에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)합니다.  
  
 다음 다이어그램은 솔루션 및 프로젝트 구성을 지 원하는 인터페이스는 구현 하는 방법을 보여줍니다.  
  
 ![구성 인터페이스 그래픽](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
구성 인터페이스  
  
 이전 다이어그램에 관련 된 몇 가지 참고 사항:  
  
- `IDispatch` 구성 개체에 대 한 옵션으로 표시 됩니다. 구체적으로 찾아보기 개체에 대 한 구성 인터페이스가 선택 사항입니다.  
  
- `IVsDebuggableProjectCfg` 구성 개체의 선택적 표시 되어 있지만 디버깅 지원을 위해 필요 합니다.  
  
- `IVsProjectCfg2` 구성 개체의 경우 선택 사항으로 표시 하지만 지원 그룹화 하는 출력에 대 한 필요 합니다.  
  
- `Config Provider` 개체는 선택적 개체로 표시 되어 있지만를 구현 하는 옵션입니다. 프로젝트 개체 또는 별도 개체에 개체를 구현할 수 있습니다.  
  
- `IVsCfgProvider2` 지원 되는 플랫폼 및 구성 편집에 대 한 필요 합니다. `IVsCfgProvider` 해당 기능을 구현 하는 경우에 충분 합니다.  
  
- 동일한 클래스 실제로 어디서 든 별도 개체를 결합할 수 있으며 다이어그램에 표시 하는 이러한 개체 중 일부는 특정 디자인 요구 사항에 기반 합니다. 이 섹션의 다른 항목에서 단, 개체 및 해당 개체와 연결 된 인터페이스를 살펴봅니다 다이어그램에서 설명 하는 시나리오에 따라 합니다.  
  
- 특정 개체를 개별적으로 구현 됩니다. 예를 들어, 프로젝트 및 솔루션 빌드 별도 스레드 및 빌드에 대 한 구성을 설명 하는 개체에서 빌드 생활 편의 별도로 관리 하는 개체에서 발생 합니다.  
  
  자세한 내용은 사용 하 여 구성 개체 인터페이스에는 이전 다이어그램의 구성 공급자 개체 인터페이스를 참조 하세요 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)합니다. 또한 [건물에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md) 구성 작성기 및 빌드 종속성 개체 인터페이스에서 자세한 정보를 제공 하 고 [배포 관리에 대 한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-managing-deployment.md) 추가 구성 배포자 및 배포 종속성 개체에 연결 된 인터페이스를 설명 합니다. 마지막으로, [출력에 대 한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-output.md) 출력 그룹 및 출력 개체 인터페이스 및 구성에 종속 된 속성 보기 및 설정에 대 한 속성 페이지의 사용에 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [빌드에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)   
 [솔루션 구성](../../extensibility/internals/solution-configuration.md)
