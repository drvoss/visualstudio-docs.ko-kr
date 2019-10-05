---
title: 원격 컴퓨터에서 UWP 앱 디버그 | Microsoft Docs
ms.date: 10/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 50d307cd65bfdf534b6ca3586e69bbc27be25e36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902886"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Visual Studio에서 원격 컴퓨터에서 UWP 앱 디버그

실행, 디버그, 프로필 및 다른 컴퓨터 또는 장치에서 유니버설 Windows 플랫폼 (UWP) 앱을 테스트 하려면 Visual Studio를 사용할 수 있습니다. 원격 컴퓨터에서 UWP 앱을 실행 중인 Visual Studio 컴퓨터는 터치, 지리적 위치, 실제 방향 등의 UWP 특정 기능을 지원 하지 않는 경우 특히 유용 합니다.

## <a name="BKMK_Prerequisites"></a> 필수 조건

Visual Studio에서 원격 장치에서 UWP 앱을 디버그 합니다.

- Visual Studio 프로젝트를 원격 디버깅을 위해 구성 되어야 합니다.
- 원격 컴퓨터와 Visual Studio 컴퓨터를 네트워크를 통해 연결 하거나 USB 또는 이더넷 케이블을 통해 직접 연결 해야 합니다. 인터넷을 통한 디버깅은 지원되지 않습니다.
- 수행 해야 합니다 [개발자 모드 켜기](/windows/uwp/get-started/enable-your-device-for-development) Visual Studio 컴퓨터와 원격 컴퓨터.
- 원격 컴퓨터는 Visual Studio 용 원격 도구 실행 되어야 합니다.
  - 시작 하 고 자동으로 원격 도구를 실행 하는 일부 Windows 10 버전입니다. 그렇지 않으면 [설치 하 고 Visual Studio 용 원격 도구를 실행](#BKMK_download)합니다.
  - Windows 10 모바일 장치 필요 하지 않거나 원격 도구를 지원 합니다.

## <a name="BKMK_ConnectVS"></a> 원격 디버깅을 위해 Visual Studio 프로젝트 구성
<a name="BKMK_DirectConnect"></a> 프로젝트를 사용할 **속성** 연결할 원격 장치를 지정 합니다. 설정을 프로그래밍 언어에 따라 다릅니다.

> [!CAUTION]
> 기본적으로 속성 페이지 설정 **유니버설 (암호화 되지 않은 프로토콜)** 으로 **인증 유형을** Windows 10 원격 연결에 대 한 합니다. 으로 설정 해야 **인증 없음** 원격 디버거를 연결할 수 있습니다. **유니버설 (암호화 되지 않은 프로토콜)** 하 고 **인증 안 함** 개발 및 원격 컴퓨터 간에 전달 된 데이터는 취약 한 프로토콜은 네트워크 보안이 없습니다. 이러한 인증 형식이 있는 신뢰할 수 있는 네트워크에 대해서만 확인 되지 악의적인 트래픽이나 유해 트래픽 위험이 선택 합니다.
>
>선택 하면 **Windows 인증** 에 대 한 합니다 **인증 유형을**를 디버깅할 때 원격 컴퓨터에 로그인 해야 합니다. 원격 디버거를 실행 해야 합니다 **Windows 인증** 모드, Visual Studio 컴퓨터와 동일한 사용자 계정입니다.

### <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> 구성 된 C# 또는 원격 디버깅을 위해 Visual Basic 프로젝트

1. 선택 된 C# 또는 Visual Studio에서 Visual Basic 프로젝트 **솔루션 탐색기** 선택한는 **속성** 아이콘을 눌러 **Alt** +  **입력**를 마우스 오른쪽 단추로 클릭 하 고 선택 하거나 **속성**합니다.

1. **디버그** 탭을 선택합니다.

1. 아래 **대상 장치**를 선택 **원격 컴퓨터** 원격 컴퓨터의 경우 또는 **장치** 직접 연결 된 Windows 10 Mobile 장치에 대 한 합니다.

1. 원격 컴퓨터에 대 한 네트워크 이름 또는 IP 주소를 입력 합니다 **원격 컴퓨터** 필드 또는 선택 **찾을** 장치에 대 한 검색할를 [원격 연결 대화 상자](#remote-connections).

    ![원격 디버깅에 대 한 프로젝트 속성 관리](../debugger/media/vsrun_managed_projprop_remote.png "디버그 관리 되는 프로젝트 속성")

### <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> 구성 된 C++ 원격 디버깅을 위해 프로젝트

1. 선택 된 C++ Visual Studio에서 프로젝트 **솔루션 탐색기** 선택한는 **속성** 아이콘을 눌러 **Alt**+**Enter**를 마우스 오른쪽 단추로 클릭 하 고 선택 하거나 **속성**합니다.

1. 선택 된 **디버깅** 탭 합니다.

3. 아래 **실행할 디버거**를 선택 **원격 컴퓨터** 원격 컴퓨터의 경우 또는 **장치** 직접 연결 된 Windows 10 Mobile 장치에 대 한 합니다.

1. 원격 컴퓨터에 대 한 입력 또는 네트워크 이름 또는 IP 주소를 선택 합니다 **컴퓨터 이름** 필드 또는 드롭 다운 하 고 선택할 **찾기** 장치에 대 한 검색 하는 [원격 연결 대화 상자 ](#remote-connections).

    ![C++원격 디버깅에 대 한 속성을 프로젝트](../debugger/media/vsrun_cpp_projprop_remote.png " C++ 디버깅 프로젝트 속성")

### <a name="remote-connections"></a> 원격 연결 대화 상자를 사용 합니다.

에 **원격 연결** 대화 상자에서 특정 원격 컴퓨터 이름 또는 IP 주소를 검색 하거나 반올림 화살표 새로 고침 아이콘을 선택 하 여 연결이 자동으로 검색 합니다. 대화 상자에 원격 디버거를 현재 실행 중인 로컬 서브넷의 장치만 검색 합니다. 모든 장치에서 검색할 수는 **원격 연결** 대화 상자.

 ![원격 연결 대화 상자](../debugger/media/vsrun_selectremotedebuggerdlg.png "원격 연결 대화 상자")

>[!TIP]
>이름으로 원격 장치에 연결할 수 없으면, 해당 IP 주소를 사용해 보세요. 원격 장치의 IP 주소를 확인 하려면 입력 **ipconfig** 명령 창에서. IP 주소 요소로 **IPv4 주소**합니다.

## <a name="BKMK_download"></a> Visual Studio용 원격 도구 다운로드 및 설치

원격 컴퓨터에서 앱을 디버깅 하려면 Visual Studio에 대 한 원격 컴퓨터 실행 되어야 합니다 원격 도구를 Visual Studio 용.

- Windows 10 모바일 장치 필요 하지 않거나 원격 도구를 지원 합니다.
- 작성자의을 실행 하는 Windows 10 Pc 업데이트 (버전 1703) 하 고 나중에 Windows 10의 Xbox, IoT 및 HoloLens 장치 원격 도구 설치 자동으로 앱을 배포 하는 경우 키를 누릅니다.
- Pre-크리에이터 업데이트 Windows 10 pc에서 하 해야 수동으로 다운로드, 설치 및 디버깅을 시작 하기 전에 원격 컴퓨터에서 원격 도구를 실행 합니다.

**다운로드 하 고 원격 도구를 설치 합니다.**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> 원격 도구 구성

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="BKMK_RunRemoteDebug"></a> UWP 앱을 원격으로 디버그

원격 디버깅 로컬 디버깅으로 동일 하 게 작동 합니다.

1. Pre-크리에이터 업데이트 버전의 Windows 10에서 해야 원격 디버깅 모니터 (*msvsmon.exe*) 원격 장치에서 실행 됩니다.

1. Visual Studio 컴퓨터에 있는지 확인 올바른 디버깅 대상 (**원격 컴퓨터** 하거나 **장치**) 도구 모음에서 녹색 화살표 옆에 나타납니다.

1. 선택 하 여 디버깅을 시작할 **디버그** > **디버깅 시작**을 **F5**, 도구 모음에서 녹색 화살표를 선택 합니다.

   프로젝트 다시 컴파일하는 다음 고 배포 하 고 원격 장치에서 시작 합니다. 디버거가 중단점에서 실행을 일시 중단 하 고, 조치 내부 및 외부로 코드를 실행할 수 있습니다.

1. 필요한 경우 선택 **디버그** > **디버깅 중지** 누르거나 **Shift**+**F5** 디버깅을 중지 하 고 원격 응용 프로그램을 닫습니다.

## <a name="see-also"></a>참고자료
- [고급 원격 배포 옵션](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Visual Studio로 UWP 앱 테스트](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [Visual Studio에서 UWP 앱 디버그](debugging-windows-store-and-windows-universal-apps.md)
