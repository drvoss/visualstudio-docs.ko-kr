---
title: VSPackage 설치 시나리오 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696752"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 설치 시나리오
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

유연 하 게 VSPackage 설치 관리자를 디자인 하는 것이 반드시 합니다. 예를 들어, 보안 패치를 나중에 해제 해야 할 수 있습니다 또는 철저 한-side-by-side 버전 관리를 지원 해야 비즈니스 전략을 변경할 수 있습니다.  
  
 [Visual Studio의 여러 버전을 지 원하는](../../extensibility/supporting-multiple-versions-of-visual-studio.md), 장점 및 지원-나란히 설치의 문제를 확인할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage의 공유 또는 side-by-side-설치 합니다. 즉, side-by-side-Vspackage 가장 유연성을 제공 하의 새 기능을 지원 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
 이 항목에서 설명 하는 시나리오에만 선택할 수 없지만 모범 사례를 제안된으로 표시 됩니다.  
  
## <a name="components-privacy-and-sharing"></a>구성 요소, 개인 정보 보호 및 공유  
  
##### <a name="make-your-components-independent"></a>구성 요소를 독립적으로 만들기  
 식별 하 고 구성 요소를 채울 할당을 `GUID`, 구성 요소를 배포 하 고, 해당 구성을 변경할 수 없습니다. 결과 구성 요소를 새 구성 요소를 새 해야 구성 요소의 컴퍼지션을 변경한 경우 `GUID`합니다. 각 구성 요소 독립적이 고 독립적일 단위를 만들어 가장 높은 버전 관리 유연성을 제공 되어 이러한 팩트를 제공 합니다. 구성 요소를 제어 하는 규칙에 대 한 자세한 내용은 참조 하세요. [구성 요소 코드를 변경](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) 하 고 [되나요 구성 요소 규칙은 손상?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)합니다.  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>구성 요소에서 공유 및 전용 리소스를 혼합 하지 마세요  
 참조 횟수는 구성 요소 수준에서 발생합니다. 따라서 하나의 구성 요소에서 공유 및 전용 리소스를 혼합 수 없도록 또한 공유 리소스를 덮어쓰지 않고 실행 파일과 같은 전용 리소스를 업데이트 합니다. 이 시나리오는 이전 버전과 호환성 문제 만들고 side-by-side-기능을 만들지 못하게 제한 합니다.  
  
 사용 하 여 VSPackage를 등록 하려면 레지스트리 값을 사용 하는 예를 들어 합니다 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 유지할지 구성 요소에서 사용 하 여 VSPackage를 등록 하는 데 하나에서 별도 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 공유 파일 또는 레지스트리 값에는 아직 다른 구성 요소에서 이동합니다.  
  
