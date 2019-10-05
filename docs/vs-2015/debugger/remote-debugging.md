---
title: 원격 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e31d177a8bda5435c2201701241638cb919cf9ec
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687544"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다른 컴퓨터에 배포된 Visual Studio 애플리케이션을 디버그할 수 있습니다.  이렇게 하려면 Visual Studio 원격 디버거를 사용합니다.  
  
 여기에 제공된 정보는 Windows 데스크톱 애플리케이션 및 ASP.NET 애플리케이션에 적용됩니다.  원격 디버깅 Windows 스토어 앱 및 Azure 앱에 대 한 정보를 참조 하세요 [Windows 스토어 및 Azure 앱에서 원격 디버깅](#bkmk_winstoreAzure)합니다.  
  
## <a name="get-the-remote-tools"></a>원격 도구 받기  
다운로드 하거나 디버그 하려는 서버나 장치에서 직접 원격 도구 설치 된 Visual Studio를 사용 하 여 호스트 컴퓨터에서 원격 도구에 가져올 수 있습니다 하거나 할 수 있습니다.

### <a name="to-download-and-install-the-remote-tools"></a>원격 도구 다운로드 및 설치 하려면
  
1. 장치 또는 서버를 디버그하려는 컴퓨터(대신 Visual Studio를 실행하는 컴퓨터)에 맞는 버전의 원격 도구를 가져옵니다.

    |버전|링크|노트|
    |-|-|-|
    |Visual Studio 2015 업데이트 3|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|메시지가 표시 되 면 무료 Visual Studio Dev Essentials 그룹에 가입 또는 유효한 Visual Studio 구독을 사용 하 여 로그인만 서명할 수 있습니다. 그런 다음 다시 링크를 열 필요한 경우. 항상 일치 (x 86, x64 또는 ARM 버전)에 장치 운영 체제 버전을 다운로드|
    |Visual Studio 2015 (이전)|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|메시지가 표시 되 면 무료 Visual Studio Dev Essentials 그룹에 가입 또는 유효한 Visual Studio 구독을 사용 하 여 로그인만 서명할 수 있습니다. 그런 다음 다시 링크를 열 필요한 경우.|
    |Visual Studio 2013|[원격 도구](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 설명서에서 페이지를 다운로드 합니다.|
    |Visual Studio 2012|[원격 도구](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 설명서에서 페이지를 다운로드 합니다.|
  
2. 다운로드 페이지에서 (86, x64 또는 ARM 버전) x 운영 체제와 일치 하는 도구 버전을 선택 하 고 원격 도구를 다운로드 합니다.
  
    > [!IMPORTANT]
    > Visual Studio의 버전과 일치 하는 원격 도구의 최신 버전을 설치 하는 것이 좋습니다. 일치 하지 않는 버전 권장 되지 않습니다.  
    >   
    >  또한 설치 하려는 운영 체제와 동일한 아키텍처를 가진 원격 도구를 설치 해야 합니다. 즉, 64 비트 운영 체제를 실행 하는 원격 컴퓨터에서 32 비트 응용 프로그램을 디버그 하려는 원격 컴퓨터의 64 비트 버전의 원격 도구를 설치 해야 합니다.  
  
3. 실행 파일을 다운로드했으면 지침에 따라 원격 컴퓨터에 애플리케이션을 설치합니다. 참조 [설치 지침](#bkmk_setup)

원격 컴퓨터에 원격 디버거 (msvsmon.exe)를 복사 하 고 실행 하려는 경우는 **원격 디버거 구성 마법사** (**rdbgwiz.exe**) 다운로드 하는 경우에 설치 되는 도구 및 있습니다 해야 마법사를 사용 하 여 나중에 구성에 대 한 원격 디버거를 서비스로 실행 하려는 경우에 특히 합니다. 자세한 내용은 [(선택 사항) 원격 디버거를 서비스로 구성](#bkmk_configureService) 아래.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>파일 공유에서 원격 디버거를 실행 하려면

원격 디버거를 찾을 수 있습니다 (**msvsmon.exe**) Visual Studio 2015 Community, Professional 또는 Enterprise를 이미 설치 된 컴퓨터에 있습니다. 대부분의 시나리오에 대 한 원격 디버깅을 설정 하는 가장 쉬운 방법은 파일 공유에서 원격 디버거 (msvsmon.exe)를 실행 하는 것입니다. 사용 제한 사항에 대 한 원격 디버거의 도움말 페이지를 참조 하세요. (**도움말 / 사용법** 원격 디버거의).

1. 찾을 **msvsmon.exe** Visual Studio 버전과 일치 하는 디렉터리에 있습니다. For Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. 공유 합니다 **원격 디버거** Visual Studio 컴퓨터의 폴더입니다.

3. 원격 컴퓨터에서 실행 **msvsmon.exe**합니다. 수행 합니다 [설치 지침](#bkmk_setup)합니다.

> [!TIP] 
> 명령줄 설치와 명령줄 참조에 대 한 도움말 페이지를 참조 하세요 **msvsmon.exe** 입력 하 여 ``msvsmon.exe /?`` Visual Studio가 설치 된 컴퓨터의 명령줄에서 (또는 이동 **도움말 / 사용량**원격 디버거의).

## <a name="supported-operating-systems"></a>Supported Operating Systems  
 원격 컴퓨터에서 다음 운영 체제 중 하나를 실행해야 합니다.  
  
- Windows 10  
  
- Windows 8 또는 8.1  
  
- Windows 7 서비스 팩 1  
  
- Windows Server 2012 또는 Windows Server 2012 R2  
  
- Windows Server 2008 서비스 팩 2, Windows Server 2008 R2 서비스 팩 1  
  
## <a name="supported-hardware-configurations"></a>지원되는 하드웨어 구성  
  
- 1.6GHz 이상의 프로세서  
  
- 1GB RAM(가상 머신에서 실행하는 경우 1.5GB)  
  
- 1GB의 하드 디스크 여유 공간  
  
- 5400RPM 하드 드라이브  
  
- 1024x768 이상 디스플레이 해상도로 실행되는 DirectX 9 지원 비디오 카드  
  
## <a name="network-configuration"></a>네트워크 구성  
 원격 컴퓨터와 Visual Studio 컴퓨터는 네트워크, 작업 그룹 또는 홈 그룹을 통해 연결되거나 이더넷 케이블을 통해 직접 연결되어야 합니다. 인터넷을 통한 디버깅은 지원되지 않습니다.  
  
## <a name="bkmk_setup"></a>원격 디버거 설정  
 원격 컴퓨터에서 관리자 권한이 있어야 합니다.  
  
1. 원격 디버거 애플리케이션을 찾습니다. (시작 메뉴를 열고 검색할 **원격 디버거**.)
  
    원격 서버에서 원격 디버거를 실행 하는 경우 원격 디버거 응용 프로그램을 마우스 오른쪽 단추로 클릭 하 고 선택할 수 있습니다 **관리자 권한으로 실행** (또는 원격 디버거를 서비스로 실행할 수 있습니다). 원격 서버에서 실행 하지 않는 경우만 해당 정상적으로 시작 합니다.
  
2. 처음으로 (또는 구성 하기 전에) 원격 도구를 시작 하면, **원격 디버깅 구성** 대화 상자가 나타납니다.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Windows 서비스 API (발생 하는 Windows Server 2008 R2에만) 설치 하지 않은 경우 선택 합니다 **설치** 단추입니다.  
  
4. 원격 도구를 사용하려는 네트워크 종류를 선택합니다. 하나 이상의 네트워크 형식을 선택해야 합니다. 컴퓨터가 도메인을 통해 연결된 경우 첫 번째 항목을 선택해야 합니다. 컴퓨터가 작업 그룹 또는 홈 그룹을 통해 연결된 경우 두 번째 또는 세 번째 항목을 적절하게 선택해야 합니다.  
  
5. 선택할 **원격 디버깅 구성** 방화벽을 구성 하 고 도구를 시작 합니다.  
  
6. 구성이 완료되면 원격 디버거 창이 나타납니다.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    원격 디버거 연결 대기 중 이제입니다. 서버 이름을 기록해 및 포트는 나중에 필요 하므로이 Visual Studio에서 구성에 대해 표시 되는 번호입니다.  
  
   디버깅 및 원격 디버거를 중지 해야 할 경우 완료 되 면 클릭 **파일 / 끝내기** 창에서. 다시 시작할 수 있습니다 합니다 **시작** 메뉴 또는 명령줄에서:  
  
   **\<Visual Studio 설치 디렉터리 > 디버거 \Common7\IDE\Remote\\< x86, x64 또는 Appx\msvsmon.exe**합니다.  
  
## <a name="configure-the-remote-debugger"></a>원격 디버거 구성  
 원격 디버거를 처음으로 시작한 후에 원격 디버거 구성의 일부 측면을 변경할 수 있습니다.
  
- 다른 사용자가 원격 디버거에 연결할 수 있도록을 선택할 **도구 / 사용 권한**합니다. 사용 권한을 부여하거나 거부하려면 관리자 권한이 있어야 합니다.

  > [!IMPORTANT]
  > Visual Studio 컴퓨터에서 사용 하는 사용자 계정에서 다른 사용자 계정으로 원격 디버거를 실행할 수는 있지만 원격 디버거의 사용 권한에 다른 사용자 계정을 추가 해야 합니다. 

   또는 사용 하 여 명령줄에서 원격 디버거를 시작할 수 있습니다 합니다 **허용 / \<사용자 이름 >** 매개 변수: **msvsmon /allow \< username@computer>** 합니다.
  
- 인증 모드 또는 포트 번호를 변경 하거나 원격 도구의 시간 제한 값을 지정 하려면: 선택할 **도구 / 옵션**합니다.  
  
   기본적으로 사용 되는 포트 번호의 나열을 참조 하세요 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)합니다.  
  
   > [!WARNING]
  > 원격 도구를 인증 안 함 모드에서 실행할 수도 있지만 이 모드는 사용하지 않는 것이 좋습니다. 이 모드에서 실행할 때는 네트워크 보안이 없습니다. 네트워크에 악의적인 트래픽이나 유해 트래픽 위험이 확실히 없는 경우에만 인증 안 함 모드를 선택하세요.

## <a name="bkmk_configureService"></a> (선택 사항) 원격 디버거를 서비스로 구성
 ASP.NET 및 기타 서버 환경에서 디버깅을 위해 관리자 권한으로 원격 디버거를 실행 하거나, 항상 실행 하려는 경우 원격 디버거를 서비스로 실행 됩니다.
  
 원격 디버거를 서비스로 구성 하려는 경우 다음이 단계를 수행 합니다.  
  
1. **원격 디버거 구성 마법사** (rdbgwiz.exe)를 찾습니다. 이는 원격 디버거와 별도의 응용 프로그램입니다. 원격 도구를 설치한 경우에만 사용할 수 있습니다. Visual Studio와 함께 설치되지 않습니다.  
  
2. 구성 마법사 실행을 시작합니다. 첫 페이지가 표시되면 **다음**을 클릭합니다.  
  
3. **Visual Studio 2015 원격 디버거를 서비스로 실행** 확인란을 선택합니다.  
  
4. 사용자 계정 및 암호의 이름을 추가합니다.  
  
    이 계정에 **서비스로 로그온** 사용자 권한을 추가해야 할 수도 있습니다. **시작** 페이지 또는 창에서 **로컬 보안 정책** (secpol.msc)을 찾습니다(또는 명령 프롬프트에서 **secpol** 입력). 창이 나타나면 **사용자 권한 할당**을 두 번 클릭한 다음 오른쪽 창에서 **서비스로 로그온** 을 찾습니다. 폴더를 두 번 클릭합니다. 사용자 계정을 추가 합니다 **속성** 창과 클릭 **확인**.) **다음**을 클릭합니다.  
  
5. 원격 도구가 통신하는 데 사용할 네트워크 유형을 선택합니다. 하나 이상의 네트워크 형식을 선택해야 합니다. 컴퓨터가 도메인을 통해 연결된 경우 첫 번째 항목을 선택해야 합니다. 컴퓨터가 작업 그룹 또는 홈 그룹을 통해 연결된 경우 두 번째 또는 세 번째 항목을 선택해야 합니다. **다음**을 클릭합니다.  
  
6. 서비스를 시작할 수 있는 경우 **Visual Studio 원격 디버거 구성 마법사를 성공적으로 완료했습니다.** 가 표시됩니다. 서비스를 시작할 수 없는 경우 **Visual Studio 원격 디버거 구성 마법사 완료 실패**가 표시됩니다. 이 페이지에서는 서비스를 시작하기 위해 수행할 몇 가지 팁도 제공합니다.  
  
7. **마침**을 클릭합니다.  
  
   이제 원격 디버거가 서비스로 실행됩니다. **제어판 / 서비스** 로 이동한 다음 **Visual Studio 2015 원격 디버거**를 찾아 이를 확인할 수 있습니다.  
  
   **제어판 / 서비스**에서 원격 디버거 서비스를 중지 및 시작할 수 있습니다.  

## <a name="remote-debug-an-aspnet-application"></a>ASP.NET 애플리케이션 원격 디버그  
 IIS를 실행하는 원격 컴퓨터에 ASP.NET 애플리케이션을 배포하는 경우 운영 체제 및 IIS 버전에 따라 다른 단계가 있습니다. IIS 7.5 또는 하세요 이상이 설치 되어 있는 Windows Server 2008 또는 Windows Server 2012를 실행 중인 원격 컴퓨터에 대 한 [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)합니다.
 
 ASP.NET Core 앱을 디버깅 하는 경우를 참조 하세요 [IIS에 게시](https://docs.asp.net/en/latest/publishing/iis.html)합니다. 다른 단계는 IIS에서 ASP.NET Core를 게시 해야 합니다. ASP.NET Core 응용 프로그램을 성공적으로 게시할 수 있습니다 원격 디버깅 [마찬가지로 다른 ASP.NET 앱](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)를 연결 해야 하는 프로세스는 w3wp.exe 대신 dnx.exe, 합니다.

## <a name="remote-debug-a-visual-c-project"></a>Visual C++ 프로젝트 원격 디버그  
 다음 절차에서는 이름 및 프로젝트의 경로 C:\remotetemp\MyMfc이 고 원격 컴퓨터의 이름이 **MJO DL**합니다.  
  
1. **mymfc**라는 MFC 애플리케이션을 만듭니다.  
  
2. `CMainFrame::OnCreate`의 시작 부분에서 쉽게 도달할 수 있는 애플리케이션의 임의 위치(예: **MainFrm.cpp**)에 중단점을 설정합니다.  
  
3. 솔루션 탐색기에서 마우스 오른쪽 단추로 클릭 프로젝트를 마우스 **속성**합니다. **디버깅** 탭을 엽니다.  
  
4. **실행할 디버거**를 **원격 Windows 디버거**로 설정합니다.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. 다음과 같이 속성을 변경합니다.  
  
   |설정|값|
   |-|-|  
   |원격 명령|C:\remotetemp\mymfc.exe|  
   |작업 디렉터리|C:\remotetemp|  
   |원격 서버 이름|MJO-DL:*portnumber*|  
   |연결|Windows 인증을 사용한 원격|  
   |디버거 형식|네이티브 전용|  
   |배포 디렉터리|C:\remotetemp.|  
   |배포할 추가 파일|C:\data\mymfcdata.txt.|  
  
    추가 파일 (선택 사항)을 배포 하는 경우 두 컴퓨터 모두에서 폴더가 있어야 합니다.  
  
6. 솔루션 탐색기에서 솔루션을 마우스 오른쪽 단추로 클릭 하 고 선택 **Configuration Manager**합니다.  
  
7. **디버그** 구성의 경우 **배포** 확인란을 선택합니다.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. 디버깅을 시작 (**디버그 / 디버깅 시작**, 또는 **F5**).  
  
9. 실행 파일이 원격 컴퓨터에 자동으로 배포됩니다.  
  
10. 메시지가 표시 되 면 원격 컴퓨터에 연결할 네트워크 자격 증명을 입력 합니다.  
  
     필요한 자격 증명은 네트워크의 보안 구성에 적용 됩니다. 예를 들어, 도메인 컴퓨터에서 보안 인증서를 선택 하면 또는 도메인 이름 및 암호를 입력 합니다. 도메인이 아닌 컴퓨터에서 입력할 수 있습니다 컴퓨터 이름 및 유효한 사용자 계정 이름 같은 <strong>MJO-DL\name@something.com</strong>, 올바른 암호와 함께 합니다.  
  
11. Visual Studio 컴퓨터에서 실행이 중단점에서 중지된 것이 표시됩니다.  
  
    > [!TIP]
    > 또는 별도의 단계로 파일을 배포할 수 있습니다. **솔루션 탐색기**에서 **mymfc** 노드를 마우스 오른쪽 단추로 클릭하고 **배포**를 선택합니다.  
  
    애플리케이션에서 사용해야 하는 비코드 파일이 있는 경우 Visual Studio 프로젝트에 포함해야 합니다. 추가 파일을 프로젝트 폴더를 만듭니다 (에 **솔루션 탐색기**, 클릭 **추가 / 새 폴더**.) 다음 폴더에 파일을 추가 (에 **솔루션 탐색기**, 클릭 **추가 하거나 기존 항목**, 파일을 선택 합니다.). 각 파일에 대한 **속성** 페이지에서 **출력 디렉터리에 복사**를 **항상 복사**로 설정합니다.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Visual C# 또는 Visual Basic 프로젝트 원격 디버그  
 디버거는 원격 컴퓨터에 Visual C# 또는 Visual Basic 데스크톱 애플리케이션을 배포할 수 없지만 다음과 같이 원격으로 계속 디버그할 수 있습니다. 다음 절차 라는 컴퓨터에서 디버깅 하 려 한다고 가정 **MJO DL**이전 그림에 나와 있는 것 처럼 합니다.
  
1. **MyWpf**라는 WPF 프로젝트를 만듭니다.  
  
2. 쉽게 도달할 수 있는 코드의 임의 위치에 중단점을 설정합니다.  
  
    예를 들어 단추 처리기에 중단점을 설정할 수 있습니다. 이렇게 하려면 MainWindow.xaml을 엽니다 도구 상자에서 단추 컨트롤을 추가 하 고 해당 처리기를 열려면 단추를 두 번 클릭 합니다.
  
3. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**합니다.  
  
4. **속성** 페이지에서 **디버그** 탭을 선택합니다.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. **작업 디렉터리** 텍스트 상자가 비어 있는지 확인합니다.  
  
6. 선택 **사용 하 여 원격 컴퓨터**, 유형과 **MJO-DL:4020** 텍스트 상자에 있습니다. (4020는 원격 디버거 창에 표시 된 포트 번호)입니다.  
  
7. **네이티브 코드 디버깅 사용**이 선택되지 않았는지 확인합니다.  
  
8. 프로젝트를 빌드합니다.  
  
9. Visual Studio 컴퓨터의 **Debug** 폴더와 동일한 경로인 폴더를 원격 컴퓨터에 만듭니다( **\<source path>\MyWPF\MyWPF\bin\Debug**).  
  
10. Visual Studio 컴퓨터에서 방금 빌드한 실행 파일을 원격 컴퓨터에서 새로 만든 폴더에 복사합니다.
  
    > [!CAUTION]
    > 코드를 다시 작성을 변경 하지 마세요 (또는이 단계를 반복 해야 합니다). 원격 컴퓨터에 복사한 실행 파일은 로컬 소스 및 기호와 정확히 일치해야 합니다.

    프로젝트를 수동으로 복사, Xcopy, Robocopy, Powershell 또는 다른 옵션을 사용할 수 있습니다.
  
11. 원격 디버거가 대상 컴퓨터에서 실행 되 고 있는지 확인 합니다. (없는 경우 검색할 **원격 디버거** 에 **시작** 메뉴. ) 원격 디버거 창에는 다음과 같습니다.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Visual Studio에서 디버깅을 시작 (**디버그 / 디버깅 시작**, 또는 **F5**).  
  
13. 메시지가 표시 되 면 원격 컴퓨터에 연결할 네트워크 자격 증명을 입력 합니다.  
  
     필요한 자격 증명은 네트워크의 보안 구성에 따라 달라 집니다. 예를 들어, 도메인 컴퓨터에서 도메인 이름 및 암호를 입력할 수 있습니다. 도메인이 아닌 컴퓨터에서 입력할 수 있습니다 컴퓨터 이름 및 유효한 사용자 계정 이름 같은 <strong>MJO-DL\name@something.com</strong>, 올바른 암호와 함께 합니다.

     WPF 애플리케이션의 주 창이 원격 컴퓨터에서 열려 있다고 표시됩니다.
  
14. 필요한 경우 중단점을 적중 하려면 작업을 수행 합니다. 중단점이 활성화된 것으로 표시되어야 합니다. 활성화되지 않은 경우 애플리케이션에 대한 기호가 로드되지 않은 것입니다. 다시 시도 및에서 문제를 해결 하는 방법 및 기호를 로드 하는 방법에 대 한 정보를 제공 하는 작동 하지 않으면 [기호 파일 이해 및 Visual Studio의 기호 설정](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx)합니다.
  
15. Visual Studio 컴퓨터에서 실행이 중단점에서 중지된 것이 표시됩니다.
  
    애플리케이션에서 사용해야 하는 비코드 파일이 있는 경우 Visual Studio 프로젝트에 포함해야 합니다. 추가 파일을 프로젝트 폴더를 만듭니다 (에 **솔루션 탐색기**, 클릭 **추가 / 새 폴더**.) 다음 폴더에 파일을 추가 (에 **솔루션 탐색기**, 클릭 **추가 하거나 기존 항목**, 파일을 선택 합니다.). 각 파일에 대한 **속성** 페이지에서 **출력 디렉터리에 복사**를 **항상 복사**로 설정합니다.
  
## <a name="set-up-debugging-with-remote-symbols"></a>원격 기호를 사용한 디버깅 설정  
 Visual Studio 컴퓨터에서 생성하는 기호를 사용하여 코드를 디버그할 수 있습니다. 로컬 기호를 사용하는 경우 원격 디버거의 성능이 훨씬 더 빠릅니다.  원격 기호를 사용해야 경우 원격 컴퓨터에서 기호를 찾도록 원격 디버깅 모니터에 지시해야 합니다.  
  
 Visual Studio 2013 Update 2부터 다음 msvsmon 명령줄 스위치를 통해 관리 코드에 원격 기호를 사용할 수 있습니다. `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 자세한 내용은 원격 디버깅 도움말을 참조 하십시오 (키를 누릅니다 **F1** 원격 디버거 창이 나 클릭 **도움말 / 사용법**). [Visual Studio 2012 및 2013의 .NET 원격 기호 로드 변경 내용](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)에서 자세한 내용을 확인할 수 있습니다.  
  
## <a name="bkmk_winstoreAzure"></a> Windows 스토어 및 Azure 앱에서 원격 디버깅  
 Windows 스토어 앱을 사용 하 여 원격 디버깅에 대 한 자세한 내용은 [Visual Studio에서 원격 장치의 Windows 스토어 앱 디버깅 및 테스트](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx)합니다.  
  
 Azure의 디버깅에 대한 자세한 내용은 다음 항목 중 하나를 참조하세요.  
  
- [클라우드 서비스 또는 가상 컴퓨터에서 Visual Studio 디버깅](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Visual Studio에서.NET 백 엔드 디버깅](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
- Azure 웹 사이트의 원격 디버깅 소개 ([1 부](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/)를 [2 부](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/)하십시오 [3 부](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)   
 [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [원격 IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)
