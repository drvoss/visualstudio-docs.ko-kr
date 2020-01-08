---
title: '오류: 웹 서버에서 디버깅을 시작할 수 없습니다. | Microsoft Docs'
ms.date: 05/23/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f0e3666c313c55df605cd7b79199827765f40f3
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404346"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>오류: 웹 서버에서 디버깅을 시작할 수 없습니다.

웹 서버에서 실행 되는 ASP.NET 응용 프로그램을 디버깅 하려고 하면 다음과 같은 오류 메시지가 표시 될 수 있습니다. `Unable to start debugging on the Web server`.

이 오류는 종종 응용 프로그램 풀, IIS 다시 설정 또는 둘 모두에 대 한 업데이트가 필요한 오류 또는 구성 변경이 발생 했기 때문에 발생 합니다. 관리자 권한 명령 프롬프트를 열고 `iisreset`를 입력 하 여 IIS를 다시 설정할 수 있습니다.

## <a name="specificerrors"></a>자세한 오류 메시지는 무엇입니까?

`Unable to start debugging on the Web server` 메시지는 일반 메시지입니다. 일반적으로 보다 구체적인 메시지는 오류 문자열에 포함 되며 문제의 원인을 파악 하는 데 도움이 될 수 있으며 보다 정확한 수정 사항을 검색 하는 데 도움이 될 수 있습니다. 다음은 기본 오류 메시지에 추가 되는 몇 가지 일반적인 오류 메시지입니다.

