---
title: Windows 스토어 앱 실행을 원격 컴퓨터 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e53e05d9df5a7bbdca5fd8a9b74dd9325dc7aae5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426472"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>원격 컴퓨터에서 Windows 스토어 앱 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows에만 적용] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Visual Studio 원격 도구 앱을 사용하면 한 디바이스에서 실행되는 Windows 스토어 앱을 Visual Studio를 실행하는 다른 컴퓨터에서 실행, 디버깅, 프로파일링 및 테스트할 수 있습니다. Visual Studio 컴퓨터에서 터치, 지리적 위치, 실제 방향 등 Windows 스토어 앱과 관련된 기능을 지원하지 않는 경우 원격 디바이스에서 특히 더 효과적으로 실행할 수 있습니다. 이 항목에서는 원격 세션을 구성하고 시작하는 절차에 대해 설명합니다.  
  
## <a name="BKMK_In_this_topic"></a> 항목 내용  
 다음 내용을 배울 수 있습니다.  
  
 [필수 구성 요소](#BKMK_Prerequisites)  
  
 [보안](#BKMK_Security)  
  
 [원격 장치에 직접 연결하는 방법](#BKMK_DirectConnect)  
  
 [원격 도구 설치](#BKMK_Installing_the_Remote_Tools)  
  
 [원격 디버거 모니터 시작](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [원격 디버거 구성](#BKMK_ConfigureRemoteDebugger)  
  
 [원격 디버깅을 위해 Visual Studio 프로젝트 구성](#BKMK_ConnectVS)  
  
- [C# 및 Visual Basic 프로젝트에 사용할 원격 장치 선택](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [JavaScript 및 C++ 프로젝트에 사용할 원격 장치 선택](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [원격 디버깅 세션 실행](#BKMK_RunRemoteDebug)  
  
## <a name="BKMK_Prerequisites"></a> 필수 구성 요소  
 원격 디바이스에서 디버깅하려면  
  
- 원격 디바이스와 Visual Studio 컴퓨터는 네트워크를 통해 연결되거나 이더넷 케이블을 통해 직접 연결되어야 합니다. 인터넷을 통한 디버깅은 지원되지 않습니다.  
  
- 원격 디바이스에 개발자 라이선스가 설치되어 있어야 합니다.  
  
- 원격 디바이스에서 원격 디버깅 구성 요소가 실행되고 있어야 합니다.  
  
- 원격 디바이스의 관리자만 설치하는 동안 방화벽을 구성할 수 있습니다. 원격 디바이스에 대한 사용자 액세스 권한이 있어야만 원격 디버거를 실행하거나 원격 디버거에 연결할 수 있습니다.  
  
## <a name="BKMK_Security"></a> 보안  
 기본적으로 원격 디버거는 Windows 인증을 사용합니다.  
  
> [!WARNING]
> 원격 디버거를 인증 안 함 모드에서 실행할 수도 있지만 이 모드는 사용하지 않는 것이 좋습니다. 이 모드에서 실행할 때는 네트워크 보안이 없습니다. 네트워크에 악의적인 트래픽이나 유해 트래픽 위험이 확실히 없는 경우에만 인증 안 함 모드를 선택하십시오.  
  
## <a name="BKMK_DirectConnect"></a> 원격 장치에 직접 연결하는 방법  
 원격 디바이스에 직접 연결하려면 Visual Studio 컴퓨터를 표준 이더넷 케이블로 디바이스에 연결합니다. 디바이스에 이더넷 포트가 없는 경우에는 이더넷 어댑터에 USB를 사용하여 케이블에 연결할 수 있습니다.  
  
## <a name="BKMK_Installing_the_Remote_Tools"></a> 원격 도구 설치  
  
> [!NOTE]
> **버전 및 업데이트**  
>   
> **Visual Studio 2015용 원격 도구** 는 이전 버전의 Visual Studio에서 지원되지 않습니다.  
>   
> Visual Studio 설치의 업데이트 버전과 일치하는 Visual Studio 2015용 원격 도구의 업데이트 버전을 설치하는 것이 좋습니다.  
>   
> VS 디버거는 VS 2015 및 VS 2015용 원격 도구의 어떤 버전 조합과도 호환됩니다. 하지만 Visual Studio의 최신 기능을 사용하려면 Visual Studio와 원격 도구 모두 최신 버전이어야 합니다.  
>   
> 다른 진단 도구를 사용할 경우 원격 도구와 Visual Studio가 동일한 버전이어야 할 수 있습니다.  
  
 **원격 장치에 원격 디버깅 구성 요소 설치**  
  
 를 실행 하거나 원격 도구용 설치 프로그램을 저장 하려면 Visual Studio의 버전과 일치 하는이 표의 링크 중 하나를 선택 합니다.  
  
|버전|링크|노트|
|-|-|-|
|Visual Studio 2015 업데이트 3|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|메시지가 표시 되 면 무료 Visual Studio Dev Essentials 그룹에 가입 또는 유효한 Visual Studio 구독을 사용 하 여 로그인만 서명할 수 있습니다. 그런 다음 다시 링크를 열 필요한 경우. 항상 일치 (x 86, x64 또는 ARM 버전)에 장치 운영 체제 버전을 다운로드|
|Visual Studio 2015 (이전)|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|메시지가 표시 되 면 무료 Visual Studio Dev Essentials 그룹에 가입 또는 유효한 Visual Studio 구독을 사용 하 여 로그인만 서명할 수 있습니다. 그런 다음 다시 링크를 열 필요한 경우. 항상 일치 (x 86, x64 또는 ARM 버전)에 장치 운영 체제 버전을 다운로드|
|Visual Studio 2013|[원격 도구](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 설명서에서 페이지를 다운로드 합니다.|
  
 설치 프로그램을 선택하여 다운로드하거나 즉시 실행할 수 있습니다. 설치 프로그램을 실행할 때 사용자 계약에 동의한 다음 **설치**를 선택합니다.  
  
 기본적으로 원격 디버깅 구성 요소는 **C:\Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger** 폴더에 설치됩니다.  
  
## <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> 원격 디버거 모니터 시작  
  
> [!NOTE]
> 원격 디버거가 Visual Studio 호스트와의 통신을 허용하도록 방화벽을 구성하기 때문에 원격 디버거를 처음 시작할 때는 원격 디바이스의 관리자여야 합니다.  
  
 원격 도구를 설치한 후 **시작** 화면에서 **원격 디버거** 를 선택합니다. 원격 디버거를 처음 시작하면 **원격 디버깅 구성** 이 나타납니다.  
  
 **원격 디버깅 구성** 대화 상자에서 다음을 수행합니다.  
  
1. Windows 웹 서비스 API가 설치되어 있지 않으면 **설치**를 선택합니다.  
  
2. **Windows 방화벽 구성** 그룹에서 연결을 허용할 네트워크를 선택합니다. 현재 디바이스가 연결되어 있는 네트워크만 사용할 수 있습니다. 네트워크를 하나 이상 선택해야 합니다.  
  
3. **원격 디버깅 구성** 을 선택하여 방화벽 옵션을 설정하고 원격 디버거를 시작합니다.  **Visual Studio 원격 디버깅 모니터** 대화 상자를 열어 원격 도구에 대한 사용자 권한을 부여하고 다른 고급 옵션을 설정합니다.  
  
4. **Visual Studio 원격 디버깅 모니터** 대화 상자가 나타납니다. 이 대화 상자에서 사용자에게 원격 도구에 대한 권한을 부여하고 기타 고급 옵션을 설정할 수 있습니다.  
  
## <a name="BKMK_ConfigureRemoteDebugger"></a> 원격 디버거 구성  
 두 도구를 사용하여 원격 디버거의 구성을 수정할 수 있습니다.  
  
1. **Visual Studio 원격 디버깅 모니터** 의 **도구**메뉴에서 다음 작업을 수행합니다.  
  
   1. **옵션** 을 선택하여 원격 디버거의 포트 번호, 인증 모드 또는 시간 제한 간격을 변경합니다.  
  
   2. **사용 권한** 을 선택하여 원격 디버깅에 대한 사용 권한이 있는 사용자를 추가하거나 제거합니다.  
  
       > [!NOTE]
       > 사용 권한은 원격으로 디버깅하는 모든 사용자 계정에 부여해야 합니다.  
  
   **원격 디버거 구성 마법사** 를 사용하여 원격 디버거에 대한 고급 옵션을 설정합니다. 마법사를 열려면 시작 화면에서 **원격 디버거 구성 마법사** 를 선택합니다.  
  
2. **Visual Studio 원격 디버거 구성** 페이지에서 원격 디버거를 서비스로 실행할 수 있습니다. 대부분의 경우 서비스로 실행할 필요는 없습니다.  
  
3. **디버깅할 수 있도록 Windows 방화벽 구성** 페이지에서 원격 디버거가 연결할 네트워크의 형식을 추가하거나 제거할 수 있습니다. 현재 디바이스가 연결되어 있는 네트워크만 사용할 수 있습니다. 네트워크를 하나 이상 선택해야 합니다.  
  
## <a name="BKMK_ConnectVS"></a> 원격 디버깅을 위해 Visual Studio 프로젝트 구성  
 프로젝트 속성에서 연결할 원격 디바이스를 지정합니다. 절차는 프로그래밍 언어에 따라 다릅니다. 원격 디바이스의 네트워크 이름을 입력하거나 원격 디버거 연결 선택 대화 상자에서 해당 이름을 선택할 수 있습니다.  
  
 ![원격 디버거 연결 대화 상자를 선택](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 이 대화 상자에는 Visual Studio 컴퓨터의 로컬 서브넷에 있으며 원격 디버거를 실행 중인 디바이스만 나열됩니다.  
  
> [!TIP]
> 원격 디바이스에 연결하는 데 문제가 있을 경우 디바이스의 IP 주소를 입력해 보십시오. 디바이스의 IP 주소를 확인하려면 명령 창을 연 다음 **ipconfig**를 입력합니다. 그러면 IP 주소가 **IPv4 Address**로 나열됩니다.  
  
### <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> C# 및 Visual Basic 프로젝트에 사용할 원격 장치 선택  
 ![원격 디버깅에 대 한 프로젝트 속성 관리](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1. 솔루션 탐색기에서 프로젝트 이름을 선택한 다음 바로 가기 메뉴에서 **속성** 을 선택합니다.  
  
2. **디버그**를 선택합니다.  
  
3. **대상 장치** 목록에서 **원격 컴퓨터** 를 선택합니다.  
  
4. **원격 컴퓨터** 상자에 원격 장치의 네트워크 이름을 입력하거나 **찾기** 를 선택하여 **원격 디버거 연결 선택** 대화 상자에서 장치를 선택합니다.  
  
### <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> JavaScript 및 C++ 프로젝트에 사용할 원격 장치 선택  
 ![C&#43; &#43; 프로젝트 속성 원격 디버깅용](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1. 솔루션 탐색기에서 프로젝트 이름을 선택한 다음 바로 가기 메뉴에서 **속성** 을 선택합니다.  
  
2. **구성 속성** 노드를 확장한 다음 **디버깅**을 선택합니다.  
  
3. **실행할 디버거** 목록에서 **원격 디버거** 를 선택합니다.  
  
4. **컴퓨터 이름** 상자에 원격 장치의 네트워크 이름을 입력하거나 해당 상자에서 아래쪽 화살표를 선택하여 **원격 디버거 연결 선택** 대화 상자에서 장치를 선택합니다.  
  
## <a name="BKMK_RunRemoteDebug"></a> 원격 디버깅 세션 실행  
 로컬 세션의 경우와 같은 방법으로 원격 디버그 세션을 시작, 중지, 탐색할 수 있습니다. 디버깅을 시작하기 전에 원격 디바이스에서 원격 디버깅 모니터가 실행되고 있는지 확인합니다.  
  
 선택한 **디버깅 시작** 에 **디버그** 메뉴 (키보드: F5)을 선택합니다. 프로젝트가 다시 컴파일된 다음 원격 디바이스에 배포되어 시작됩니다. 디버거는 중단점에서 실행을 일시 중단하며 사용자는 한 단계씩 코드를 실행하거나, 프로시저 단위로 실행하거나 코드를 종료하여 한 번에 한 줄씩 실행할 수 있습니다. **디버깅 중지** 를 선택하여 디버그 세션을 끝내고 원격 응용 프로그램을 종료할 수 있습니다. 자세한 내용은 [Visual Studio에서 앱을 디버그](../debugger/debug-store-apps-in-visual-studio.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio로 스토어 앱 테스트](../test/testing-store-apps-with-visual-studio.md)   
 [Visual Studio에서 앱 디버그](../debugger/debug-store-apps-in-visual-studio.md)
