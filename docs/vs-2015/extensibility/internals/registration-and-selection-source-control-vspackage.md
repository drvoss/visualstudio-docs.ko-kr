---
title: 등록 및 선택 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 692f2a9f34edd41839179f7229e079ec8e791800
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185829"
---
# <a name="registration-and-selection-source-control-vspackage"></a>등록 및 선택(소스 제어 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어 VSPackage를 노출 하려면 등록 해야 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 둘 이상의 소스 제어 VSPackage를 등록 하는 경우 사용자가 적절 한 시간에 로드 하는 VSPackage 선택할 수 있습니다. 참조 [Vspackage](../../extensibility/internals/vspackages.md) Vspackage 및 등록 하는 방법에 대 한 자세한 내용은 합니다.  
  
## <a name="registering-a-source-control-package"></a>원본 제어 패키지 등록  
 소스 제어 패키지 등록 되도록는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 환경 지원 되는 기능은 해당 하 고 쿼리를 찾을 수 있습니다. 이 지연 로드 구성표를 필수 명령 또는 해당 기능 또는 명시적으로 요청 하는 경우에 패키지의 인스턴스에 생성 됩니다.  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 버전별 레지스트리 키에 정보를 저장 하는 Vspackage\\*X.Y*여기서 *X* 주 버전 번호 이며 *Y* 부 버전 번호입니다. Side-by-side-여러 버전의 설치를 지 원하는 기능을 제공 하는이 이렇게 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 사용자 인터페이스 (UI) 소스 제어 Vspackage 뿐만 아니라 여러 설치한 소스 제어 플러그 인 (소스 제어 어댑터 패키지)를 통해 중에서 선택 지원 합니다. 있을 수 있습니다만 하나의 활성 원본 제어 플러그 인 또는 VSPackage 번. 그러나 아래와 같이 IDE 자동 솔루션 기반 패키지 교환 메커니즘을 통해 원본 제어 플러그 인 및 Vspackage 간의 전환을 허용 합니다. 이 선택 메커니즘을 사용 하도록 설정 하려면 소스 제어 VSPackage 부분 몇 가지 요구 사항이 있습니다.  
  
### <a name="registry-entries"></a>레지스트리 항목  
 소스 제어 패키지를 개인 guid가 세 개 필요합니다.  
  
- 패키지 GUID: 원본 제어 구현 (이 단원의 ID_Package 라고 함)를 포함 하는 패키지에 대 한 기본 GUID입니다.  
  
- 소스 제어 GUID: 이 소스 제어는 Visual Studio 원본 제어 스텁을 등록 하는 데 사용 되는 VSPackage에 대 한 GUID 및 명령 UI 컨텍스트의 GUID로도 사용 됩니다. 원본 제어 서비스 GUID를 GUID 소스 제어에 등록 됩니다. 예제에서는 소스 제어 GUID ID_SccProvider 라고 합니다.  
  
- 소스 제어 서비스 GUID: 개인 서비스 (이 단원의 SID_SccPkgService 라고 함)는 Visual Studio에서 사용 되는 GUID입니다. 그 뿐 아니라 소스 제어 패키지 하 고 Vspackage에서 도구 창에 대 한 다른 Guid를 정의 해야 합니다.  
  
  다음 레지스트리 항목을 소스 제어 VSPackage에서 이루어져야 합니다.  
  
