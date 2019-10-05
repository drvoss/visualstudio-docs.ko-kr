---
title: '연습: 격리 셸 응용 프로그램을 만드는 기본 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e92fa99a266dc1d1b537387f3dae848a6ecb285d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442279"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>연습: 기본 격리 셸 응용 프로그램 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에는 격리 셸 솔루션을 만들고, 도움말 도구 창 사용자 지정 하는 격리 셸을 설치 하는 설치 프로그램을 만드는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다. 격리 셸을 배포 하려면 Visual Studio Shell (격리) 재배포 가능 패키지도 사용 해야 합니다.  
  
## <a name="creating-an-isolated-shell-solution"></a>격리 셸 솔루션을 만들기  
 이 섹션에서는 Visual Studio Shell 격리 프로젝트 템플릿을 사용 하 여 격리 셸 솔루션을 만드는 방법을 보여 줍니다. 솔루션에는 다음 프로젝트가 포함 됩니다.  
  
- 합니다 *SolutionName*합니다. AboutBoxPackage 프로젝트/상자에 대 한 도움말의 모양을 사용자 지정할 수 있습니다.  
  
- 격리 셸 응용 프로그램의 다양 한 구성 요소를 정의 하는 source.extension.vsixmanifest 파일을 포함 하는 ShellExtensionsVSIX 프로젝트입니다.  
  
- 합니다 *SolutionName* 격리 셸 응용 프로그램을 호출 하는 실행 파일을 생성 하는 프로젝트입니다. 이 프로젝트에 격리 셸 응용 프로그램의 동작과 모양 사용자 수를 허용 하는 셸 사용자 지정 폴더를 포함 합니다.  
  
- 합니다 *SolutionName* 프로젝트를 활성 메뉴 명령 및 지역화 가능한 문자열을 정의 하는 위성 어셈블리를 생성 합니다.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>기본 격리 셸 솔루션을 만들려면  
  
1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.  
  
2. 에 **새 프로젝트** 창에서 확장 **기타 프로젝트 형식** 차례로 **확장성**합니다. 선택 된 **Visual Studio Shell 격리** 프로젝트 템플릿.  
  
3. 프로젝트 이름을 `MyVSShellStub` 위치를 지정 합니다. 했는지 **솔루션용 디렉터리 만들기** 체크 인 되 고 클릭 **확인**합니다.  
  
     새 솔루션에 나타납니다 **솔루션 탐색기**합니다.  
  
4. 솔루션을 빌드 및 격리 셸 응용 프로그램 디버깅을 시작 합니다.  
  
     Visual Studio 격리 셸이 나타납니다. 제목 표시줄 읽습니다 **MyVSShellStub**합니다. 제목 표시줄 아이콘 \MyVSShellStub\Resource Files\ApplicationIcon.ico에서 생성 됩니다.  
  
## <a name="customizing-the-application-name-and-icon"></a>응용 프로그램 이름과 아이콘을 사용자 지정  
 제목 표시줄에 회사 이름과 해당 로고를 사용 하 여 응용 프로그램을 브랜드화 하려면이 좋습니다. 다음 단계에는 이름과 MyVSShellStub.Application.pkgdef 패키지 정의 파일을 변경 하 여 사용자 지정 응용 프로그램 제목 표시줄에 표시 되는 아이콘을 변경 하는 방법을 보여 줍니다.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>응용 프로그램 이름과 아이콘을 사용자 지정 하려면  
  
1. \Shell Customization\MyVSShellStub.Application.pkgdef MyVSShellStub 프로젝트를 엽니다.  
  
2. 변경 된 `AppName` 요소 값을 **"AppName" = "Fabrikam 음악 Editor"**  
  
3. 응용 프로그램 아이콘을 변경 하려면 다른 아이콘 \MyVSShellStub\MyVSShellStub\MyVSShellStub\ 디렉터리로 복사 합니다. 기존 ApplicationIcon.ico 파일을 ApplicationIcon1.ico을 바꿉니다. 새 파일을 ApplicationIcon.ico을 바꿉니다.  
  
4. 솔루션을 빌드하고 디버깅을 시작합니다. 격리 셸 IDE에 표시 됩니다. 제목 표시줄에 새 아이콘 옆의 **Fabrikam 음악 편집기**합니다.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>기본 웹 브라우저 홈 페이지 사용자 지정  
 이 섹션의 기본 홈 페이지를 변경 하는 방법을 보여 줍니다 합니다 **웹 브라우저** 패키지 정의 파일을 변경 하 여 창입니다.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>기본 웹 브라우저 홈 페이지를 사용자 지정 하려면  
  
