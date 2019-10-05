---
title: VSPackage 개발을 위한 Devenv 명령줄 스위치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185272"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 개발을 위한 Devenv 명령줄 스위치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 개발자는 devenv.exe가 Visual Studio 통합된 개발 환경 (IDE)를 시작 하는 파일을 실행할 때 명령줄에서 작업을 자동화할 수 있습니다.  
  
 작업은 다음과 같습니다.  
  
- IDE 외부에서 미리 정의 된 구성에서 응용 프로그램을 배포 합니다.  
  
- 자동으로 사전 설정을 사용 하 여 프로젝트 빌드는 빌드 설정 또는 디버그 구성 합니다.  
  
- IDE 외부 모두에서 특정 한 구성에서 IDE를 로드 합니다. 또한 시작 시 IDE를 사용자 지정할 수 있습니다.  
  
## <a name="guidelines-for-switches"></a>스위치에 대 한 지침  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 문서-사용자 수준 devenv 명령줄 스위치를 설명합니다. 자세한 내용은 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)합니다. 또한 Devenv VSPackage 개발, 배포 및 디버깅을 사용 하 여 유용한 추가 명령줄 스위치를 지원 합니다.  
  
|명령줄 스위치|설명|  
|--------------------------|-----------------|  
|/safemode|시작 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 안전 모드에서 기본 IDE 및 서비스를 로드 합니다. /Safemode 스위치에서 로드 될 때 모든 타사 VSPackages 방지 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 시작, 안정적으로 실행 되도록 합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|  
|/resetskippkgs|문제 Vspackage를 로드 하지 않으려는 사용자가 추가한 로드 옵션을 건너뛸 모든 지웁니다 시작한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. SkipLoading 태그가 존재 VSPackage 로드 하는 사용 하지 않도록 설정 합니다. 태그를 지우면 VSPackage 로드 하는 다시 사용 하도록 설정 합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|  
|/rootsuffix|시작 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 대체 위치를 사용 하 여 합니다. 다음 명령을 만든 바로 가기에 실행 되는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 설치 관리자:<br /><br /> devenv /RootSuffix exp<br /><br /> 이 경우 exp 10.0 보다는 예를 들어 10.0Exp 특정 접미사를 사용 하 여 위치를 식별합니다. 실험적 인스턴스를 사용 하면 인스턴스의 별도로 VSPackage를 디버깅할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 코드를 작성 하는 합니다.<br /><br /> 이 스위치는 VSRegEx.exe를 사용 하 여 만든 위치를 식별 하는 모든 문자열을 사용할 수 있습니다. 자세한 내용은 [의 실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다.|  
|/splash|표시는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 정상적으로 시작 화면 및 주요 IDE를 표시 하기 전에 메시지 상자를 표시 합니다. 메시지 상자를 사용 하면 예를 들어 VSPackage 제품 아이콘을 확인 하려면 시작 화면을 연구 수 있습니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [명령줄 스위치를 추가합니다.](../extensibility/adding-command-line-switches.md)   
 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)
