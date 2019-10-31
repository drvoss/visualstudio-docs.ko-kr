---
title: 실행 중인 ASP.NET 프로세스 찾기 | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187663"
---
# <a name="find-the-name-of-the-aspnet-process"></a>ASP.NET 프로세스의 이름 찾기

실행 중인 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 앱을 디버깅 하려면 Visual Studio 디버거가 이름으로 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 프로세스에 연결 되어야 합니다.

**ASP.NET 앱을 실행 하는 프로세스를 확인 하려면 다음을 수행 합니다.**

1. 앱을 실행 하는 동안 Visual Studio에서 **디버그** > **프로세스에 연결**을 선택 합니다.

1. **프로세스에 연결** 대화 상자에서 다음 목록에 있는 프로세스 이름의 첫 문자를 입력 하거나 검색 상자에 입력 합니다. 실행 되는는 ASP.NET 앱을 실행 하는 것입니다. 앱을 디버깅 하려면 해당 프로세스에 연결 합니다.

    - w3wp.exe *는 IIS 6.0 이상입니다.*
    - *aspnet_wp.exe* 는 IIS의 이전 버전입니다.
    - *iisexpress* 는 iisexpress입니다.
    - *dotnet* 이 ASP.NET Core 됩니다.
    - *inetinfo.exe* 는 in-process로 실행 되는 오래 된 ASP 응용 프로그램입니다.

>[!NOTE]
>Visual Studio 2012 및 이전 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 코드는 파일 시스템에 있고 테스트 서버 *웹* *WebServer40 또는 webdev*. .exe에서 실행할 수 있습니다. 이 경우 로컬 디버깅의 경우 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 프로세스 대신 WebServer40 *또는* *webdev. .exe* 에 연결 합니다.

**참고 항목:**

- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [웹 응용 프로그램 원격 디버깅을 위한 필수 구성 요소](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [시스템 요구 사항](../debugger/aspnet-debugging-system-requirements.md)
- [ASP.NET 애플리케이션 디버그](../debugger/how-to-enable-debugging-for-aspnet-applications.md)