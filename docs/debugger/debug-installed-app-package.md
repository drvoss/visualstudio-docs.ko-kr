---
title: 설치 된 UWP 앱 패키지 디버그 | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d5c2e94e9fa80145489bddfb005b7136bdff8a71
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211296"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Visual Studio에서 설치 된 UWP 앱 패키지 디버그

Visual Studio는 Windows 10 컴퓨터 및 Xbox, HoloLens 및 IoT 장치에서 설치 된 UWP (유니버설 Windows 플랫폼) 앱 패키지를 디버그할 수 있습니다.

>[!NOTE]
>설치 된 UWP 앱에 대 한 Visual Studio 디버깅은 휴대폰에서 지원 되지 않습니다.

UWP 앱을 디버깅 하는 방법에 대 한 자세한 내용은 [설치 된 앱 패키지 디버깅](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) 및 [Uwp (유니버설 Windows 앱) 빌드](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/)에 대 한 블로그 게시물을 참조 하세요.

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>로컬 컴퓨터에 설치 된 UWP 앱 디버그

1. Visual Studio에서 **디버그** > **기타 디버그 대상** > 디버그**설치 된 앱 패키지**를 선택 합니다.

1. **설치 된 응용 프로그램 패키지 디버그** 대화 상자의 **연결 형식**에서 **로컬 컴퓨터**를 선택 합니다.

1. **설치 된 앱 패키지**에서 디버깅 하려는 앱을 선택 하거나 검색 상자에 이름을 입력 합니다. 실행 되지 않는 설치 된 앱 패키지는 **실행**중이 아닌 것으로 나타나고 실행 중인 앱이 **실행**되 고 있습니다.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. 필요한 경우 다음 **코드 형식 디버그**에서 코드 형식을 변경 하 고 기타 옵션을 선택 합니다.
   - 앱이 시작 될 때 디버깅을 시작할 **때 시작 하지 않음 (시작 시 코드 디버그)을** 선택 합니다. 앱을 시작할 때 디버깅을 시작 하는 것은 사용자 지정 매개 변수를 사용 하 여 프로토콜 활성화와 같은 [여러 시작 메서드에서](/windows/uwp/xbox-apps/automate-launching-uwp-apps)제어 경로를 디버깅 하는 효과적인 방법입니다.

1. **시작**을 선택 하거나, 앱이 실행 되 고 있는 경우 **연결**을 선택 합니다.

> [!NOTE]
> Visual Studio에서**프로세스에 연결** **디버그** > 를 선택 하 여 실행 중인 UWP 또는 다른 앱 프로세스에 연결할 수도 있습니다. 원래 Visual Studio 프로젝트는 실행 중인 프로세스에 연결할 필요가 없지만 응용 프로그램 기호 로드는의 원래 코드가 없는 프로세스를 디버그할 때 상당히 유용 합니다. [디버거에서 기호 및 소스 파일 지정](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조 하세요.

## <a name="remote"></a>원격 컴퓨터 또는 장치에서 설치 된 UWP 앱 디버그

Visual Studio가 설치 된 UWP 앱을 Windows 10 장치 또는 원격 게시의 업데이트 Windows 10 컴퓨터에 처음으로 디버그할 때 대상 장치에 원격 디버깅 도구를 설치 합니다.

1. Visual Studio 컴퓨터와 원격 장치 또는 컴퓨터에서 [개발자 모드를 사용 하도록 설정](/windows/uwp/get-started/enable-your-device-for-development) 합니다.

1. 이전 Creator의 업데이트 Windows 10을 실행 하는 원격 컴퓨터에 연결 하는 경우 원격 컴퓨터에서 [원격 디버거를 수동으로 설치 하 고 시작](../debugger/remote-debugging.md) 합니다.

1. Visual Studio 컴퓨터에서 **디버그** > **기타 디버그 대상** > 디버그**설치 된 앱 패키지**를 선택 합니다.

1. **설치 된 응용 프로그램 패키지 디버그** 대화 상자의 **연결 형식**에서 **원격 컴퓨터** 또는 **장치**를 선택 합니다.

   **장치**를 선택 하는 경우 컴퓨터는 Windows 10 장치에 물리적으로 연결 되어 있어야 합니다.

   원격 컴퓨터의 경우 컴퓨터 주소가 **주소**옆에 표시 되지 않으면 **변경**을 선택 합니다.

   1. **원격 연결** 대화 상자에서 **주소**옆에 연결 하려는 컴퓨터의 이름 또는 IP 주소를 입력 합니다.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      디버거가 컴퓨터 이름을 사용 하 여 원격 컴퓨터에 연결할 수 없는 경우 대신 IP 주소를 사용 합니다. Xbox, HoloLens 또는 IoT 장치에 대 한 IP 주소를 사용 합니다.
   1. **인증 모드**옆의 인증 옵션을 선택 합니다.

      대부분의 앱에서 기본값인 **범용 (암호화 되지 않은 프로토콜)** 을 유지 합니다.
   1. **선택**을 선택 합니다.

1. **설치 된 앱 패키지**에서 디버깅 하려는 앱을 선택 하거나 검색 상자에 이름을 입력 합니다. 실행 되지 않는 설치 된 앱 패키지는 **실행**중이 아닌 것으로 나타나고 실행 중인 앱이 **실행**되 고 있습니다.

1. 필요한 경우 다음 **코드 형식 디버그**에서 코드 형식을 변경 하 고 기타 옵션을 선택 합니다.
   - 앱이 시작 될 때 디버깅을 시작할 **때 시작 하지 않음 (시작 시 코드 디버그)을** 선택 합니다. 앱을 시작할 때 디버깅을 시작 하는 것은 사용자 지정 매개 변수를 사용 하 여 프로토콜 활성화와 같은 [여러 시작 메서드에서](/windows/uwp/xbox-apps/automate-launching-uwp-apps)제어 경로를 디버깅 하는 효과적인 방법입니다.

1. **시작**을 선택 하거나, 앱이 실행 되 고 있는 경우 **연결**을 선택 합니다.

연결 된 Xbox, HoloLens 또는 IoT 장치에서 처음 설치 된 앱 패키지의 디버깅을 시작 하면 Visual Studio에서 대상 장치에 대 한 올바른 버전의 원격 디버거를 설치 합니다. 원격 디버거를 설치 하는 데 시간이 걸릴 수 있으며 **원격 디버거 시작** 메시지는 발생 하는 동안 표시 됩니다.

>[!NOTE]
>현재 Xbox 또는 HoloLens 장치는 이미 실행 중인 디버거가 연결 된 앱을 다시 시작 합니다.

UWP 앱의 원격 배포에 대 한 자세한 내용은 [uwp 앱 배포 및 디버그](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) 및 [원격 컴퓨터에서 uwp 앱 디버그](run-windows-store-apps-on-a-remote-machine.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [원격 디버깅](../debugger/remote-debugging.md)
- [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)