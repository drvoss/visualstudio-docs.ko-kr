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
ms.openlocfilehash: f41292c22de1d9c76007ca44cb7accbf82359b3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730025"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>원격 디버깅 오류 및 문제 해결

원격으로 디버깅 하는 동안 다음 오류가 발생할 수 있습니다.

- [Error: Unable to Automatically Step Into the Server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [오류: Microsoft Visual Studio 원격 디버깅 모니터(MSVSMON.EXE)가 원격 컴퓨터에서 실행 중인 것 같지 않습니다.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [오류: 원격 컴퓨터는 원격 연결 대화 상자에 표시되지 않습니다.](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>관리자 권한으로 원격 디버거 실행

원격 디버거를 관리자로 실행 하지 않는 경우 문제가 발생할 수 있습니다. 예를 들어 다음과 같은 오류가 표시 될 수 있습니다. "Visual Studio 원격 디버거 (MSVSMON. EXE)의 권한이 부족 하 여이 프로세스를 디버그할 수 없습니다. " 원격 디버거를 서비스가 아닌 응용 프로그램으로 실행 하는 경우 [다른 사용자 계정](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) 오류가 표시 될 수 있습니다.

### <a name="when-running-the-remote-debugger-as-a-service"></a>원격 디버거를 서비스로 실행 하는 경우

원격 디버거를 서비스로 실행 하는 경우 다음과 같은 여러 가지 이유로 관리자 권한으로 실행 하는 것이 좋습니다.

- 원격 디버거 서비스는 관리자의 연결만 허용 하므로 관리자 권한으로 실행 하 여 새로 도입 된 보안 위험이 **없습니다** .

- Visual Studio 사용자에 게 원격 디버거 자체가 아닌 프로세스를 디버깅할 수 있는 권한이 있는 경우 발생 하는 오류를 방지할 수 있습니다.

- 원격 디버거의 설정 및 구성을 간소화 합니다.

원격 디버거를 관리자로 실행 하지 않고도 디버그할 수 있지만 이러한 작업을 올바르게 수행 하려면 여러 가지 요구 사항을 충족 해야 하며, 종종 고급 서비스 구성 단계가 필요 합니다.

- 원격 컴퓨터에서 사용 중인 계정에는 **로그온 서비스로 로그온** 권한이 있어야 합니다. "서비스로 로그온을 추가 [하려면 오류"](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) 문서의 단계를 참조 하세요.

- 이 계정에는 대상 프로세스를 디버그할 수 있는 권한이 있어야 합니다. 이러한 권한을 얻으려면 디버깅할 프로세스와 동일한 계정으로 원격 디버거를 실행 해야 합니다. (관리자 권한으로 서비스를 실행 하는 것이 더 쉬운 대안입니다.) 

- 이 계정은 네트워크를 통해 Visual Studio 컴퓨터에 다시 연결할 수 있어야 합니다. 도메인에서 원격 디버거가 기본 제공 로컬 시스템 또는 네트워크 서비스 계정 또는 도메인 계정으로 실행 되는 경우 다시 연결 하는 것이 더 쉽습니다. 기본 제공 계정에는 보안 위험을 초래할 수 있는 승격 된 보안 권한이 있습니다.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>원격 디버거를 응용 프로그램으로 실행 하는 경우 (표준 모드)

사용자 고유의 비관리자 프로세스 (예: 일반 응용 프로그램)에 연결 하려는 경우 원격 디버거를 관리자 권한으로 실행 하 고 있는지 여부는 중요 하지 않습니다.

여러 시나리오에서 관리자 권한으로 원격 디버거를 실행 하려고 합니다.

- 다른 사용자로 실행 중인 프로세스에 연결 하려는 경우 (예: IIS를 디버깅할 때) 또는

- 다른 프로세스를 시작 하려고 하는데 실행 하려는 프로세스가 관리자입니다.

프로세스를 시작 하려는 경우 관리자 권한으로 실행 하 **고 싶은 프로세스** 는 관리자가 **아닙니다** .

## <a name="see-also"></a>참조
- [Remote Debugging](../debugger/remote-debugging.md)