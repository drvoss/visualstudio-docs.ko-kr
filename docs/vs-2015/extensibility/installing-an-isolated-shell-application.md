---
title: 격리 셸 응용 프로그램 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 60862d631d93788f10c372310da9eb3d181943ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414538"
---
# <a name="installing-an-isolated-shell-application"></a>격리 셸 응용 프로그램 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

셸 앱을 설치 하려면 다음 단계를 수행 해야 합니다.  
  
- 솔루션을 준비 합니다.  
  
- 응용 프로그램에 대 한 Windows Installer (MSI) 패키지를 만듭니다.  
  
- 설치 프로그램 부트스트래퍼를 만듭니다.  
  
  이 문서의 예제에서는 코드를 모두 제공 되는 [셸 배포 샘플](http://go.microsoft.com/fwlink/?LinkId=262245), MSDN 웹 사이트 코드 갤러리에서 다운로드할 수 있습니다. 샘플은 이러한 각 단계를 수행 하는 결과 보여줍니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 항목에 설명 된 절차를 수행 하려면 다음 도구는 컴퓨터에 설치 되어야 합니다.  
  
- The Visual Studio SDK  
  
- 합니다 [Windows Installer XML 도구 집합](http://go.microsoft.com/fwlink/?LinkId=82720) 버전 3.6  
  
  이 샘플은 Microsoft Visualization and Modeling SDK를 모든 셸에 필요한에 필요 합니다.  
  
## <a name="preparing-your-solution"></a>솔루션 준비  
 기본적으로 셸 템플릿을 VSIX 패키지를 빌드 하지만이 문제는 주로 디버깅용으로 사용 합니다. 셸 응용 프로그램을 배포 하는 경우 설치 하는 동안 다시 시작 하 고 레지스트리 액세스를 허용 하도록 MSI 패키지를 사용 해야 합니다. MSI 배포에 대 한 응용 프로그램을 준비 하려면 다음 단계를 수행 합니다.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>셸 응용 프로그램을 MSI 배포를 준비 하려면  
  
1. 솔루션에서 각.vsixmanifest 파일을 편집 합니다.  
  
     에 `Identifier` 요소를 추가 `InstalledByMSI` 요소 및 `SystemComponent` 요소를 다음 해당 값을 설정 하 고 `true`합니다.  
  
     이러한 요소를 사용 하 여 제거할에서 구성 요소 및 사용자 설치에 VSIX 설치 관리자를 방지 합니다 **확장 및 업데이트** 대화 상자.  
  
2. VSIX 매니페스트가 포함 된 각 프로젝트에 대해 MSI가 설치 하는 원본 위치에 내용을 출력 하는 빌드 작업을 편집 합니다. 빌드 출력에서 VSIX 매니페스트를 포함 하지만.vsix 파일을 빌드하지 마세요.  
  
## <a name="creating-an-msi-for-your-shell"></a>Shell 용 MSI 만들기  
 MSI 패키지를 빌드하려면를 사용 하는 권장 합니다 [Windows Installer XML 도구 집합](http://go.microsoft.com/fwlink/?LinkId=82720) 표준 설치 프로젝트를 보다 더 큰 유연성도 제공 합니다.  
  
 Product.wxs 파일에서 검색 요소 및 셸 구성 요소의 레이아웃을 설정 합니다.  
  
 그런 다음.reg 파일을 솔루션에 대 한와 ApplicationRegistry.wxs에서 레지스트리 항목을 만듭니다.  
  
### <a name="detection-blocks"></a>검색 블록  
 검색 블록은는 `Property` 검색할 필수 구성 요소를 지정 하는 요소 및 `Condition` 필수 구성 요소 컴퓨터에 없는 경우 반환할 메시지를 지정 하는 요소입니다. 예를 들어, 셸 응용 프로그램 재배포 가능 패키지, Microsoft Visual Studio Shell 필요 하 고 검색 블록에 다음 태그 예제와 유사 합니다.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>셸 구성 요소 레이아웃  
 대상 디렉터리 구조와 설치할 구성 요소를 식별 하는 요소를 추가 해야 합니다.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>셸 구성 요소의 레이아웃을 설정 하려면  
  
1. 계층 구조를 만들 `Directory` 을 나타내는 다음 예제와 같이 대상 컴퓨터의 파일 시스템을 만들려는 디렉터리의 모든 요소입니다.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     이러한 디렉터리에서 참조 하는 `Id` 설치 해야 하는 파일을 지정 하는 경우.  
  
2. 셸 및 셸 응용 프로그램 필요를 다음 예제와 같이 구성 요소를 식별 합니다.  
  
    > [!NOTE]
    > 일부 요소는 다른.wxs 파일의 정의를 참조할 수 있습니다.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. `ComponentRef` 요소는 현재 구성 요소에 필요한 파일을 식별 하는 다른.wxs 파일을 가리킵니다. 예를 들어 GeneralProfile HelpAbout.wxs에 다음 정의 합니다.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef` 요소는 사용자의 컴퓨터에 이러한 파일이 표시 되는 위치를 지정 합니다. 합니다 `Directory` 요소는 하위 디렉터리로 이동 하 고 각 것을 설치할 수 있도록 지정 `File` 요소 빌드된 또는 솔루션의 일부로 존재 하 고 해당 파일을 찾을 수 있는 MSI 파일을 만들면 식별 파일을 나타냅니다.  
  
    2. `ComponentGroupRef` 요소가 다른 요소 (또는 구성 요소 및 구성 요소 그룹)의 그룹을 나타냅니다. 예를 들어 `ComponentGroupRef` ApplicationGroup 아래에 정의 된 다음과 같은 Application.wxs 합니다.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > Shell (격리) 응용 프로그램에 대 한 필수 종속성 다음과 같습니다. DebuggerProxy, MasterPkgDef, 리소스 (특히:.winprf 파일) 응용 프로그램 및 PkgDefs 합니다.  
  
### <a name="registry-entries"></a>레지스트리 항목  
 Shell (격리) 프로젝트 템플릿을 포함 한 *ProjectName*.reg 파일 설치에 병합 하기 위해 레지스트리 키에 대 한 합니다. 이러한 레지스트리 항목에는 설치 및 정리 목적 모두에 대 한 MSI의 일부 여야 합니다. 또한 ApplicationRegistry.wxs에서 일치 하는 레지스트리 요소를 만들어야 합니다.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>MSI에 대 한 레지스트리 항목을 통합 하려면  
  
1. 에 **셸 사용자 지정** 폴더를 열고 *ProjectName*. 지역  
  
2. 대상 설치 디렉터리의 경로 사용 하 여 $RootFolder$ 토큰의 모든 인스턴스를 대체 합니다.  
  
3. 응용 프로그램에 필요한 다른 레지스트리 항목을 추가 합니다.  
  
4. ApplicationRegistry.wxs를 엽니다.  
  
5. 각 레지스트리 항목에 대해 *ProjectName*.reg, 다음 예제에 나온 것 처럼 해당 레지스트리 블록을 추가 합니다.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @="PhotoStudio DTE Object"|\<RegistryKey Id = 'DteClsidRegKey' 루트 'HKCR' 키 = =' $(차이 DteClsidRegKey)' 작업 'createAndRemoveOnUninstall' = ><br /><br /> \<RegistryValue Type='string' Name='@' Value='$(var.ShortProductName) DTE Object' /><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue 형식 = 'string' 이름 =' @' 값 ='[INSTALLDIR] $(차이 ShortProductName).exe ' / ><br /><br /> \</RegistryKey>|  
  
     이 예제에서는 Var.DteClsidRegKey 맨 위 행에 있는 레지스트리 키를 확인합니다. Var.ShortProductName 확인 `PhotoStudio`합니다.  
  
## <a name="creating-a-setup-bootstrapper"></a>설치 프로그램 부트스트래퍼를 만들어  
 모든 필수 구성 요소를 먼저 설치 된 경우에 완료 된 MSI 설치 됩니다. 최종 사용자 환경을 쉽게 하려면 수집 하 고 응용 프로그램을 설치 하기 전에 모든 필수 구성 요소를 설치 하는 설치 프로그램을 만듭니다. 성공적으로 설치를 위해 이러한 작업을 수행 합니다.  
  
- 관리자가 설치를 적용 합니다.  
  
- Visual Studio Shell (격리 모드) 설치 여부를 확인 합니다.  
  
- 순서로 하나 또는 둘 다 셸 설치 관리자를 실행 합니다.  
  
- 다시 시작 요청을 처리 합니다.  
  
- MSI를 실행 합니다.  
  
### <a name="enforcing-installation-by-administrator"></a>관리자가 설치를 적용합니다.  
 이 프로시저는 \Program Files와 같은 필요한 디렉터리에 액세스 하는 설치 프로그램을 사용 하도록 설정 하려면 필요\\합니다.  
  
##### <a name="to-enforce-installation-by-administrator"></a>관리자가 설치를 적용 하려면  
  
1. 설치 프로젝트에 대 한 바로 가기 메뉴를 열고 선택한 **속성**합니다.  
  
2. 아래 **구성 속성/링커/매니페스트 파일**설정 **UAC 실행 수준** 하 **requireAdministrator**합니다.  
  
     이 속성에 포함 된 매니페스트 파일에 관리자 권한으로 실행 되도록 프로그램 필요한 특성을 배치 합니다.  
  
### <a name="detecting-shell-installations"></a>셸 설치를 검색합니다.  
 Visual Studio Shell (격리)을 설치 해야 하는지 여부를 확인 하려면 먼저 HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install의 레지스트리 값을 확인 하 여 이미 설치 되어 있는지 확인 합니다.  
  
> [!NOTE]
> 또한 이러한 값 Product.wxs에 셸 검색 블록에서 읽어옵니다.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder Visual Studio Shell을 설치 하 고 파일을 확인할 수 있습니다 위치를 지정 합니다.  
  
 셸 설치를 검색 하는 방법의 예제를 참조 하세요.를 `GetProductDirFromReg` 셸 배포 예제의 Utilities.cpp의 함수입니다.  
  
 패키지는 Visual Studio 셸 중 하나 또는 두 컴퓨터에 설치 되지 않은 구성 요소를 설치 하는 목록에 추가 해야 합니다. 예제를 참조 하세요.를 `ComponentsPage::OnInitDialog` 셸 배포 예제의 ComponentsPage.cpp의 함수입니다.  
  
### <a name="running-the-shell-installers"></a>셸 설치 관리자를 실행합니다.  
 셸 설치 관리자를 실행 하려면 올바른 명령줄 인수를 사용 하 여 Visual Studio Shell 재배포 가능 패키지를 호출 합니다. 최소한 명령줄 인수를 사용 해야 합니다 **/norestart /q** 수행한 다음을 확인 하려면 반환 코드를 감시 하 고 있습니다. 다음 예제에서는 Shell (격리) 재배포 가능 패키지를 실행합니다.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Shell 언어 팩 설치 관리자를 실행합니다.  
 대신는 셸 또는 셸 요소를 설치 하는 언어 팩만 필요한을 찾으면 다음 예제와 같이 언어 팩을 설치할 수 있습니다.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>반환 값을 해독  
 일부 운영 체제에서는 Visual Studio Shell (격리 모드) 설치를 다시 시작을 해야 합니다. 이 조건에 대 한 호출의 반환 코드에서 확인할 수 있습니다 `ExecCmd`합니다.  
  
|반환 값|설명|  
|------------------|-----------------|  
|ERROR_SUCCESS|설치가 완료 되었습니다. 이제 응용 프로그램을 설치할 수 있습니다.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|설치가 완료 되었습니다. 컴퓨터를 다시 시작한 후 응용 프로그램을 설치할 수 있습니다.|  
|3015|설치 진행 중입니다. 컴퓨터를 다시 시작은 설치를 계속 해야 합니다.|  
  
### <a name="handling-restarts"></a>다시 시작 처리  
 사용 하 여 셸 설치 관리자를 실행 하는 **/norestart** 컴퓨터를 다시 시작 또는 다시 시작 하려면 컴퓨터에 대 한 요청 하지 않습니다는 지정한 인수를 합니다. 그러나 다시 시작 해야 할 수 있습니다 하 고 컴퓨터를 다시 시작한 후 설치 관리자 계속 되도록 확인 해야 합니다.  
  
 다시 시작을 올바르게 처리 하려면 하나의 설치 프로그램이 다시 시작 설정 및 다시 시작 프로세스를 올바르게 처리 되는 인지를 확인 합니다.  
  
 ERROR_SUCCESS_REBOOT_REQUIRED 또는 3015 반환 되 면 코드는 컴퓨터를 다시 시작 후 설치가 계속 됩니다.  
  
 다시 시작을 처리 하려면 이러한 작업을 수행 합니다.  
  
- Windows 시작 되 면 설치를 계속 하려면 레지스트리를 설정 합니다.  
  
- Double 부트스트래퍼를 다시 시작을 수행 합니다.  
  
- 셸 설치 관리자 ResumeData 키를 삭제 합니다.  
  
- Windows를 다시 시작 합니다.  
  
- MSI의 시작 경로 다시 설정 합니다.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Windows 시작 되 면 설치를 다시 시작 하려면 레지스트리를 설정 합니다.  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ 레지스트리 키를 관리자 권한으로 시스템 시작 시 실행 하 고 지워집니다. HKEY_CURRENT_USER 유사한 키를 포함 하지만 일반 사용자로 실행 되 고 설치는 적합 하지 않습니다. 설치 관리자를 호출 하는 RunOnce 키에는 문자열 값을 배치 하 여 설치를 다시 시작할 수 있습니다. 하지만 사용 하 여 설치 관리자를 호출 하는 권장를 **다시 시작** 또는 시작 하는 대신 다시 시작 하는 응용 프로그램에 알리기 위해 유사한 매개 변수입니다. 또한 여러 번 다시 시작 해야 할 수 있는 설치에서 특히 유용 설치 프로세스에서의 현재 위치를 나타내기 위해 매개 변수를 포함할 수 있습니다.  
  
 다음 예제에서는 설치를 다시 시작 하기 위한 RunOnce 레지스트리 키 값을 보여 줍니다.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Double 부트스트래퍼를 다시 설치  
 설치 RunOnce에서 직접 사용 하는 경우에 데스크톱 완전히 로드 할 수 없습니다. 설치의 또 다른 실행을 만들고 RunOnce 인스턴스를 종료 하면 전체 사용자 인터페이스에서 사용할 수 있도록 해야 합니다.  
  
 올바른 사용 권한을 가져옵니다 하 고 다시 시작 하기 전에 다음 예와 같이 중지 위치 인지 알고 있어야 하는 데 충분 한 정보가 제공 해야 합니다를 다시 설치 프로그램을 실행 해야 합니다.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>셸 설치 관리자 ResumeData 키 삭제  
 셸 설치 관리자를 다시 시작한 후 설치를 다시 시작 하는 데이터를 사용 하 여 HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData 레지스트리 키를 설정 합니다. 응용 프로그램에 셸 설치 관리자 없습니다, 다시 시작 때문에 다음 예와 같이 해당 레지스트리 키를 삭제 합니다.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Windows를 다시 시작  
 필요한 레지스트리 키를 설정 하면 Windows를 다시 시작할 수 있습니다. 다음 예제에서는 다른 Windows 운영 체제에 대 한 다시 시작 명령을 호출합니다.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>MSI의 시작 경로 다시 설정  
 다시 시작 하기 전에 현재 디렉터리의 설치 프로그램 위치 하지만 다시 시작한 후 위치는 system32 디렉터리 됩니다. 설치 프로그램은 다음 예제와 같이 각 MSI 호출 하기 전에 현재 디렉터리를 다시 설정 합니다.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>응용 프로그램 MSI를 실행합니다.  
 Visual Studio Shell installer ERROR_SUCCESS 반환 된 후에 응용 프로그램에 대해 MSI를 실행할 수 있습니다. 설치 프로그램은 사용자 인터페이스를 제공 하므로 자동 모드에서 MSI를 시작 (**/q**) 및 로깅을 사용 하 여 (**/L**) 다음 예제와 같이 합니다.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>참고 항목  
 [연습: 기본 격리 셸 애플리케이션 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
