---
title: MSI 및 VSIX 배포 DSL의 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3aaaf704e1ad8880ef7768ef9d7a23d325882a15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422567"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL의 MSI 및 VSIX 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 고유의 컴퓨터 또는 다른 컴퓨터에 도메인 특정 언어를 설치할 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 대상 컴퓨터에 이미 설치 되어 있어야 합니다.  
  
## <a name="which"></a> VSIX 및 MSI 배포 중에서 선택  
 도메인 특정 언어 배포 하는 방법은 두 가지가 있습니다.  
  
|메서드|이점|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장)|배포 하기 아주 간단 합니다. 복사 하 고 실행 합니다 **.vsix** DslPackage 프로젝트에서 파일입니다.<br /><br /> 자세한 내용은 참조 [를 설치 하 고는 VSX를 사용 하 여 DSL을 제거](#Installing)합니다.|  
|MSI (설치 관리자 파일)|-을 열도록 허용 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL 파일을 두 번 클릭 합니다.<br />-대상 컴퓨터에서 DSL 파일 형식을 사용 하 여 아이콘을 연결합니다.<br />-DSL 파일 형식을 사용 하 여 XSD (XML 스키마)에 연결합니다. 파일에 로드 되 면이 경고를 방지 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.<br /><br /> MSI를 만들려는 솔루션에는 설치 프로젝트를 추가 해야 합니다.<br /><br /> 자세한 내용은 [MSI 파일을 사용 하 여 DSL을 배포](#msi)합니다.|  
  
## <a name="Installing"></a> 설치 하 고는 VSX를 사용 하 여 DSL을 제거 합니다.  
 사용자가 내에서 DSL 파일을 열 수 DSL이이 메서드에 의해 설치 되 면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 있지만 Windows 탐색기에서 파일을 열 수 없습니다.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX를 사용 하 여 DSL을 설치 하려면  
  
1. 컴퓨터에서 찾을 합니다 **.vsix** DSL 패키지 프로젝트에서 만든 파일입니다.  
  
    1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **DslPackage** 프로젝트를 마우스 클릭 **Windows 탐색기에서 폴더 열기**합니다.  
  
    2. 파일을 찾습니다 **bin\\\*\\**_YourProject_**합니다. DslPackage.vsix**  
  
2. 복사 합니다 **.vsix** DSL을 설치 하려는 대상 컴퓨터에는 파일입니다. 이 컴퓨터는 사용 중인 컴퓨터이거나 다른 컴퓨터일 수 있습니다.  
  
    - 대상 컴퓨터의 버전 중 하나가 있어야 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Dsl 런타임에 지 합니다. 자세한 내용은 [시각화 및 모델링 SDK에 대 한 Visual Studio 버전 지원](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)합니다.  
  
    - 대상 컴퓨터의 버전 중 하나가 있어야 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에 지정 된 **DslPackage\source.extensions.manifest**합니다.  
  
3. 대상 컴퓨터에서 두 번 클릭 합니다 **.vsix** 파일입니다.  
  
     **Visual Studio 확장 설치 관리자** 에서 확장을 열고 설치합니다.  
  
4. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 시작하거나 다시 시작합니다.  
  
5. DSL을 테스트 하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL에 정의 된 확장명을 가진 새 파일을 만듭니다.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX를 사용 하 여 설치 된 DSL을 제거 하려면  
  
1. 에 **도구** 메뉴에서 클릭 **확장 관리자**합니다.  
  
2. **설치된 확장**을 확장합니다.  
  
3. DSL 정의 되어 있는 확장 하 고 클릭 한 다음 선택 **제거**합니다.  
  
   드물게 결함이 있는 확장은 로드되지 않고 오류 창에 보고서를 생성하지만 확장 관리자에 나타나지 않습니다. 이 경우 다음 위치에서 파일을 삭제하여 확장을 제거할 수 있습니다.  
  
   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
## <a name="msi"></a> DSL의 MSI 배포합니다.  
 DSL에 대해 MSI (Windows Installer) 파일에 정의 하 여 사용자가 Windows 탐색기에서 DSL 파일을 열 수를 허용할 수 있습니다. 파일 이름 확장명을 사용 하 여 아이콘 및 간단한 설명을 연결할 수 있습니다. 또한 MSI DSL 파일 유효성 검사에 사용할 수 있는 XSD가 설치할 수 있습니다. 원한다 면 동시에 설치할 MSI에 다른 구성 요소를 추가할 수 있습니다.  
  
 MSI 파일 및 기타 배포 옵션에 대 한 자세한 내용은 참조 하세요. [응용 프로그램 배포, 서비스 및 구성 요소](../deployment/deploying-applications-services-and-components.md)합니다.  
  
 설치 프로젝트를 추가 하면 MSI를 빌드하려면 사용자 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션입니다. 설치 프로젝트를 만드는 가장 쉬운 방법에서 다운로드할 수 있는 CreateMsiSetupProject.tt 템플릿을 사용 하는 것은 [VMSDK 사이트](http://go.microsoft.com/fwlink/?LinkID=186128)합니다.  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>DSL의 MSI 배포 하려면  
  
1. 설정 `InstalledByMsi` 확장 매니페스트에서 합니다. 이 설치 하 고 제외 하 고 MSI가 제거 되는 VSX 방지 합니다. 이 MSI에 다른 구성 요소를 포함 하는 경우 중요 합니다.  
  
   1. Open DslPackage\source.extension.tt  
  
   2. 앞에 다음 줄을 삽입 `<SupportedProducts>`:  
  
       ```  
       <InstalledByMsi>true</InstalledByMsi>  
       ```  
  
2. 만들거나 Windows 탐색기에서 DSL에 나타내는 아이콘을 편집 합니다. 예를 들어 편집 **DslPackage\Resources\File.ico**  
  
3. DSL의 다음 특성을 올바른지 확인 합니다.  
  
   - DSL 탐색기의 루트 노드를 클릭 하 고 속성 창에서 검토 합니다.  
  
       - 설명  
  
       - 버전  
  
   - 클릭 합니다 **편집기** 노드의 속성 창에서 클릭 **아이콘**합니다. 아이콘 파일에서 참조할 값을 설정 **DslPackage\Resources**와 같은 **File.ico**  
  
   - 에 **빌드** 메뉴를 열고 **Configuration Manager**, 같은 빌드 하려는 구성을 선택 하 고 **릴리스** 또는 **디버그** .  
  
4. 로 이동 [Visualization and Modeling SDK 홈 페이지](http://go.microsoft.com/fwlink/?LinkID=186128), 및를 **다운로드** 탭에서 다운로드 **CreateMsiSetupProject.tt**합니다.  
  
5. 추가 **CreateMsiSetupProject.tt** Dsl 프로젝트에 있습니다.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 라는 파일을 만듭니다 **CreateMsiSetupProject.vdproj**합니다.  
  
6. Windows 탐색기에서 Dsl 복사\\새 폴더로 *.vdproj 라는 설치 합니다.  
  
    (원하는 경우 이제 제외할 수 있습니다 CreateMsiSetupProject.tt Dsl 프로젝트에서.)  
  
7. **솔루션 탐색기**에 추가 **설치\\\*.vdproj** 기존 프로젝트로 합니다.  
  
8. 에 **프로젝트** 메뉴에서 클릭 **프로젝트 종속성**합니다.  
  
    에 **프로젝트 종속성** 대화 상자, 설치 프로젝트를 선택 합니다.  
  
    선택 상자 옆 **DslPackage**합니다.  
  
9. 솔루션을 다시 빌드합니다.  
  
10. Windows 탐색기에서 설치 프로젝트에서 빌드된 MSI 파일을 찾습니다.  
  
     DSL을 설치 하려는 컴퓨터에 MSI 파일을 복사 합니다. MSI 파일을 두 번 클릭 합니다. 설치 관리자를 실행합니다.  
  
11. 대상 컴퓨터에서 DSL의 파일 확장명을 가진 새 파일을 만듭니다. 확인 합니다.  
  
    - Windows 탐색기 목록 보기에서 파일의 아이콘 및 설명을 사용자가 정의한를 사용 하 여 표시 됩니다.  
  
    - 파일을 두 번 클릭 하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL 편집기에서 DSL 파일을 열어서 시작 합니다.  
  
    원한다 면 텍스트 템플릿을 사용 하는 대신 수동으로 설치 프로젝트를 만들 수 있습니다. 이 절차를 포함 하는 연습은의 5 장 참조를 [Visualization and Modeling SDK 랩](http://go.microsoft.com/fwlink/?LinkId=208878)합니다.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI에서 설치 된 DSL을 제거 하려면  
  
1. Windows, 엽니다는 **프로그램 및 기능** 제어판입니다.  
  
2. DSL을 제거 합니다.  
  
3. Visual Studio를 다시 시작합니다.