|키 이름|항목|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(기본값) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(기본값) = rg_sz:\<패키지의 이름 ><br /><br /> Service = rg_sz:{SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(기본값) = rg_sz: #\<지역화 된 이름에 대 한 리소스 ID ><br /><br /> 패키지 rg_sz =: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (유의 키 이름을 `SourceCodeControl`에서 이미 사용 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에 대 한 선택 항목으로 사용할 수 없는 \<PackageName >.)|(기본값) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>소스 제어 패키지를 선택합니다.  
 여러 원본 제어 플러그 인 API 기반 플러그 인 및 소스 제어 Vspackage를 동시에 등록할 수 있습니다. 소스 제어 플러그 인 또는 VSPackage를 선택 하는 프로세스를 사용 해야 하는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 플러그 인을 로드 또는 적절 한 경우에는 VSPackage 및 불필요 한 구성 요소를 로드 하 여 필요 없을 때까지 연기할 수 있습니다. 또한 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 메뉴 항목, 대화 상자 및 도구 모음을 포함 하는 다른 비활성 Vspackage에서 모든 UI를 제거 하 고 활성 VSPackage에 대 한 UI를 표시 해야 합니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다음 작업 중 하나를 수행할 때 소스 제어 VSPackage를 로드 합니다.  
  
- 솔루션 (솔루션은 소스 제어에서) 하는 경우 열려 있습니다.  
  
   솔루션 또는 소스 제어에서 프로젝트를 열 때 IDE 하면 소스 제어 VSPackage 로드 되도록 해당 솔루션에 대해 지정 되었습니다.  
  
- 소스 제어 VSPackage의 메뉴 명령 실행 됩니다.  
  
  (지연 된 로드로 라고도)를 사용 하는 소스 제어 VSPackage를 실제로 하는 경우에 필요한 모든 구성 요소를 로드 해야 합니다.  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>자동 솔루션 기반 VSPackage 교환  
 소스 제어 Vspackage를 수동으로 바꿀 수 있습니다 통해 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **옵션** 대화 상자의 합니다 **소스 제어** 범주입니다. 자동 솔루션 기반 패키지를 특정 솔루션에 대 한 지정 된 소스 제어 패키지를 해당 솔루션을 열 때 자동으로 활성으로 설정 되는 의미를 교환 합니다. 모든 원본 제어 패키지를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>입니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 둘 다 전환 처리 원본 제어 플러그 인 (소스 제어 플러그 인 API를 구현) 및 소스 제어 Vspackage입니다.  
  
 소스 컨트롤 어댑터 패키지를 사용 하 여 모든 원본 제어 플러그 인 API를 기반으로 전환 플러그 인입니다. 중간 소스 제어 어댑터 패키지로 전환 하 고 원본 제어 플러그 인 확인 프로세스를 사용자에 게는 활성 또는 비활성으로 설정 합니다. 어댑터 패키지는 모든 소스 제어 플러그 인 활성화 된 경우에 항상 활성입니다. 단순히 로드와 플러그 인 DLL 언로드 두 원본 제어 플러그 인 금액 사이의 전환을 말합니다. 하지만 적절 한 VSPackage를 로드 하는 IDE 상호 작용을 포함 소스 제어 VSPackage로 전환 합니다.  
  
 소스 제어 VSPackage는 솔루션 파일에는 VSPackage의 레지스트리 키 및 모든 솔루션을 열 때 호출 됩니다. 솔루션을 열면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 레지스트리 값을 찾아 적절 한 소스 제어 VSPackage를 로드 합니다. 모든 소스 제어 Vspackage 위에 설명 된 레지스트리 항목이 있어야 합니다. 소스 제어 중인 솔루션은 특정 소스 제어 VSPackage 사용 하 여 연결 중인으로 표시 됩니다. 소스 제어 Vspackage 구현 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 자동 솔루션 기반 VSPackage 교체를 사용 하도록 설정 합니다.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio 패키지 선택 및 전환에 대 한 UI  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 플러그 인 선택 항목을 소스 제어 VSPackage에 대 한 UI를 제공 합니다 **옵션** 대화 상자의 합니다 **소스 제어** 범주입니다. VSPackage를 사용자가 현재 소스 제어 플러그 인을 선택할 수 있습니다. 드롭다운 목록에 포함 됩니다.  
  
- 모든 소스 제어 패키지 설치  
  
- 모든 원본 제어 플러그 인 설치  
  
- "None" 옵션을 소스 코드 제어를 사용 하지 않도록 설정 하는  
  
  현재 소스 제어 선택 UI만 표시 됩니다. VSPackage 선택 UI를 숨기고 이전 VSPackage에 대 한 새 UI를 보여 줍니다. 활성 VSPackage에서 사용자별으로 선택 됩니다. 사용자의 여러 복사본이 있으면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 동시에 열을 각각 다른 활성 VSPackage를 사용할 수 있습니다. 각 사용자의 개별 인스턴스를 가질 수 있습니다 여러 사용자가 동일한 컴퓨터에 로그온 하는 경우 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 각각 다른 활성 VSPackage를 사용 하 여 엽니다. 때의 여러 인스턴스 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 소스 제어 VSPackage 마지막 열려 있는 솔루션은 기본 소스 제어 VSPackage를 다시 시작 시 활성 설정에 대 한 활성화 된 사용자가 닫힙니다.  
  
  이전 버전과 달리 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], IDE 다시 시작을 소스 제어 Vspackage를 전환 하려면 유일한 방법은 더 이상. 자동으로 VSPackage 선택이 됩니다. 패키지를 전환 하려면 Windows 사용자 권한 (관리자 또는 Power User 없습니다) 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [기능](../../extensibility/internals/source-control-vspackage-features.md)   
 [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackage](../../extensibility/internals/vspackages.md)