1. MyVSShellStub.Application.pkgdef 파일에서 변경 된 `DefaultHomePage` 요소 값을 "<http://www.microsoft.com>"입니다.  
  
2. MyVSShellStub 프로젝트를 다시 작성 합니다.  
  
3. 솔루션을 빌드하고 디버깅을 시작합니다.  
  
4. **보기 / 기타 Windows**, 클릭 **웹 브라우저**합니다. 합니다 **웹 브라우저** 창에는 Microsoft Corporation 홈 페이지가 표시 됩니다.  
  
## <a name="removing-the-print-command"></a>인쇄 명령 제거  
 격리 셸 UI 프로젝트에서.vsct 파일 형식의 선언 집합을 이루어져 `<Define name=No_` *요소*`>`여기서 *요소* 표준 Visual Studio 메뉴 중 하나인 및 명령입니다.  
  
 선언을 주석 처리 된 경우 해당 메뉴 또는 명령을 격리 셸에서 제외 됩니다. 반대로, 선언은 주석 처리 하는 경우 메뉴 또는 명령을 격리 셸에 포함 됩니다.  
  
 다음 단계에서는.vsct 파일에서 인쇄 명령을 주석입니다.  
  
#### <a name="to-remove-the-print-command"></a>인쇄 명령을 제거 하려면  
  
1. 있는지 확인 합니다 **인쇄** 명령에 표시 되는 **파일** 격리 셸 응용 프로그램에서 메뉴.  
  
2. MyVSShellStubUI 프로젝트에서 편집을 위해 \Resource Files\MyVSShellStubUI.vsct을 엽니다.  
  
3. 이 줄 주석 처리를 제거 합니다.  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. 인쇄 명령을 제거합니다.  
  
5. 격리 셸 응용 프로그램 디버깅을 시작 합니다. 있는지 확인 합니다 **파일 / 인쇄** 명령 사라지게 됩니다.  
  
## <a name="removing-features-from-the-isolated-shell"></a>격리 셸에서 기능 제거  
 이러한 기능은 사용자 지정 격리 셸 응용 프로그램에서 하지 않을 경우.pkgundef 파일을 편집 하 여 Visual Studio를 사용 하 여 로드 되는 패키지 중 일부를 제거할 수 있습니다. $RootKey$ \Packages 레지스트리 키의 하위 키 중 하나에 패키지를 지정 합니다.  
  
> [!NOTE]
> 기능을 찾는 Visual Studio의 Guid를 참조 하세요 [Visual Studio 기능의 패키지 Guid](../extensibility/package-guids-of-visual-studio-features.md)합니다.  
  
 다음 절차는 XML을 제거 하는 방법 격리 셸 편집기를 보여 줍니다.  
  
#### <a name="to-remove-the-xml-editor"></a>XML 편집기를 제거 하려면  
  
1. MyVSShellStub 프로젝트의 셸 사용자 지정 폴더에 MyVSShellStub.pkgundef 파일을 엽니다.  
  
