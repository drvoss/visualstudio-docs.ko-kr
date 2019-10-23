---
title: '오류: 웹 서버가 제대로 구성 되어 있지 않습니다. | Microsoft Docs'
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
ms.openlocfilehash: be5db0a08a287e2611c29396e96e72719b5106a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736920"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>오류: 웹 서버가 제대로 구성되어 있지 않습니다.

여기에 설명 된 단계를 수행 하 여 문제를 해결 한 후 디버깅을 다시 시도 하기 전에 IIS를 다시 설정 해야 할 수도 있습니다. 관리자 명령 프롬프트를 열고 `iisreset`를 입력 하 여이 작업을 수행할 수 있습니다.

이 문제를 해결 하려면 다음 단계를 수행 합니다.

1. 서버에서 호스트 되는 웹 앱이 릴리스 빌드로 구성 된 경우 디버그 빌드로 다시 게시 하 고, 컴파일 요소에서 web.config 파일에 `debug=true` 포함 되어 있는지 확인 합니다. IIS를 다시 설정 하 고 다시 시도 하세요.

    예를 들어 릴리스 빌드에 대 한 게시 프로필을 사용 하는 경우 디버그 및 다시 게시로 변경 합니다. 그렇지 않으면 게시할 때 debug 특성이 `false`로 설정 됩니다.

2. IIS 실제 경로가 올바른지 확인 하십시오. IIS의 **기본 설정 > 실제 경로** (또는 이전 버전의 IIS에서는 **고급 설정** )에서이 설정을 찾을 수 있습니다.

    웹 응용 프로그램을 다른 컴퓨터에 복사 했거나, 수동으로 이름을 바꾸거나, 이동 하는 경우 실제 경로가 올바르지 않을 수 있습니다. IIS를 다시 설정 하 고 다시 시도 하세요.

3. Visual Studio에서 로컬로 디버깅 하는 경우 속성에서 올바른 서버가 선택 되어 있는지 확인 합니다. 프로젝트 형식에 따라 **디버그 >** **웹 > 서버** 또는 속성 >를 엽니다. Web Forms 프로젝트의 경우 **속성 페이지 > 시작 옵션 > 서버**)를 엽니다.

    IIS와 같은 외부 (사용자 지정) 서버를 사용 하는 경우 URL이 올바른지를 지정 해야 합니다. 그렇지 않으면 IIS Express를 선택한 후 다시 시도 하세요.

4. IIS 서버에 올바른 버전의 ASP.NET가 설치 되어 있는지 확인 합니다.

    IIS 및 Visual Studio 프로젝트에서 ASP.NET 버전이 일치 하지 않으면이 문제가 발생할 수 있습니다. Web.config에서 프레임 워크 버전을 설정 해야 할 수도 있습니다. IIS에 ASP.NET를 설치 하려면 [WebPI (웹 플랫폼 설치 관리자)](https://www.microsoft.com/web/downloads/platform.aspx)를 사용 합니다. 또한 [ASP.NET 3.5 및 ASP.NET 4.5을 사용 하는 iis 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 ASP.NET Core의 경우 iis를 사용 하 여 [Windows에서 호스트](https://docs.asp.net/en/latest/publishing/iis.html)를 참조 하세요.

4. IIS의 `maxConnection` 제한이 너무 적고 연결이 너무 많은 경우 [연결 제한을 늘려야](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)할 수 있습니다.

## <a name="see-also"></a>참조
- [원격 IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)