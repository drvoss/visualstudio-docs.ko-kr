---
title: '방법: 스크립트에 연결 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 993d1b3b6b4db6b435064a873142f563a950f4db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387853"
---
# <a name="how-to-attach-to-script"></a>방법: 스크립트에 연결
이 항목에서는 디버깅을 위해 스크립트 파일에 Visual Studio 디버거를 수동으로 연결하는 방법에 대해 설명합니다.

### <a name="to-attach-to-a-running-process"></a>실행 중인 프로세스에 연결하려면

1. **디버그** 메뉴에서 **프로세스에 연결**을 선택합니다. (열려 있는 프로젝트가 없으면 **도구** 메뉴에서 **프로세스에 연결**을 선택합니다.)

2. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 연결할 스크립트 프로세스를 찾습니다. **형식** 열에서 스크립트 프로세스를 확인할 수 있습니다.

   1. 디버깅할 프로세스가 다른 컴퓨터에서 실행되고 있으면 먼저 원격 컴퓨터를 선택해야 합니다.

   2. 프로세스가 다른 사용자 계정으로 실행되고 있으면 **모든 사용자의 프로세스 표시** 확인란을 선택합니다.

   3. **원격 데스크톱 연결**을 통해 연결되어 있으면 **모든 세션의 프로세스 표시** 확인란을 선택합니다.

3. 연결할 프로세스를 클릭합니다.

4. 에 **연결할** 상자에 표시 됩니다 **스크립트 코드** 또는 **자동: 스크립트 코드**합니다. 다른 항목이 표시될 경우 다음 단계를 수행합니다.

   1. **선택**을 클릭합니다.

   2. **코드 형식 선택** 대화 상자의 **다음 코드 형식 디버깅**을 클릭하고 **스크립트**를 선택합니다.

   3. **확인**을 클릭합니다.

5. **연결**을 클릭합니다.

    이때 Internet Explorer에서 스크립트 디버깅을 사용할 수 없다는 내용의 경고가 표시될 수 있습니다. 발생 하는 경우 참조 [경고: 스크립트 디버깅 사용 안 함](../debugger/warning-script-debugging-disabled.md)합니다.

   **사용 가능한 프로세스** 목록은 **프로세스** 대화 상자를 열 때 자동으로 표시됩니다. 대화 상자가 열려 있는 동안 백그라운드에서 프로세스를 시작하고 중지할 수 있습니다. 따라서 내용이 현재 상태가 아닐 수 있습니다. 언제든지 **새로 고침** 단추를 눌러 목록을 새로 고쳐 현재 프로세스 목록을 확인할 수 있습니다.

   디버깅하는 동안 여러 프로그램에 연결할 수 있지만 언제든지 디버거에서 활성화되는 프로그램은 한 개뿐입니다. 활성 프로그램은 디버그 위치 도구 모음에서 설정할 수 있습니다. 자세한 내용은 [방법: 현재 프로세스 설정](/previous-versions/visualstudio/visual-studio-2010/d5d4sxdw(v=vs.100))합니다.

   활성 프로그램에는 모든 **디버그** 메뉴 실행 명령이 적용됩니다. 프로세스 대화 상자에서 디버깅된 된 프로그램을 중단할 수 있습니다. 참조 [중단점을 사용 하 여](../debugger/using-breakpoints.md)입니다.

> [!NOTE]
> 신뢰할 수 없는 사용자 계정에서 소유한 프로세스에 연결하면 보안 경고 확인 대화 상자가 나타납니다. 자세한 내용은 참조 하세요. [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 다음 정보가 의심 스 럽 또는 확실 하지 않은 경우이 프로세스에 연결 하지 않는](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)합니다.

 터미널 서비스(원격 데스크톱) 세션에서 디버깅할 때 사용 가능한 프로세스 목록에 사용 가능한 프로세스 중 일부가 표시되지 않는 경우가 있습니다. [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] 이상 버전에서 사용자 계정이 제한된 사용자로 Visual Studio를 실행하는 경우 서비스 및 w3wp.exe를 비롯한 다른 서버 프로세스에 사용되는 세션 0에서 실행되는 프로세스는 사용 가능한 프로세스 목록에 표시되지 않습니다. 관리자 계정으로 Visual Studio를 실행하거나 터미널 서비스 세션 대신 서버 콘솔에서 Visual Studio를 실행하여 이 문제를 해결할 수 있습니다. 이 두 가지 해결 방법을 모두 사용할 수 없으면 세 번째 방법으로 Windows 명령줄에서 vsjitdebugger.exe -p ProcessId를 입력하여 프로세스에 연결합니다. 프로세스 ID는 tlist.exe를 사용하여 확인할 수 있습니다. tlist.exe를 얻으려면 [Windows Hardware Developer Central](/windows-hardware/drivers/dashboard/)에서 Debugging Tools for Windows를 다운로드하여 설치합니다.

## <a name="see-also"></a>참고 항목
- [클라이언트 쪽 스크립트 디버깅](../debugger/client-side-script-debugging.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 잘 모르겠으면 이 프로세스에 연결하지 마세요.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [디버거 보안](../debugger/debugger-security.md)