2. 다음 줄을 주석 처리 제거 합니다.  
  
     [$RootKey$\Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. 솔루션 다시 빌드 및 격리 셸 디버깅을 시작 합니다. 예를 들어 \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct XML 파일을 엽니다. 파일에서 XML 키워드 색으로 표시 되지 않습니다 됩니다 확인 하 고 해당 입력 "<" 줄에 않습니다 하지 XML 도구 설명이 표시 합니다.  
  
## <a name="customizing-the-helpabout-box"></a>도움말을 사용자 지정/상자에 대 한  
 도움말을 사용자 지정할 수 있습니다/격리 된 셸 프로젝트 템플릿의 일부로 만들어지는 상자에 대 한 합니다.  
  
#### <a name="to-customize-the-company-name"></a>회사 이름을 사용자 지정 하려면  
  
1. MyVSShellStub.AboutBoxPackage 프로젝트, 회사 이름, 저작권 정보, 제품 버전 및 제품 설명을 \Properties\AssemblyInfo.cs 파일에 있습니다. 이 파일을 엽니다.  
  
2. 변경 된 `AssemblyCompany` 값을 **Fabrikam**, `AssemblyProduct` 및 `AssemblyTitle` 값을 **Fabrikam 음악 편집기**, 및 `AssemblyCopyright` 값을 **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3. 제품에 대 한 설명을 추가, 변경 된 `AssemblyDescription` 값을 **Fabrikam 음악 편집기에 대 한 설명을.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. 디버깅을 시작 하 고 격리 셸 응용 프로그램에서 엽니다는 **도움말] / [정보** 상자입니다. 변경 된 문자열을 표시 됩니다. 도움말/상자에 대 한 제목으로 동일 합니다 `AssemblyTitle` AssemblyInfo.cs에는 값입니다.  
  
5. 속성을 **도움말/정보** 상자 자체 MyVSShellStub.AboutBoxPackage\AboutBox.xaml 파일에 포함 됩니다. 도움말/상자에 대 한 너비를 변경 하려면로 이동 합니다 `AboutDialogStyle` 블록과 설정를 `Width` 200 속성:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6. 솔루션 다시 빌드 및 격리 셸 디버깅을 시작 합니다. 도움말/상자에 대 한는 약 사각형입니다.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>격리 셸 응용 프로그램을 배포 하기 전에  
 Visual Studio Shell (격리) 재배포 가능 패키지가 포함 된 모든 컴퓨터에 격리 셸 응용 프로그램을 설치할 수 있습니다. 재배포 가능 패키지에 대 한 자세한 내용은 참조는 [Visual Studio 확장 다운로드](http://go.microsoft.com/fwlink/?LinkID=119298) 웹 사이트입니다.  
  
## <a name="deploying-the-isolated-shell-application"></a>격리 셸 응용 프로그램 배포  
 설치 프로젝트를 만들어 대상 컴퓨터에 격리 셸 응용 프로그램을 배포 합니다. 이러한 작업을 지정 해야 합니다.  
  
- 대상 컴퓨터에서 파일과 폴더의 레이아웃입니다.  
  
- .NET Framework 및 Visual Studio 셸 런타임 있는지을 보장 하는 시작 조건은 대상 컴퓨터에 설치 됩니다.  
  
  다음 절차에서는 컴퓨터에 InstallShield Limited Edition을 설치 해야 합니다.  
  
#### <a name="to-create-the-setup-project"></a>설치 프로젝트를 만들려면  
  
1. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭 하 고 클릭 **새 프로젝트 추가**합니다.  
  
2. 에 **새 프로젝트** 대화 상자에서 **기타 프로젝트 형식** 선택한 후 **설치 및 배포**합니다. InstallShield 템플릿을 선택 합니다. 새 프로젝트의 이름을 `MySetup` 을 클릭 한 다음 **확인**합니다.  
  
3. InstallShield Limited Edition이 이미 설치 되어 다음 단계로 이동 합니다.  
  
    InstallShield Limited Edition 이미 설치 되어 있지 않으면, InstallShield 다운로드 페이지가 나타납니다. 다운로드 하 고 Visual Studio 버전과 호환 되는 InstallShield의 버전을 선택 하면 제품 설치 지침을 따릅니다. InstallShield 설치를 등록 하거나 평가판으로 사용할 것인지 결정 해야 합니다. 설치를 완료 한 후에 Visual Studio를 다시 시작 해야 합니다.  
  
   > [!IMPORTANT]
   > InstallShield 프로젝트를 만들려면 관리자 권한으로 Visual Studio를 시작 해야 합니다. 이렇게 하지 않는 경우 프로젝트를 빌드할 때 오류가 받습니다.  
  
   다음 단계에는 설치 프로젝트를 구성 하는 방법을 보여 줍니다.  
  
> [!IMPORTANT]
> 설치 프로젝트를 구성 하기 전에 한 번 이상 격리 된 셸 프로젝트의 릴리스 구성은 빌드 되었는지 확인 합니다.  
  
#### <a name="to-configure-the-setup-project"></a>설치 프로젝트를 구성 하려면  
  
1. 에 **솔루션 탐색기**아래에 있는 합니다 **MySetup** 프로젝트 **프로젝트 도우미**. 맨 아래쪽 행에는 **프로젝트 도우미** 창에서 선택 **응용 프로그램 정보**합니다. 입력 **Fabrikam** 회사 이름으로 및 **Fabrikam 음악 편집기** 응용 프로그램 이름으로 합니다. 오른쪽 맨 아래에서 앞으로 화살표를 선택 합니다 **프로젝트 도우미**합니다.  
  
2. 선택 **예** 아래에서 **응용 프로그램 컴퓨터에 설치할 소프트웨어에 필요한?** 선택한 후 **Microsoft.NET Framework 4.5 전체 패키지**합니다.  
  
3. 선택 합니다 **응용 프로그램 파일** 창의 맨 아래에 있는 단추를 확인 합니다 **Fabrikam 음악 편집기** 폴더를 선택 합니다.  
  
4. 선택 된 **파일 추가** 단추입니다. 에 **파일 추가** 대화 상자에서 다음 파일을 추가 합니다 **MyVSShellStub\Release** 폴더:  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll.manifest  
  
    4. MyVSShellStub.pkgdef  
  
    5. MyVSShellStub.pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. Splash.bmp  
  
5. 클릭 합니다 **프로젝트 출력 추가** 추가한 단추 **MyVSShellStub/기본 출력**합니다. **확인**을 클릭합니다.  
  
6. 왼쪽된 창에서 아래 **대상 컴퓨터**를 마우스 오른쪽 단추로 클릭 합니다 **Fabrikam 음악 편집기 [INSTALLDIR]** 노드 추가 **새 폴더** 라는 **확장** .  
  
7. 마우스 오른쪽 단추로 클릭 합니다 **확장** 왼쪽된 창에서 노드 라는 새 폴더를 추가한 **응용 프로그램**합니다.  
  
8. 선택 합니다 **응용 프로그램** 폴더를 클릭 합니다 **프로젝트 출력 추가** 단추를 선택한 다음 MyVSShellStub.AboutBoxPackage 프로젝트에서 기본 출력을 선택 합니다.  
  
9. 클릭 합니다 **파일 추가** 단추 및 \MyVSShellStub\Release\Extensions\Application\ 폴더에서 다음 파일을 추가 합니다.  
  
    - MyVSShellStub.AboutBoxPackage.pkgdef  
  
    - MyVSShellStub.Application.pkgdef  
  
10. 마우스 오른쪽 단추로 클릭 합니다 **Fabrikam 음악 편집기 [INSTALLDIR]** 왼쪽된 창에서 노드 라는 새 폴더를 추가한 **1033**합니다.  
  
11. 1033 폴더를 선택 하 고 클릭 합니다 **프로젝트 출력 추가** 단추를 선택한 MyVSShellStubUI 프로젝트에서 기본 출력 합니다.  
  
12. 으로 이동 합니다 **응용 프로그램 바로 가기를** 창입니다.  
  
13. 클릭 **새로 만들기** 바로 가기를 만들고 선택 **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**합니다.  
  
14. 으로 이동 합니다 **설치 인터뷰** 창입니다.  
  
15. 모든 항목을 설정 **No**합니다.  
  
16. **솔루션 탐색기**, MySetup 프로젝트를 열고 **설치 요구 사항 정의 및 작업 \ 요구 사항**합니다. 합니다 **요구 사항** 창이 열립니다.  
  
17. 마우스 오른쪽 단추로 클릭 **시스템 소프트웨어 요구 사항** 선택한 **시작 새 조건 만들기**합니다. 합니다 **시스템 검색 마법사** 나타납니다.  
  
18. 에 **찾을 하 시겠습니까?** 창 선택 **레지스트리 항목** 드롭 다운 목록에서 클릭 **다음**합니다.  
  
19. 에 **에 대 한 확인 하 시겠습니까?** 창 **HKEY_LOCAL_MACHINE** 레지스트리 루트. 입력 **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 64 비트 시스템용 또는 **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 32 비트 시스템용 를입력합니다. **설치** 레지스트리 값으로. **다음**을 클릭합니다.  
  
20. 에 **값을 사용 하 여 작업을 수행 하 시겠습니까?** 창 입력 **이 제품에는 Visual Studio 2015 격리 셸 재배포 가능 패키지를 설치 해야 합니다.** 표시 텍스트 및 클릭 **완료**합니다.  
  
21. 설치 프로젝트를 만들려면 격리 셸 솔루션을 다시 빌드하십시오.  
  
     다음 폴더에서 setup.exe 파일을 찾을 수 있습니다.  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>설치 프로그램을 테스트  
 설치를 테스트 하려면 setup.exe 파일을 다른 컴퓨터로 복사 하 고 설치 프로그램 실행 파일을 실행 합니다. 격리 셸 응용 프로그램을 실행할 수 있어야 합니다.
