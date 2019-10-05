---
title: '오류: 웹 서버가 올바르게 구성 되지 않았습니다. | Microsoft Docs'
ms.date: 09/20/2017
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc0c61b766b6f93fd1321b15861000d7c628f124
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850405"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>오류: 웹 서버가 제대로 구성되어 있지 않습니다.

문제를 해결 하려면 여기서 설명 하는 단계를 수행한 후 및 디버깅을 다시 시도 하기 전에 IIS를 다시 설정 해야 할 수 있습니다. 관리자 명령 프롬프트를 열고 입력 하 여 이렇게 `iisreset`합니다.

이 문제를 해결 하려면 다음이 단계를 수행 합니다.

1. 서버에서 호스팅되는 웹 앱으로 구성 된 경우 릴리스 빌드에서 디버그 빌드를 다시 게시 및이 web.config 파일에 포함 되어 있는지 확인 하는 `debug=true` 컴파일 요소에 있습니다. IIS 및 다시 시도 다시 설정 합니다.

    예를 들어, 릴리스 빌드에 대 한 게시 프로필을 사용 하는, 하는 경우 디버그로 변경 하 고 다시 게시 합니다. 그렇지 않으면 debug 특성에 설정할 `false` 게시 하는 경우.

2. (IIS) 실제 경로가 올바른지 확인 합니다. IIS에서이 설정을 찾아야 **기본 설정 > 실제 경로** (또는 **고급 설정** 이전 버전의 IIS에서).

    실제 경로 웹 응용 프로그램을 다른 컴퓨터에 복사, 수동으로 이름을 변경 되었거나 이동 하는 경우 위치가 하지 않을 수 있습니다. IIS 및 다시 시도 다시 설정 합니다.

3. Visual Studio에서 로컬로 디버깅 하는, 하는 경우 올바른 서버 속성에서 선택 되어 있는지 확인 합니다. (열려 **속성 > 웹 > 서버** 하거나 **속성 > 디버그** 프로젝트 형식에 따라 합니다. Web Forms 프로젝트를 엽니다 **속성 페이지 > 시작 옵션 > 서버**).

    IIS와 같은 외부 (사용자 지정) 서버를 사용 하는 URL을 올바른 이어야 합니다. 그렇지 않은 경우 IIS Express 및 다시 시도 선택 합니다.

4. (IIS) 서버에서 올바른 버전의 ASP.NET가 설치 되었는지 확인 합니다.

    일치 하지 않는 버전의 Visual Studio 프로젝트에 IIS에서 ASP.NET에는이 문제가 발생할 수 있습니다. Web.config에서 프레임 워크 버전을 설정 해야 합니다. IIS에서 ASP.NET을 설치 하려면 사용 합니다 [웹 플랫폼 설치 관리자 (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)합니다. 도 참조 하세요 [IIS 8.0를 사용 하 여 ASP.NET 3.5 및 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 ASP.NET Core [IIS 사용 하 여 Windows에서 호스트](https://docs.asp.net/en/latest/publishing/iis.html)합니다.

4. 경우는 `maxConnection` IIS에서의 제한은 너무 낮기 및 너무 많은 연결이 해야 할 수 있습니다 [연결 제한을 늘리도록](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)합니다.

## <a name="see-also"></a>참고 항목
- [원격 IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)