- [IIS는 시작 url과 일치 하는 웹 사이트를 나열 하지 않습니다.](#IISlist)
- [웹 서버가 제대로 구성되어 있지 않습니다.](#web_server_config)
- [웹 서버에 연결할 수 없습니다.](#unabletoconnect)
- [웹 서버가 적시에 응답 하지 않았습니다.](#webservertimeout)
- [Microsoft Visual Studio 원격 디버깅 모니터(msvsmon.exe)가 원격 컴퓨터에서 실행 중인 것 같지 않습니다.](#msvsmon)
- [원격 서버에서 오류를 반환 했습니다.](#server_error)
- [ASP.NET 디버깅을 시작할 수 없습니다.](#aspnet)
- [디버거가 원격 컴퓨터에 연결할 수 없습니다.](#cannot_connect)
- [일반적인 구성 오류는 도움말을 참조하십시오. 디버거 외부에서 웹 페이지를 실행 합니다. 추가 정보가 제공 될 수 있습니다.](#see_help)
- [지원 되지 않는 작업입니다. 알 수 없는 오류: *오류 번호*](#operation_not_supported)

## <a name="IISlist"></a>IIS는 시작 url과 일치 하는 웹 사이트를 나열 하지 않습니다.

- 관리자 권한으로 Visual Studio를 다시 시작 하 고 디버깅을 다시 시도 합니다. (일부 ASP.NET 디버깅 시나리오에는 상승 된 권한이 필요 합니다.)

    Visual studio 바로 가기 아이콘을 마우스 오른쪽 단추로 클릭 하 고 **속성 > 고급**을 선택한 다음 항상 관리자 권한으로 실행을 선택 하 여 visual studio를 항상 관리자 권한으로 실행 하도록 구성할 수 있습니다.

## <a name="web_server_config"></a> 웹 서버가 제대로 구성되어 있지 않습니다.

- [웹 서버가 제대로 구성 되어 있지 않습니다. 오류](../debugger/error-the-web-server-is-not-configured-correctly.md)를 참조 하십시오.

## <a name="unabletoconnect"></a>웹 서버에 연결할 수 없습니다.

- Visual Studio와 웹 서버를 동일한 컴퓨터에서 실행 하 고 **F5 키** 를 사용 하 여 디버깅 하 고 ( **프로세스에 연결**하는 대신)? 프로젝트 속성을 열고 프로젝트가 올바른 웹 서버에 연결 하도록 구성 되어 있는지 확인 하 고 URL을 시작 합니다. 프로젝트 형식에 따라 **디버그 >** **웹 > 서버** 또는 속성 >를 엽니다. Web Forms 프로젝트의 경우 **속성 페이지 > 시작 옵션 > Server**를 엽니다.

- 그렇지 않으면 응용 프로그램 풀을 다시 시작한 다음 IIS를 다시 설정 합니다. 자세한 내용은 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조 하세요.

## <a name="webservertimeout"></a>웹 서버가 적시에 응답 하지 않았습니다.

- IIS를 다시 설정 하 고 디버깅을 다시 시도 합니다. 여러 디버거 인스턴스를 IIS 프로세스에 연결할 수 있습니다. reset은이를 종료 합니다. 자세한 내용은 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조 하세요.

## <a name="msvsmon"></a> Microsoft Visual Studio 원격 디버깅 모니터(msvsmon.exe)가 원격 컴퓨터에서 실행 중인 것 같지 않습니다.

- 원격 컴퓨터에서 디버깅 하는 경우 [원격 디버거를 설치 하 고 실행](../debugger/remote-debugging.md)중인지 확인 합니다. 메시지가 방화벽을 언급 하는 경우, 특히 타사 방화벽을 사용 하는 경우 [방화벽의 올바른 포트가](../debugger/remote-debugger-port-assignments.md) 열려 있는지 확인 합니다.
- HOSTS 파일을 사용 하는 경우 올바르게 구성 되어 있는지 확인 합니다. 예를 들어 **F5 키** 를 사용 하 여 디버깅 하는 경우 ( **프로세스에 연결 하**는 대신) 호스트 파일은 프로젝트 형식에 따라 프로젝트 속성, **속성 > 웹 > 서버** 또는 **> 속성과**동일한 프로젝트 URL을 포함 해야 합니다.

## <a name="server_error"></a>원격 서버에서 오류를 반환 했습니다.

[Iis 로그 파일](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) 에서 오류 하위 및 추가 정보를 확인 하 고이 iis 7 [블로그 게시물](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)을 참조 하십시오.

또한 몇 가지 일반적인 오류 코드와 몇 가지 제안 사항이 있습니다.
- (403) 사용할 수 없습니다. 이 오류가 발생할 수 있는 원인에는 여러 가지가 있으므로 해당 웹 사이트의 로그 파일 및 IIS 보안 설정을 확인 하십시오. 서버 web.config의 컴파일 요소에 `debug=true` 포함 되어 있는지 확인 합니다. 웹 응용 프로그램 폴더에 올바른 권한이 있는지와 응용 프로그램 풀 구성이 올바른지 확인 합니다 (암호가 변경 되었을 수 있음). [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조 하세요. 이러한 설정이 이미 올바르고 로컬에서 디버그 하는 경우에는 프로젝트 형식에 따라 웹 > 서버 또는 **> 속성** **> 웹 서버** 또는 속성에서 올바른 서버 유형 및 URL에 연결 하 고 있는지도 확인 합니다.
- (503) 서버를 사용할 수 없습니다. 오류 또는 구성 변경으로 인해 응용 프로그램 풀이 중지 되었을 수 있습니다. 응용 프로그램 풀을 다시 시작 합니다.
- (404) 찾을 수 없습니다. 응용 프로그램 풀이 올바른 버전의 ASP.NET에 대해 구성 되어 있는지 확인 합니다.

## <a name="aspnet"></a>ASP.NET 디버깅을 시작할 수 없습니다.

- 응용 프로그램 풀을 다시 시작 하 고 IIS를 다시 설정 하십시오. 자세한 내용은 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조 하세요.
- URL 다시 쓰기를 수행 하는 경우 URL을 다시 작성 하지 않고 기본 web.config를 테스트 합니다. [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)에서 URL 다시 쓰기 모듈에 대 한 **참고** 를 참조 하세요.

## <a name="cannot_connect"></a>디버거가 원격 컴퓨터에 연결할 수 없습니다.

로컬로 디버깅 하는 경우 Visual Studio에서 프로젝트 속성을 열고 프로젝트가 올바른 웹 서버 및 URL에 연결 하도록 구성 되어 있는지 확인 합니다. (프로젝트 형식에 따라 **디버그 >** **웹 > 서버** 또는 속성 >를 엽니다.

이 오류는 Visual Studio가 32 비트 응용 프로그램 이므로 로컬로 디버그할 때 발생할 수 있으므로 64 비트 버전의 원격 디버거를 사용 하 여 64 비트 응용 프로그램을 디버그 합니다. IIS의 앱 풀에서 **32 비트 응용 프로그램 사용** 이 `true`로 설정 되어 있는지 확인 하 고 iis를 다시 시작한 후 다시 시도 하십시오.

또한 호스트 파일을 사용 하는 경우 올바르게 구성 되어 있는지 확인 합니다. 예를 들어 호스트 파일에는 프로젝트 형식에 따라 프로젝트 속성, **속성 > 웹 > 서버** 또는 **> 속성**에서와 같은 프로젝트 URL을 포함 해야 합니다.

## <a name="see_help"></a> 일반적인 구성 오류는 도움말을 참조하십시오. 디버거 외부에서 웹 페이지를 실행 하면 추가 정보가 제공 될 수 있습니다.

- 동일한 컴퓨터에서 Visual Studio와 웹 서버를 실행 하 고 있나요? 프로젝트 속성을 열고 프로젝트가 올바른 웹 서버에 연결 하도록 구성 되어 있는지 확인 하 고 URL을 시작 합니다. (프로젝트 형식에 따라 **디버그 >** **웹 > 서버** 또는 속성 >를 엽니다.

- 이 작업이 작동 하지 않거나 원격으로 디버깅 하는 경우에는 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)의 단계를 따르세요.

## <a name="operation_not_supported"></a>지원 되지 않는 작업입니다. 알 수 없는 오류: *오류 번호*

URL 다시 쓰기를 수행 하는 경우 URL을 다시 작성 하지 않고 기본 web.config를 테스트 합니다. [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)에서 URL 다시 쓰기 모듈에 대 한 **참고** 를 참조 하세요.

## <a name="vxtbshttpservererrorsthingstocheck"></a>IIS 구성 확인

여기에 설명 된 단계를 수행 하 여 문제를 해결 한 후 디버깅을 다시 시도 하기 전에 IIS를 다시 설정 해야 할 수도 있습니다. 관리자 권한 명령 프롬프트를 열고 `iisreset`를 입력 하 여이 작업을 수행할 수 있습니다.

* IIS 응용 프로그램 풀을 중지 한 후 다시 시작 하 고 다시 시도 하세요.

    응용 프로그램 풀이 오류로 인해 중지 되었을 수 있습니다. 또는 응용 프로그램 풀을 중지 하 고 다시 시작 해야 할 수도 있습니다.

    > [!NOTE]
    > 응용 프로그램 풀을 계속 중지 하는 경우 제어판에서 URL 재작성 모듈을 제거 해야 할 수 있습니다. 웹 플랫폼 설치 관리자 (WebPI)를 사용 하 여 다시 설치할 수 있습니다. 이 문제는 중요 한 시스템 업그레이드 후에 발생할 수 있습니다.

* 응용 프로그램 풀 구성을 확인 하 고 필요한 경우 수정한 후 다시 시도 하세요.

    Visual Studio 프로젝트와 일치 하지 않는 버전의 ASP.NET 응용 프로그램 풀을 구성할 수 있습니다. 응용 프로그램 풀에서 ASP.NET 버전을 업데이트 하 고 다시 시작 합니다. 자세한 내용은 [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)를 참조 하십시오.

    또한 암호 자격 증명이 변경 된 경우 응용 프로그램 풀 또는 웹 사이트에서 업데이트 해야 할 수 있습니다.  응용 프로그램 풀의 고급 설정에서 자격 증명을 업데이트 **> 모델 > id를 처리**합니다. 웹 사이트의 경우 **기본 설정 >** 자격 증명을 업데이트 합니다. 응용 프로그램 풀을 다시 시작 합니다.

* 웹 응용 프로그램 폴더에 올바른 권한이 있는지 확인 합니다.

    웹 응용 프로그램 폴더에 대 한 읽기 및 실행 권한과 [응용 프로그램 풀](/iis/manage/configuring-security/application-pool-identities) 에 연결 된 특정 사용자를 IIS_IUSRS, IUSR 또는 특정 사용자에 게 제공 해야 합니다. 문제를 해결 하 고 응용 프로그램 풀을 다시 시작 합니다.

* IIS에 올바른 버전의 ASP.NET가 설치 되어 있는지 확인 합니다.

    IIS 및 Visual Studio 프로젝트에서 ASP.NET 버전이 일치 하지 않으면이 문제가 발생할 수 있습니다. Web.config에서 프레임 워크 버전을 설정 해야 할 수도 있습니다. IIS에 ASP.NET를 설치 하려면 [WebPI (웹 플랫폼 설치 관리자)](https://www.microsoft.com/web/downloads/platform.aspx)를 사용 합니다. 또한 [ASP.NET 3.5 및 ASP.NET 4.5을 사용 하는 iis 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 ASP.NET Core의 경우 iis를 사용 하 여 [Windows에서 호스트](https://docs.asp.net/en/latest/publishing/iis.html)를 참조 하세요.

* IP 주소만 사용하는 경우의 인증 오류 해결

     기본적으로 IP 주소는 인터넷의 일부로 인식되는데 인터넷에서는 NTLM 인증을 수행할 수 없습니다. 웹 사이트가 인증을 요구 하도록 IIS에서 구성 된 경우이 인증에 실패 합니다. 이 문제를 해결 하기 위해 IP 주소 대신 원격 컴퓨터의 이름을 지정할 수 있습니다.

## <a name="other-causes"></a>기타 원인

IIS 구성으로 인해 문제가 발생 하지 않는 경우 다음 단계를 수행 합니다.

- 관리자 권한으로 Visual Studio를 다시 시작 하 고 다시 시도 하세요.

    웹 배포 사용과 같은 일부 ASP.NET 디버깅 시나리오에는 Visual Studio에 대 한 상승 된 권한이 필요 합니다.

- Visual Studio의 여러 인스턴스가 실행 중인 경우 Visual Studio의 한 인스턴스에서 프로젝트를 다시 열고 (관리자 권한 포함) 다시 시도 합니다.

- 로컬 주소가 있는 HOSTS 파일을 사용 하는 경우 컴퓨터의 IP 주소 대신 루프백 주소를 사용해 보세요.

    로컬 주소를 사용 하지 않는 경우에는 프로젝트 형식에 따라 프로젝트 속성, **속성 > 웹 > 서버** 또는 **> 속성**에서와 동일한 프로젝트 URL이 호스트 파일에 포함 되어 있는지 확인 합니다.

## <a name="more-troubleshooting-steps"></a>추가 문제 해결 단계

* 서버의 브라우저에서 localhost 페이지를 엽니다.

     IIS가 올바르게 설치되어 있지 않은 경우 브라우저에 `http://localhost` 를 입력하면 오류가 발생합니다.

     IIS에 배포 하는 방법에 대 한 자세한 내용은 [ASP.NET 3.5 and ASP.NET 4.5를 사용 하는 iis 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 및 ASP.NET Core의 경우 iis를 사용 하 [여 Windows에서 호스트](https://docs.asp.net/en/latest/publishing/iis.html)를 참조 하세요.

* 서버에 기본 ASP.NET 응용 프로그램을 만듭니다 (또는 기본 web.config 파일 사용).

    앱을 사용 하 여 디버거를 사용할 수 없는 경우에는 서버에서 로컬로 기본 ASP.NET 응용 프로그램을 만들고 기본 앱을 디버깅 해 보세요. (기본 ASP.NET MVC 템플릿을 사용 하는 것이 좋습니다.) 기본 앱을 디버그할 수 있는 경우 두 구성 간의 차이점을 식별 하는 데 도움이 될 수 있습니다. URL 재작성 규칙과 같은 web.config 파일의 설정에서 차이점을 찾습니다.

## <a name="see-also"></a>참조
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)