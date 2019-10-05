---
title: VSPackage 용 설치 디렉터리를 선택 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697242"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>VSPackage용 설치 디렉터리 선택
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 및 해당 지원 파일을 사용자의 파일 시스템에 있어야 합니다. 위치는 VSPackage는 관리 또는 사용자 선택을 확인 하 고-side-by-side 버전 관리 체계를 관리 되지 않는 하는지 여부에 따라 달라 집니다.  
  
## <a name="unmanaged-vspackages"></a>관리 되지 않는 Vspackage  
 비관리 VSPackage를 모든 위치에 설치할 수 있는 COM 서버를입니다. 등록 정보 위치를 정확 하 게 반영 해야 합니다. 설치 관리자 사용자 인터페이스 (UI) ProgramFilesFolder Windows Installer 속성의 하위 디렉터리와 같이 기본 위치를 제공 해야 합니다. 예를 들어:  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\  
  
 작은 부팅 파티션을 유지 하는 사용자에 맞게 기본 디렉터리를 변경 하 여 다른 볼륨에 응용 프로그램 및 도구를 설치 하려는 사용자를 허용 합니다.  
  
 Side-by-side-체계 버전 관리 VSPackage를 사용 하는 경우에 다른 버전을 저장 하위 디렉터리를 사용할 수 있습니다. 예를 들어:  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>관리되는 VSPackage  
 관리 되는 Vspackage는 또한 모든 위치에 설치할 수 있습니다. 그러나 항상 전역 어셈블리 캐시 (GAC)에 어셈블리 로드 시간을 줄이고에 설치 하는 것이 좋습니다. 관리 되는 Vspackage는 항상 강력한 이름의 어셈블리 이기 때문에 GAC에 설치 하는 강력한 이름 서명을 확인 설치 시에만 것을 의미 합니다. 파일 시스템의 다른 곳에 설치 하는 강력한 이름의 어셈블리에 로드 될 때마다 확인 해당 서명이 있어야 합니다. Regpkg 도구를 사용 하 여 GAC에 관리 되는 Vspackage를 설치할 때 **/assembly** 어셈블리의 강력한 이름을 가리키는 레지스트리 항목을 작성 하는 스위치입니다.  
  
 GAC와 다른 위치에서 관리 되는 Vspackage를 설치 하는 경우에 디렉터리 계층 구조를 선택 하는 것에 대 한 관리 되지 않는 Vspackage에 대 한 지정 된 이전 지시를 따릅니다. Regpkg 도구를 사용 하 여 **/codebase** VSPackage 어셈블리의 경로 가리키는 레지스트리 항목을 작성 하는 스위치입니다.  
  
 자세한 내용은 [등록 및 등록 취소 Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)합니다.  
  
## <a name="satellite-dlls"></a>위성 Dll  
 VSPackage 위성 Dll 규칙에 따라-특정 로캘에 대 한 리소스를 포함 하는-VSPackage 디렉터리의 하위 디렉터리에 있습니다. 로캘 ID (LCID) 값에 해당 하는 하위 디렉터리입니다.  
  
 [관리 Vspackage](../../extensibility/managing-vspackages.md) 나타냅니다는 레지스트리 항목 위치를 제어 하는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 실제로 VSPackage는 위성 DLL입니다. 그러나 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] LCID 값을 다음 순서에서에 대 한 명명 된 하위 디렉터리에 위성 DLL을 로드 하려고 합니다.  
  
1. 기본 LCID (VS LCID 영어에 대 한 예를 들어 \1033)  
  
2. 기본 보조 언어를 사용 하 여 LCID 기본값입니다.  
  
3. 시스템 기본값 LCID입니다.  
  
4. 기본 보조 언어를 사용 하 여 시스템 기본값 LCID입니다.  
  
5. 미국 영어 (. \1033 또는. \0x409).  
  
   VSPackage DLL 리소스 및 SatelliteDll\DllName 레지스트리 진입점을 포함 하는 경우 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 위의 순서를 로드 하려고 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [공유 및 버전 관리 Vspackage 중에서 선택](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Vspackage 관리](../../extensibility/managing-vspackages.md)   
 [관리 되는 패키지 등록](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
