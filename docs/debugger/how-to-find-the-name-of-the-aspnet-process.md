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
ms.openlocfilehash: 27221a4ae47b9fb06130b550ceb6d3cc1f00dce0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906807"
---
# <a name="find-the-name-of-the-aspnet-process"></a>ASP.NET 프로세스의 이름 찾기

실행 하는 디버그 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 앱을 Visual Studio 디버거를 연결 해야 합니다는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 이름으로 처리 합니다.

**프로세스는 ASP.NET 앱을 실행 하는 방법을 알아보려면:**

1. Visual Studio에서 실행 되는 앱 선택 **디버깅할** > **프로세스에 연결**합니다.

1. 에 **프로세스에 연결** 프로세스의 첫 문자 다음 목록에서 이름 또는 검색 상자에 입력 대화 상자를 입력 합니다. ASP.NET 앱을 실행 중인 것이입니다. 응용 프로그램을 디버깅 하는 프로세스에 연결 합니다.

    - *w3wp.exe* 는 IIS 6.0 이상.
    - *aspnet_wp.exe* 이전 버전의 IIS 됩니다.
    - *iisexpress.exe* IISExpress 됩니다.
    - *dotnet.exe* ASP.NET core.
    - *inetinfo.exe* 이전 ASP 응용 프로그램 프로세스에서 실행 됩니다.

>[!NOTE]
>Visual Studio 2012 및 이전 버전 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 코드를 파일 시스템에서 테스트 서버에서 실행 *WebDev.WebServer.exe* 하거나 *WebDev.WebServer40.exe*합니다. 이 경우 로컬 디버깅을 위해 연결할 *WebDev.WebServer.exe* 또는 *WebDev.WebServer40.exe* 대신는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 프로세스입니다.

**참고 항목:**

- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [원격 디버깅 웹 응용 프로그램에 대 한 필수 구성 요소](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)
- [시스템 요구 사항](../debugger/aspnet-debugging-system-requirements.md)
- [ASP.NET 애플리케이션 디버그](../debugger/how-to-enable-debugging-for-aspnet-applications.md)