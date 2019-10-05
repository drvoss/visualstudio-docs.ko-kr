---
title: 원격 디버깅 오류 및 문제 해결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043336"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>원격 디버깅 오류 및 문제 해결

원격으로 디버그 하려고 할 때 다음 오류가 나올 수 있습니다.

- [오류: 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없음](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [오류: Microsoft Visual Studio 원격 디버깅 모니터(MSVSMON.EXE)가 원격 컴퓨터에서 실행 중인 것 같지 않습니다.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [오류: 원격 머신은 원격 연결 대화 상자에 표시되지 않습니다.](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>관리자 권한으로 원격 디버거를 실행 합니다.

관리자 권한으로 원격 디버거를 실행 하지 않으면 문제 나올 수 있습니다. 예를 들어, 다음과 같은 오류가 표시 될 수 있습니다. "Visual Studio 원격 디버거 (MSVSMON 합니다. EXE)에이 프로세스를 디버깅할 권한이 없습니다. " 표시 될 수 있습니다 (서비스가 아닌) 응용 프로그램으로 원격 디버거를 실행 하는 경우는 [다른 사용자 계정](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) 오류입니다.

### <a name="when-running-the-remote-debugger-as-a-service"></a>원격 디버거가 서비스로 실행 하는 경우

S 서비스로 원격 디버거를 실행 하는 경우에 여러 가지 이유로 관리자로 실행 하는 것이 좋습니다.

- 원격 디버거 서비스는 관리자에 게에서 연결만 허용 **없습니다** 관리자 권한으로 실행 하 여 도입 된 새로운 보안 위험이 있습니다.

- Visual Studio 사용자가 원격 디버거 자체 보다 프로세스를 디버깅 하려면 더 많은 권한을 경우 결과 오류를 방지할 수 있습니다.

- 설치 및 원격 디버거의 구성을 간소화 합니다.

관리자 권한으로 원격 디버거를 실행 하지 않고 디버그할 수 있지만, 올바르게 작동 하도록 몇 가지 요구 사항이 및 고급 서비스 구성 단계가 필요한 경우가 많습니다.

- 원격 컴퓨터에서 사용 하는 계정에 있어야 합니다 **서비스로 로그온** 권한. 단계를 추가 하려면"logon as a service" 아래에 나오는 합니다 [다시 연결할 수 없습니다](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) 오류 문서.

- 계정에는 대상 프로세스를 디버깅할 권한이 있어야 합니다. 이러한 권리를 가져오려면 디버깅할 프로세스와 동일한 계정으로 원격 디버거를 실행 해야 합니다. (쉽게 대신 사용 하는 관리자 권한으로 서비스를 실행 하는.) 

- 계정 (즉, 인증)로 다시 연결할 수 있어야 합니다. 네트워크를 통해 Visual Studio 컴퓨터. 도메인에 기본 제공 로컬 시스템 또는 네트워크 서비스 계정 또는 도메인 계정을 원격 디버거를 실행 하는 경우에 다시 연결할 쉽습니다. 기본 제공 계정 상승 된 보안 위험을 제공할 수 있는 보안 권한이 있어야 합니다.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>응용 프로그램 (기본 모드)으로 원격 디버거를 실행 하는 경우

고유한 낮은 권한의 프로세스 (예: 일반 응용 프로그램)에 연결 하려는 경우 관리자 권한으로 원격 디버거를 실행 하는 경우 중요 하지 않습니다.

여러 시나리오에서 관리자 권한으로 원격 디버거를 실행 하려면:

- 다른 사용자로 실행 중인 프로세스에 연결 하 시겠습니까 (때와 같이 IIS 디버깅), 또는

- 다른 프로세스를 시작 하려는 및 시작 하려면 프로세스 관리자가 있습니다.

할 **되지** 프로세스를 시작 하 고 프로세스를 시작 하는 경우 관리자 권한으로 실행 하려는 **하지** 관리자 여야 합니다.

## <a name="see-also"></a>참고 항목
- [Remote Debugging](../debugger/remote-debugging.md)