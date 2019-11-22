---
title: Remote Debugging | Microsoft Docs
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
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300551"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다른 컴퓨터에 배포된 Visual Studio 애플리케이션을 디버그할 수 있습니다.  이렇게 하려면 Visual Studio 원격 디버거를 사용합니다.  
  
 여기에 제공된 정보는 Windows 데스크톱 애플리케이션 및 ASP.NET 애플리케이션에 적용됩니다.  For information about remote debugging Windows Store apps and Azure apps, see [Remote Debugging on Windows Store and Azure apps](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Get the remote tools  
You can either download the remote tools directly on the device or server that you want to debug, or you can get the remote tools from your host machine with Visual Studio installed.

### <a name="to-download-and-install-the-remote-tools"></a>To download and install the remote tools
  
1. On the device or server machine that you want to debug (rather than the machine running Visual Studio), get the correct version of the remote tools.

    |Version|링크|노트|
    |-|-|-|
    |Visual Studio 2015 업데이트 3|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary. Always download the version matching your device operating system (x86, x64, or  ARM version)|
    |Visual Studio 2015 (older)|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary.|
    |Visual Studio 2013|[원격 도구](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2013 documentation|
    |Visual Studio 2012|[원격 도구](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2012 documentation|
  
2. On the download page, choose the version of the tools that matches your operating system (x86, x64, or  ARM version) and download the remote tools.
  
    > [!IMPORTANT]
    > We recommend you install the most recent version of the remote tools that matches your version of Visual Studio. Mismatched versions are not recommended.  
    >   
    >  In addition, you must install the remote tools that have the same architecture as the operating system on which you want to install it. In other words, if you want to debug a 32-bit application on a remote computer running a 64-bit operating system, you must install the 64-bit version of the remote tools on the remote computer.  
  
3. 실행 파일을 다운로드했으면 지침에 따라 원격 컴퓨터에 애플리케이션을 설치합니다. See [setup instructions](#bkmk_setup)

If you try to copy the remote debugger (msvsmon.exe) to the remote computer and run it, be aware that the **Remote Debugger Configuration Wizard** (**rdbgwiz.exe**) is installed only when you download the tools, and you may need to use the wizard for configuration later, especially if you want the remote debugger to run as a service. For more information, see [(Optional) Configure the remote debugger as a service](#bkmk_configureService) below.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>To run the remote debugger from a file share

You can find the remote debugger (**msvsmon.exe**) on a computer with Visual Studio 2015 Community, Professional, or Enterprise already installed. For many scenarios, the easiest way to set up remote debugging is to run the remote debugger (msvsmon.exe) from a file share. For usage limitations, see the remote debugger's Help page (**Help / Usage** in the remote debugger).

1. Find **msvsmon.exe** in the directory matching your version of Visual Studio. For Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Share the **Remote Debugger** folder on the Visual Studio computer.

3. On the remote computer, run **msvsmon.exe**. Follow the [setup instructions](#bkmk_setup).

> [!TIP] 
> For command line installation and command line reference, see the Help page for **msvsmon.exe** by typing ``msvsmon.exe /?`` in the command line on the computer with Visual Studio installed (or go to **Help / Usage** in the remote debugger).

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
  
- 1GB의 사용 가능한 하드 디스크 공간  
  
- 5400RPM 하드 드라이브  
  
- 1024x768 이상 디스플레이 해상도로 실행되는 DirectX 9 지원 비디오 카드  
  
## <a name="network-configuration"></a>네트워크 구성  
 원격 컴퓨터와 Visual Studio 컴퓨터는 네트워크, 작업 그룹 또는 홈 그룹을 통해 연결되거나 이더넷 케이블을 통해 직접 연결되어야 합니다. 인터넷을 통한 디버깅은 지원되지 않습니다.  
  
## <a name="bkmk_setup"></a>Set up the remote debugger  
 원격 컴퓨터에서 관리자 권한이 있어야 합니다.  
  
1. 원격 디버거 애플리케이션을 찾습니다. (Open the Start menu and search for **Remote Debugger**.)
  
    If you are running the remote debugger on a  remote server, you can right-click the Remote Debugger app and choose **Run as administrator** (Or, you can run the remote debugger as a service).If you are not running it on a remote server, just start it normally.
  
2. When you start the remote tools for the first time (or before you have configured it), the **Remote Debugging Configuration** dalog box appears.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. If the Windows Service API is not installed (which happens only on Windows Server 2008 R2), choose the **Install** button.  
  
4. 원격 도구를 사용하려는 네트워크 종류를 선택합니다. 하나 이상의 네트워크 형식을 선택해야 합니다. 컴퓨터가 도메인을 통해 연결된 경우 첫 번째 항목을 선택해야 합니다. 컴퓨터가 작업 그룹 또는 홈 그룹을 통해 연결된 경우 두 번째 또는 세 번째 항목을 적절하게 선택해야 합니다.  
  
5. Choose **Configure remote debugging** to configure the firewall and start the tool.  
  
6. 구성이 완료되면 원격 디버거 창이 나타납니다.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    The remote debugger is now waiting for a connection. Make a note of the server name and port number that is displayed, because you will need this later for configuration in Visual Studio.  
  
   When you are finished debugging and need to stop the remote debugger, click **File / Exit** on the window. You can restart it from the **Start** menu or from the command line:  
  
   **\<Visual Studio installation directory>\Common7\IDE\Remote Debugger\\<x86, x64, or Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>원격 디버거 구성  
 원격 디버거를 처음으로 시작한 후에 원격 디버거 구성의 일부 측면을 변경할 수 있습니다.
  
- To enable other users to connect to the remote debugger, choose **Tools / Permissions**. 사용 권한을 부여하거나 거부하려면 관리자 권한이 있어야 합니다.

  > [!IMPORTANT]
  > You can run the remote debugger under a user account that differs from the user account you are using on the Visual Studio computer, but you must add the different user account to the remote debugger's permissions. 

   Alternatively, you can start the remote debugger from the command line with the **/allow \<username>** parameter: **msvsmon /allow \<username@computer** .
  
- To change the Authentication mode or the port number, or to specify a timeout value for the remote tools: choose **Tools / Options**.  
  
   For a listing of the port numbers used by default, see [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > 원격 도구를 인증 안 함 모드에서 실행할 수도 있지만 이 모드는 사용하지 않는 것이 좋습니다. 이 모드에서 실행할 때는 네트워크 보안이 없습니다. 네트워크에 악의적인 트래픽이나 유해 트래픽 위험이 확실히 없는 경우에만 인증 안 함 모드를 선택하세요.

## <a name="bkmk_configureService"></a> (Optional) Configure the remote debugger as a service
 For debugging in ASP.NET and other server environments, you must either run the remote debugger as an Administrator or, if you want it always running,  run the remote debugger as a service.
  
 If you want to configure the remote debugger as a service, follow these steps.  
  
1. **원격 디버거 구성 마법사** (rdbgwiz.exe)를 찾습니다. (This is a separate application from the Remote Debugger.) It is available only when you install the remote tools. Visual Studio와 함께 설치되지 않습니다.  
  
2. 구성 마법사 실행을 시작합니다. 첫 페이지가 표시되면 **다음**을 클릭합니다.  
  
3. **Visual Studio 2015 원격 디버거를 서비스로 실행** 확인란을 선택합니다.  
  
4. 사용자 계정 및 암호의 이름을 추가합니다.  
  
    이 계정에 **서비스로 로그온** 사용자 권한을 추가해야 할 수도 있습니다. **시작** 페이지 또는 창에서 **로컬 보안 정책** (secpol.msc)을 찾습니다(또는 명령 프롬프트에서 **secpol** 입력). 창이 나타나면 **사용자 권한 할당**을 두 번 클릭한 다음 오른쪽 창에서 **서비스로 로그온** 을 찾습니다. 폴더를 두 번 클릭합니다. Add the user account to the **Properties** window and click **OK**.) Click **Next**.  
  
5. 원격 도구가 통신하는 데 사용할 네트워크 유형을 선택합니다. 하나 이상의 네트워크 형식을 선택해야 합니다. 컴퓨터가 도메인을 통해 연결된 경우 첫 번째 항목을 선택해야 합니다. 컴퓨터가 작업 그룹 또는 홈 그룹을 통해 연결된 경우 두 번째 또는 세 번째 항목을 선택해야 합니다. **다음**을 클릭합니다.  
  
6. 서비스를 시작할 수 있는 경우 **Visual Studio 원격 디버거 구성 마법사를 성공적으로 완료했습니다.** 가 표시됩니다. 서비스를 시작할 수 없는 경우 **Visual Studio 원격 디버거 구성 마법사 완료 실패**가 표시됩니다. 이 페이지에서는 서비스를 시작하기 위해 수행할 몇 가지 팁도 제공합니다.  
  
7. **마침**을 클릭합니다.  
  
   이제 원격 디버거가 서비스로 실행됩니다. **제어판 / 서비스** 로 이동한 다음 **Visual Studio 2015 원격 디버거**를 찾아 이를 확인할 수 있습니다.  
  
   **제어판 / 서비스**에서 원격 디버거 서비스를 중지 및 시작할 수 있습니다.  

## <a name="remote-debug-an-aspnet-application"></a>ASP.NET 애플리케이션 원격 디버그  
 IIS를 실행하는 원격 컴퓨터에 ASP.NET 애플리케이션을 배포하는 경우 운영 체제 및 IIS 버전에 따라 다른 단계가 있습니다. For remote computers running Windows Server 2008 or Windows Server 2012 that have IIS 7.5 or later installed, please see [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 If you are debugging an ASP.NET Core app, please see [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html). Different steps are required to publish an ASP.NET Core on IIS. Once you publish an ASP.NET Core app successfully, you can remote debug it [just like other ASP.NET apps](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), except that the process you need to attach to is dnx.exe instead of w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Visual C++ 프로젝트 원격 디버그  
 In the following procedure, the name and path of the project is C:\remotetemp\MyMfc, and the name of the remote computer is **MJO-DL**.  
  
1. **mymfc**라는 MFC 애플리케이션을 만듭니다.  
  
2. `CMainFrame::OnCreate`의 시작 부분에서 쉽게 도달할 수 있는 애플리케이션의 임의 위치(예: **MainFrm.cpp**)에 중단점을 설정합니다.  
  
3. In Solution Explorer, right-click on the project and select **Properties**. **디버깅** 탭을 엽니다.  
  
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
  
    If you deploy additional files (optional), the folder must exist on both machines.  
  
6. In Solution Explorer, right-click the solution and choose **Configuration Manager**.  
  
7. **디버그** 구성의 경우 **배포** 확인란을 선택합니다.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Start debugging (**Debug / Start Debugging**, or **F5**).  
  
9. 실행 파일이 원격 컴퓨터에 자동으로 배포됩니다.  
  
10. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials are specific to your network's security configuration. For example, on a domain computer, you might choose a security certificate or enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.  
  
11. Visual Studio 컴퓨터에서 실행이 중단점에서 중지된 것이 표시됩니다.  
  
    > [!TIP]
    > 또는 별도의 단계로 파일을 배포할 수 있습니다. **솔루션 탐색기**에서 **mymfc** 노드를 마우스 오른쪽 단추로 클릭하고 **배포**를 선택합니다.  
  
    애플리케이션에서 사용해야 하는 비코드 파일이 있는 경우 Visual Studio 프로젝트에 포함해야 합니다. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). 각 파일에 대한 **속성** 페이지에서 **출력 디렉터리에 복사**를 **항상 복사**로 설정합니다.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Visual C# 또는 Visual Basic 프로젝트 원격 디버그  
 디버거는 원격 컴퓨터에 Visual C# 또는 Visual Basic 데스크톱 애플리케이션을 배포할 수 없지만 다음과 같이 원격으로 계속 디버그할 수 있습니다. The following procedure assumes that you want to debug it on a computer named **MJO-DL**, as shown in the earlier illustration.
  
1. **MyWpf**라는 WPF 프로젝트를 만듭니다.  
  
2. 쉽게 도달할 수 있는 코드의 임의 위치에 중단점을 설정합니다.  
  
    예를 들어 단추 처리기에 중단점을 설정할 수 있습니다. To do this, open MainWindow.xaml, and add a Button control from the Toolbox, then double-click the button to open it's handler.
  
3. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
4. **속성** 페이지에서 **디버그** 탭을 선택합니다.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. **작업 디렉터리** 텍스트 상자가 비어 있는지 확인합니다.  
  
6. Choose **Use remote machine**, and type **MJO-DL:4020** in the text box. (4020 is the port number shown in the remote debugger window).  
  
7. **네이티브 코드 디버깅 사용**이 선택되지 않았는지 확인합니다.  
  
8. 프로젝트를 빌드합니다.  
  
9. Visual Studio 컴퓨터의 **Debug** 폴더와 동일한 경로인 폴더를 원격 컴퓨터에 만듭니다( **\<source path>\MyWPF\MyWPF\bin\Debug**).  
  
10. Visual Studio 컴퓨터에서 방금 빌드한 실행 파일을 원격 컴퓨터에서 새로 만든 폴더에 복사합니다.
  
    > [!CAUTION]
    > Do not make changes to the code or rebuild (or you must repeat this step). 원격 컴퓨터에 복사한 실행 파일은 로컬 소스 및 기호와 정확히 일치해야 합니다.

    You can copy the project manually, use Xcopy, Robocopy, Powershell, or other options.
  
11. Make sure the remote debugger is running on the target machine. (If it's not, search for **Remote Debugger** in the **Start** menu. ) The remote debugger window looks like this.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. In Visual Studio, start debugging (**Debug / Start Debugging**, or **F5**).  
  
13. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials vary depending on your network's security configuration. For example, on a domain computer, you can  enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.

     WPF 애플리케이션의 주 창이 원격 컴퓨터에서 열려 있다고 표시됩니다.
  
14. If necessary, take action to hit the breakpoint. 중단점이 활성화된 것으로 표시되어야 합니다. 활성화되지 않은 경우 애플리케이션에 대한 기호가 로드되지 않은 것입니다. Retry, and if that doesn't work, get information about loading symbols and how troubleshoot them at [Understanding symbol files and Visual Studio’s symbol settings](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Visual Studio 컴퓨터에서 실행이 중단점에서 중지된 것이 표시됩니다.
  
    애플리케이션에서 사용해야 하는 비코드 파일이 있는 경우 Visual Studio 프로젝트에 포함해야 합니다. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). 각 파일에 대한 **속성** 페이지에서 **출력 디렉터리에 복사**를 **항상 복사**로 설정합니다.
  
## <a name="set-up-debugging-with-remote-symbols"></a>원격 기호를 사용한 디버깅 설정  
 Visual Studio 컴퓨터에서 생성하는 기호를 사용하여 코드를 디버그할 수 있습니다. 로컬 기호를 사용하는 경우 원격 디버거의 성능이 훨씬 더 빠릅니다.  원격 기호를 사용해야 경우 원격 컴퓨터에서 기호를 찾도록 원격 디버깅 모니터에 지시해야 합니다.  
  
 Visual Studio 2013 Update 2부터 다음 msvsmon 명령줄 스위치를 통해 관리 코드에 원격 기호를 사용할 수 있습니다. `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 For more information, please see the remote debugging help (press **F1** in the remote debugger window, or click **Help / Usage**). [Visual Studio 2012 및 2013의 .NET 원격 기호 로드 변경 내용](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)에서 자세한 내용을 확인할 수 있습니다.  
  
## <a name="bkmk_winstoreAzure"></a> Remote Debugging on Windows Store and Azure apps  
 For information about remote debugging with Windows Store apps, see [Debug and test Windows Store apps on a remote device from Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Azure의 디버깅에 대한 자세한 내용은 다음 항목 중 하나를 참조하세요.  
  
- [Debugging a Cloud Service or Virtual Machine in Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Debugging the .NET Backend in Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Introduction to Remote Debugging on Azure Web Sites ([Part 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Part 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Part 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>관련 항목:  
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)   
 [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [원격 IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)
