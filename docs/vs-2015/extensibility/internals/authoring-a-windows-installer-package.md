---
title: Windows Installer 패키지를 authoring | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e92e965f0efe531f1618be509d0a7c9655c573d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682546"
---
# <a name="authoring-a-windows-installer-package"></a>Windows Installer 패키지 작성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

데이터 드라이브는 Windows Installer 모델입니다. 레지스트리 항목을 쓰고 파일을 복사 하는 절차 스크립트를 작성 하는 대신 예를 들어 만든 파일 및 레지스트리 데이터를 포함 하는 데이터베이스 테이블의 행과 열입니다.  
  
## <a name="database-entries"></a>데이터베이스 항목  
 VSPackage를 설치 하려면 Windows Installer 패키지를 다음 작업을 수행할 데이터베이스 항목을 포함 해야 합니다.  
  
- 검색 버전을 찾으려고 시스템 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage (AppSearch, CompLocator, RegLocator, DrLocator, 및 서명을 포함 하는 Windows Installer 테이블 사용)을 지원 합니다.  
  
- 지원 되는 버전이 없는 경우 설치를 취소 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 되어 VSPackage의 다른 시스템 요구를 충족 되지 않으면 (시작 조건 테이블 사용) 또는 합니다.  
  
- VSPackage 및 종속 파일 (directory, 구성 요소 및 파일 테이블 사용)을 설치 합니다.  
  
- VSPackage에 대 한 적절 한 정보 (레지스트리 테이블 사용)을 레지스트리에 추가 합니다.  
  
- VSPackage를 통합 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 호출한 **devenv.exe /setup** (CustomAction 테이블 사용).  
  
  자세한 내용은 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)합니다.  
  
## <a name="setup-tools"></a>도구 설정  
 다양 한 타사 설치 도구는 Windows Installer 패키지에 대 한 개발 환경을 제공 합니다. 두 가지 무료 도구는 다음과 같습니다.  
  
- InstallShield Limited Edition  
  
   Visual Studio를 통해 제한 된 버전의 InstallShield 가져올 수 있습니다 **새 프로젝트** 대화 합니다. 확장 **기타 프로젝트 형식** 선택한 후 **설치 및 배포**합니다. InstallShield 템플릿을 선택 합니다.  
  
- Windows Installer XML 도구 집합  
  
   도구 집합 XML 소스 파일에서 Windows Installer 패키지를 빌드합니다. 도구 집합 Microsoft 오픈 소스 프로젝트입니다. 소스 코드 및 실행 파일을 다운로드할 수 있습니다 [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix)합니다.  
  
  에 통합 하는 상용 제품에 대 한 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 를 사용 하 여는 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]를 참조 하십시오 [ https://marketplace.visualstudio.com/ ](https://marketplace.visualstudio.com/)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Installer를 사용하여 VSPackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
