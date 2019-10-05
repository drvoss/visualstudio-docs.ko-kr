---
title: '오류: 웹 서버에서 디버깅을 시작할 수 없습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185477"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>오류: 웹 서버에서 디버깅을 시작할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

웹 서버에서 실행 중인 ASP.NET 응용 프로그램을 디버깅 하려고 할 때이 오류 메시지가 표시 될 수 있습니다. 웹 서버에서 디버깅을 시작할 수 없습니다.
  
대부분의 경우 IIS가 올바르게 구성 되지 않아이 오류가 발생 합니다.

## <a name="vxtbshttpservererrorsthingstocheck"></a> IIS 구성 확인

여기에서는 및 디버깅을 다시 시도 하기 전에 자세한 문제를 해결 하는 단계를 수행한 후 IIS를 다시 설정 해야 할 수 있습니다. 관리자 명령 프롬프트를 열고 입력 하 여 이렇게 `iisreset`, 또는이 IIS 관리자에서를 수행할 수 있습니다. 

* 중지 하 고 응용 프로그램 풀을 다시 시작을 다시 시도 하세요.

    응용 프로그램 풀 중지 될 수 있습니다 또는 중지 하 고 응용 프로그램 풀이 다시 시작 하는 내용을 다른 구성을 변경 해야 할 수 있습니다.
    
    > [!NOTE]
    > 응용 프로그램 풀을 중지 하는 경우 제어판에서 URL 재작성 모듈을 제거 하 고 웹 플랫폼 설치 관리자 (WPI)를 사용 하 여 다시 설치 하는 것이 해야 합니다. 중요 한 시스템을 업그레이드 한 후 문제일 수 있습니다.

* 응용 프로그램 풀 구성을 확인 하 고 필요한 경우 수정 후 다시 시도 하세요.

    암호 자격 증명 변경 되 면 응용 프로그램 풀에서 업데이트 해야 합니다. 또한 ASP.NET 최근에 설치한 경우 ASP.NET의 잘못 된 버전에 대 한 응용 프로그램 풀을 구성할 수 있습니다. 이 문제를 해결 하 고 응용 프로그램 풀을 다시 시작 합니다.
    
* 웹 응용 프로그램 폴더에 올바른 권한이 있는지 확인 합니다.

    IIS_IUSRS를 제공 하거나 IUSR (또는 응용 프로그램 풀과 관련 된 특정 사용자) 읽기 및 웹 응용 프로그램 폴더에 대 한 권한을 실행 해야 합니다. 이 문제를 해결 하 고 응용 프로그램 풀이 다시 시작 합니다.

* 호스트 파일을 로컬 주소를 사용 하 여를 사용 하는 경우 컴퓨터의 IP 주소 대신 루프백 주소를 사용해 보세요.

* 브라우저에서 localhost 페이지 표시 합니다.

     IIS가 올바르게 설치되어 있지 않은 경우 브라우저에 `http://localhost` 를 입력하면 오류가 발생합니다.
     
     IIS에 배포 하는 방법에 대 한 내용은 [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 또는 ASP.NET Core [IIS에 게시](https://docs.asp.net/en/latest/publishing/iis.html)).

* IIS에서 올바른 버전의 ASP.NET가 설치 되었는지 확인 합니다.  참조 [ASP.NET 응용 프로그램 배포](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) 또는 ASP.NET Core [IIS에 게시](https://docs.asp.net/en/latest/publishing/iis.html)).

* 서버에서 기본 ASP.NET 응용 프로그램을 만듭니다.

     서버에서 로컬로 기본 ASP.NET 응용 프로그램을 만들어 보세요 앱 디버거를 사용 하 여 작업을 확인할 수 없는 경우에 기본 응용 프로그램을 디버깅 하려고 합니다. 기본 앱을 디버그할 수 하는 경우는 도움이 될 수 있습니다 두 구성 간의 차이점을 식별 합니다.
  
* IP 주소만 사용하는 경우의 인증 오류 해결

     기본적으로 IP 주소는 인터넷의 일부로 인식되는데 인터넷에서는 NTLM 인증을 수행할 수 없습니다. 웹 사이트를 IIS에서 인증을 요구 하도록 구성 된 경우에이 인증이 실패 합니다. 이 문제를 해결 하려면 원격 컴퓨터에서 IP 주소 대신의 이름을 지정할 수 있습니다.
     
## <a name="other-causes"></a>다른 원인

Visual Studio의 이전 버전 사용 중인 경우:

- 상승 된 권한으로 Visual Studio를 다시 시작 하 고 다시 시도 하세요.

    (나중에 수정) 이전 버전의 버그는 몇 가지 ASP.NET 디버깅 시나리오에서에서 상승 된 권한이 필요 합니다.
    
- Visual Studio의 여러 인스턴스를 실행 하는 경우 Visual Studio의 한 인스턴스에서 프로젝트를 다시 열고 다시 시도 합니다.

## <a name="see-also"></a>참고 항목  
 [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