## <a name="scenario-1-shared-vspackage"></a>시나리오 1: 공유 VSPackage  
 이 시나리오에서는 공유 VSPackage (여러 버전의 지원 하는 단일 바이너리 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)])는 Windows Installer 패키지에 제공 합니다. 각 버전을 사용 하 여 등록 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 사용자가 선택할 수 있는 기능에 의해 제어 됩니다. 기능을 분리에 할당 하는 경우 각 구성 요소를 선택할 수 있음을 개별적으로 설치 또는 제거, VSPackage의 다른 버전으로 통합 하는 컨트롤에서 사용자를 두면 의미 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. (참조 [Windows Installer 기능](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) 기능을 사용 하 여 Windows Installer 패키지에 대 한 자세한 내용은 합니다.)  
  
 ![VS 공유 VSPackage 그래픽](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
공유 VSPackage 설치 관리자  
  
 그림에 표시 된 것과 같이 공유 구성 요소는 항상 설치 Feat_Common 기능의 일부로 수행 됩니다. 만들어 Feat_VS2002 기능과 Feat_VS2003 표시를 사용자가 선택할 수 설치 시의 어떤 버전으로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 를 통합 하는 VSPackage를 원합니다. 사용자를 추가 하 여 기능에는 경우 추가 또는 제거의 서로 다른 버전의 VSPackage 등록 정보를 제거 합니다. Windows Installer 유지 관리 모드를 이용할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
> [!NOTE]
> 기능의 표시 열을 0으로 설정 숨겨집니다. 예: 1, 낮은 수준 열 값을 항상 설치를 확인 합니다. 자세한 내용은 [installlevel과 속성](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) 하 고 [기능 테이블](https://msdn.microsoft.com/library/aa368585.aspx)합니다.  
  
## <a name="scenario-2-shared-vspackage-update"></a>시나리오 2: 공유 VSPackage 업데이트  
 이 시나리오에서 시나리오 1에서에서 VSPackage 설치 관리자의 업데이트 된 버전이 제공 됩니다. 토론을 위해이 업데이트는 지원에 대 한 추가 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 있지만 간단한 보안 패치 또는 버그 수정을 서비스 팩 수도 있습니다. 최신 구성 요소를 설치 하는 것에 대 한 Windows Installer 규칙 시스템에 이미 변경 되지 않은 구성 요소는 다시 복사 되지 필요 합니다. 이 경우 버전 1.0 이미 시스템과 Comp_MyVSPackage.dll 업데이트 된 구성 요소를 덮어쓰게 Feat_VS2005 Comp_VS2005_Reg 해당 구성 요소를 사용 하 여 새 기능을 추가 하도록 선택할 수 있도록 합니다.  
  
> [!CAUTION]
> 여러 버전의 VSPackage가 공유 될 때마다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], VSPackage의 후속 릴리스에서 이전 버전과 이전 버전과의 호환성을 유지 관리 하는 반드시 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]입니다. 이전 버전과 호환성을 유지할 수 없는 경우-병렬, 개인 Vspackage를 사용 해야 합니다. 자세한 내용은 [Visual Studio의 여러 버전을 지 원하는](../../extensibility/supporting-multiple-versions-of-visual-studio.md)합니다.  
  
 ![VS 공유 VS 패키지 업데이트 이미지](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
VSPackage 업데이트 설치 관리자를 공유합니다.  
  
 이 시나리오에는 새 VSPackage 설치 관리자의 부 업그레이드에 대 한 Windows 설치 관리자의 지원 활용 하 고 표시 합니다. 사용자가 버전 1.1을 설치 하기만 하 고 1.0 버전 업그레이드 합니다. 그러나 버전 1.0 시스템에 필요는 없습니다. 동일한 설치 관리자가 버전 1.1 버전 1.0이 없는 시스템에 설치 하는 것입니다. 이 방식으로 부 버전 업그레이드를 위해 장점은 업그레이드 설치 관리자 및 전체 제품 설치 관리자를 개발 하는 작업을 통해 필요 하다 고 한다는 점입니다. 하나의 설치 관리자는 두 가지 작업을 수행합니다. 보안 수정 프로그램 또는 서비스 수 대신 활용 Windows Installer 패치를 압축 합니다. 자세한 내용은 [패치 및 업그레이드](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)합니다.  
  
## <a name="scenario-3-side-by-side-vspackage"></a>시나리오 3: Side-by-side-VSPackage  
 이 시나리오에서는 두 명의 VSPackage 설치 관리자-Visual Studio.NET 2003의 각 버전에 대 한 하나 및 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 각 설치 관리자 설치--나란히 또는 private로 VSPackage (특히 작성 및 특정 버전의 설치는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). 각 VSPackage는 자체 구성 요소입니다. 따라서 각 서비스할 수 있습니다 개별적으로 패치 또는 유지 관리를 사용 하 여 해제 합니다. VSPackage DLL 버전별 이제 이기 때문에 동일한 구성 요소는 DLL과 해당 등록 정보를 포함 하도록 안전 합니다.  
  
 ![VS 쪽&#45;에서&#45;쪽 VS 패키지 그래픽](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Side-by-side-VSPackage 설치 관리자  
  
 각 설치 관리자에는 두 명의 설치 관리자 간에 공유 되는 코드도 포함 됩니다. 공유 코드를 공용 위치에 설치 되어 있으면 설치.msi 파일을 모두 설치 됩니다 공유 코드를 한 번만. 두 번째 설치 관리자에는 구성 요소에서 참조 횟수를 증가 시킵니다. 참조 횟수를 Vspackage 중 하나를 제거 하는 경우 공유 코드를 다른 VSPackage에 대 한 유지 하도록 보장 합니다. 두 번째 VSPackage 에서도 제거 되는 공유 코드가 제거 됩니다.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>시나리오 4: Side-by-side-VSPackage 업데이트  
 이 시나리오에서는 VSPackage에 대 한 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] 발생 하면 보안상에서 취약점으로 인 한 해야 할 업데이트를 실행 합니다. 시나리오 2와 같이 보안 픽스를 포함할 수 있을 뿐만 아니라 위치에 이미 보안 픽스를 사용 하 여 새 설치를 배포한 기존 설치를 업데이트 하는 새.msi 파일을 만들 수 있습니다.  
  
 이 경우에 VSPackage는 전역 어셈블리 캐시 (GAC)에 설치 된 관리 되는 VSPackage입니다. 보안 픽스를 포함 하도록 다시 작성할 때 어셈블리 버전 번호의 수정 번호 부분을 변경 해야 합니다. 등록 정보를 새 어셈블리 버전 번호를 덮어쓰는 이전 버전에 대 한 일으키는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 고정된 어셈블리를 로드 합니다.  
  
 ![VS 쪽&#45;에서&#45;쪽 VS 패키지 업데이트 그래픽](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Side-by-side-VSPackage에 대 한 업데이트 설치 관리자  
  
 **참고** side-by-side-어셈블리의 배포에 대 한 자세한 내용은 참조 하세요. [배포를 단순화 및.NET Framework를 사용 하 여 DLL 지옥 해결](https://msdn.microsoft.com/library/ms973843.aspx)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [여러 버전의 Visual Studio 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
