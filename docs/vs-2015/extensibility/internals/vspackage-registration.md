---
title: VSPackage 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a11f05edb4e7d476fdbcab82d365f9327dd4869a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685280"
---
# <a name="vspackage-registration"></a>VSPackage 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage advise 해야 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 는 설치 되 고 해야 로드할 수 있습니다. 이 프로세스는 레지스트리에서 정보를 작성 하 여 수행 됩니다. 설치 관리자의 일반적인 작업입니다.  
  
> [!NOTE]
> VSPackage 개발 중에 자체 등록을 사용 하 여 허용 되는 사례입니다. 그러나 [!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)] 파트너 설치의 일부로 자동으로 등록을 사용 하 여 해당 제품을 제공할 수 없습니다.  
  
 Windows Installer 패키지에 대 한 레지스트리 항목 레지스트리 테이블에서 일반적으로 수행 됩니다. 또한 레지스트리 테이블의 파일 확장명을 등록할 수 있습니다. 그러나 Windows Installer ProgId (프로그래밍 식별자), 클래스, 확장 및 동사 테이블을 통해 기본 제공 지원을 제공합니다. 자세한 내용은 [데이터베이스 테이블](https://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)합니다.  
  
 레지스트리 항목 선택한 side-by-side-전략에 대 한 적절 한 구성 요소와 연결 되어 있는지 확인 해야 합니다. 예를 들어, 공유 파일에 대 한 레지스트리 항목은 해당 파일의 Windows Installer 구성 요소를 사용 하 여 연결 해야 합니다. 마찬가지로, 버전별 파일에 대 한 레지스트리 항목은 해당 파일의 구성 요소를 사용 하 여 연결 해야 합니다. 그렇지 않으면을 설치 하거나 한 버전의 VSPackage 제거 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다른 버전의 VSPackage를 손상 시킬 수 있습니다. 자세한 내용은 참조 하세요. [Visual Studio의 여러 버전 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
> 등록을 관리 하는 가장 쉬운 방법은 개발자 등록 및 설치 시 등록에 대 한 동일한 파일에서 동일한 데이터를 사용 하는 것입니다. 예를 들어 일부 설치 관리자-개발 도구는 빌드 시.reg 형식의 파일을 사용할 수 있습니다. 개발자가 자신의 일상적인 개발에 대 한.reg 파일을 유지 하 고 디버깅을 동일한 파일에에서 포함 될 수 설치 관리자를 자동으로 합니다. 등록 데이터를 자동으로 공유할 수 없습니다, 하는 경우 설치 프로그램의 사본을 등록 데이터가 최신 인지 확인 해야 합니다.  
  
## <a name="registering-unmanaged-vspackages"></a>관리 되지 않는 Vspackage 등록  
 (Visual Studio 패키지 템플릿에 의해 생성 된 포함)는 관리 되지 않는 Vspackage 등록 정보를 저장할 ATL 스타일.rgs 파일을 사용 합니다. .Rgs 파일 형식 ATL에 특정 되며 일반적으로 사용할 수 없습니다-제작 도구를 설치 하는 것입니다. VSPackage 설치 관리자에 대 한 등록 정보를 별도로 유지 되어야 합니다. 예를 들어, 개발자가 파일을 보관할 수.reg 형태로.rgs 동기화 파일 변경 내용. .Reg 파일을 RegEdit를 사용 하 여 개발 작업에 대 한 병합 또는 설치 프로그램을 통해 사용할 수 있습니다.  
  
## <a name="registering-managed-vspackages"></a>관리 되는 Vspackage를 등록합니다.  
 RegPkg 도구에서 관리 되는 VSPackage 등록 특성을 읽고 정보 레지스트리 또는 설치 프로그램을 통해 사용할 수 있는 쓰기.reg 서식 파일에 직접 작성할 수 있습니다 하거나 합니다.  
  
> [!NOTE]
> RegPkg 도구 재배포 가능 패키지 되지 않으며 사용자의 시스템에서 VSPackage를 등록에 사용할 수 없습니다.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>이유는 Vspackage 등록 하지 않아야 자체 설치 시  
 VSPackage 설치 관리자 자체 등록에 의존 하지 않아야 합니다. 얼핏 보기에 자체 VSPackage에서에서 VSPackage의 레지스트리 값을 유지는 좋은 방법 처럼 보입니다. 개발자가 일상적인 작업에 대 한 사용 가능한 레지스트리 값이 필요 하 고 테스트를 별도 설치 관리자에서 레지스트리 데이터 복사본을 유지 하지 않으려면 의미입니다. 설치 관리자는 자체 레지스트리 값을 쓸 VSPackage에서 사용할 수 있습니다.  
  
 이론상에서 좋지만 자체 등록에 VSPackage 설치에 적합 하는 여러 결점이 있습니다.  
  
- 올바르게 설치, 제거, 설치 롤백 및 제거 rollback을 지원 하려면 자체 RegPkg를 호출 하 여 등록 하는 모든 관리 되는 VSPackage에 대 한 네 가지 사용자 지정 작업을 작성 해야 합니다.  
  
- 네 번째 사용자 지정 작업 RegSvr32 또는 RegPkg의 지원 되는 모든 버전에 대 한 호출을 만든 side-by-side-지원 접근 필요할 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
- 자체 등록된 키를 다른 기능이 나 응용 프로그램에서 사용할 경우 인해 방법이 없기 때문에 자체 등록 된 모듈을 사용 하 여 설치를 안전 하 게 롤백할 수 없습니다.  
  
- 경우에 따라 자체 등록 된 Dll 표시 되지 않거나 잘못 된 버전에 있는 보조 Dll에 연결 합니다. 반면에 Windows Installer 레지스트리 테이블을 사용 하 여 시스템의 현재 상태에 의존 하지 않고 Dll을 등록할 수 있습니다.  
  
- 형식 라이브러리와 같은 네트워크 리소스에 대 한 액세스 구성 요소가 원본에서 실행으로 지정 및 SelfReg 테이블에 포함 된 자동 등록 코드를 정의할 수 있습니다. 설치 구성 요소 관리자 설치 중에 실패를 발생할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [관리 되는 패키지 등록](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
