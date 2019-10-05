---
title: Vspackage 문제 해결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62c1847e9ff476e364ed99cabc4b47a970c4c4da
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695501"
---
# <a name="troubleshooting-vspackages"></a>VSPackage 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음은 일반적인 문제는 문제를 해결 하기 위한 팁 및 VSPackage를 사용 하 여 있을 수 있습니다.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>부터 Visual Studio를 유지 하는 VSPackage의 문제를 해결 하려면  
  
- 시작 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 안전 모드에서.  
  
     시작 하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 프롬프트에서 안전 모드에서는 입력 **devenv.exe /safemode**합니다.  
  
     이 과정에 포함 된 Vspackage를 제외 하 고 없습니다 Vspackage 로르 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>VSPackage를 로드 하지 않습니다 하는 문제를 해결 하려면  
  
1. 일반적으로 실험적 레지스트리 루트를 실행 하려면 VSPackage 등록 된 레지스트리 루트를 사용 해야 합니다.  
  
     자세한 내용은 [의 실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다.  
  
2. 실험적 레지스트리 루트에서 실행 하는 VSPackage을 대상으로 하는 경우의 실험적 버전 실행 되 고 있는지 확인 하십시오 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
     실험 버전을 실행 하려면 명령 창에서 다음을 입력 합니다. **devenv /rootsuffix exp**합니다.  
  
3. VSPackage 레지스트리 항목을 확인 합니다.  
  
     자세한 내용은 [Vspackage 등록](internals/registering-vspackages.md) 하 고 [관리 Vspackage](../extensibility/managing-vspackages.md)합니다.  
  
4. 열기는 **출력** 인스턴스의 창 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSPackage를 로드 하는 실패 합니다. VSPackage 로드에 실패 한 이유에 대 한 정보는 해당 창에 표시 될 수 있습니다.  
  
    > [!NOTE]
    > 실험적 버전을 시작 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE) 검사 합니다 **출력** 두 버전의 창.  
  
5. 활동 로그를 검사 합니다.  
  
     자세한 내용은 [방법: 활동 로그를 사용 하 여](../extensibility/how-to-use-the-activity-log.md)입니다.  
  
6. IDE에 의해 throw 된 예외에 대 한 자세한 내용은 **예외** 에 **디버그** 예외를 사용 하도록 설정 하려면 메뉴. 에 **예외** 대화 상자에 대 한 자세한 내용을 보려는 예외 유형을 선택 합니다.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>VSPackage를 등록 하지 않는 문제를 해결 하려면  
  
1. VSPackage 어셈블리가 신뢰할 수 있는 위치에 있는지 확인 합니다. RegPkg 기본.net 보안 구성에 네트워크 공유와 같은 신뢰할 수 없는 또는 부분적으로 신뢰할 수 있는 위치에 어셈블리를 등록할 수 없습니다. 사용자가 신뢰할 수 없는 위치에서 프로젝트를 만들 때마다 경고가 나타나더라도 "이이 메시지를 다시 표시 않음" 확인란을 반복에서이 경고를 방지할 수 있습니다.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>명령을 표시 되지 않는 또는 명령을 클릭 하면 오류를 생성 하는 문제를 해결 하려면  
  
1. 다음을 입력 하 여 새롭거나 변경 된 메뉴 명령 및 IDE에 이미 병합 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 프롬프트: **devenv /rootsuffix Exp /setup**합니다.  
  
2. 했는지 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSPackage에 대 한 UI.dll를 찾을 수 있습니다.  
  
    1. 레지스트리의 패키지 섹션에서 VSPackage의 CLSID를 찾습니다.  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<version>* \Packages  
  
    2. SatelliteDll 하위 키를 제공한 경로가 올바른지 확인 합니다.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>예기치 않게 동작 하는 VSPackage는 문제를 해결 하려면  
  
1. 코드에 중단점을 설정합니다.  
  
     디버깅을 위한 좋은 출발점은 생성자 및 초기화 메서드입니다. 메뉴 명령과 같이 평가할 영역에서 중단점을 설정할 수도 있습니다. 중단점을 사용 하려면 디버거에서 실행 해야 합니다.  
  
    1. **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
    2. 에 **속성 페이지** 대화 상자를 선택 합니다 **디버그** 탭 합니다.  
  
    3. 에 **명령줄 인수** 개발 환경의 루트 접미사를 입력 하는 VSPackage 대상입니다. 예를 들어, 실험적 빌드를 선택 하려면 입력: **RootSuffix Exp**합니다.  
  
    4. 에 **디버그** 메뉴에서 클릭 **디버깅 시작** 하거나 F5 키를 누릅니다.  
  
        > [!NOTE]
        > 프로젝트를 디버깅 하는 경우 만들거나 이제 프로젝트의 기존 인스턴스를 로드 합니다.  
  
2. 활동 로그를 사용 합니다.  
  
     주요 지점에서 활동 로그에 정보를 기록 하 여 VSPackage 동작을 추적 합니다. 이 기술은 소매 환경에서 VSPackage를 실행할 때 특히 유용 합니다. 자세한 내용은 [방법: 활동 로그를 사용 하 여](../extensibility/how-to-use-the-activity-log.md)입니다.  
  
3. 공용 기호를 사용 합니다.  
  
     디버깅 하는 동안 가독성을 높이기 디버거에 기호를 연결할 수 있습니다.  
  
    1. **도구/옵션** 메뉴에서로 이동 합니다 **디버깅/기호** 대화 상자.  
  
    2. 이 추가 **기호 파일 (.pdb) 위치**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3. 성능 향상을 위해 예를 들어 기호 캐시 폴더를 지정 합니다.  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>누락 된 VSPackage 나 해당 종속성 중 하나를 해결 하려면  
  
1. 관리 코드에 대 한 참조 경로가 올바른지 확인 합니다.  
  
   1. **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
   2. 선택 합니다 **참조** 탭에 **속성 페이지** 모든 경로 올바른 대화 상자 하 고 있는지 확인 합니다. 사용할 수 있습니다 합니다 **개체 브라우저** 참조 된 개체를 찾아볼 수 있습니다.  
  
        관리 코드에 대해 사용할 수 있습니다 합니다 [Fuslogvw.exe (어셈블리 바인딩 로그 뷰어)](https://msdn.microsoft.com/library/e32fa443-0778-4cc3-bf36-5c8ea297d296) 실패 한 어셈블리 로드의 세부 정보를 표시 합니다.  
  
2. 비관리 코드에서 VSPackage의 CLSID를 찾기는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CLSID 레지스트리 노드:  
  
    HKLM\Software\Microsoft\Visual Studio\\*\<version>* \CLSID  
  
   InprocServer32 항목 VSPackage dll의 올바른 경로가 있는지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [VSPackage](../extensibility/internals/vspackages.md)
