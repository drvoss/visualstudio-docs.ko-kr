---
title: ASP.NET apps에 대해 디버깅 사용 | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911348"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio에서 ASP.NET 또는 ASP.NET Core apps 디버그

Visual Studio에서 ASP.NET 및 ASP.NET Core apps를 디버그할 수 있습니다. 프로세스는 ASP.NET와 ASP.NET Core 간에 다르며 IIS Express 또는 로컬 IIS 서버에서 실행 하는지 여부에 따라 다릅니다.

>[!NOTE]
>다음 단계와 설정은 로컬 서버에서 응용 프로그램을 디버깅 하는 경우에만 적용 됩니다. 원격 IIS 서버에서 앱을 디버깅 하면 **프로세스에 연결**을 사용 하 고이 설정을 무시 합니다. IIS의 원격 디버깅 ASP.NET 앱에 대 한 자세한 내용 및 지침은 원격 [iis 컴퓨터의](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)원격 디버그 [ASP.NET iis ASP.NET Core 컴퓨터](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 의 원격 디버그를 참조 하세요.

기본 제공 IIS Express 서버는 Visual Studio에 포함 되어 있습니다. IIS Express는 ASP.NET 및 ASP.NET Core 프로젝트에 대 한 기본 디버그 서버 이며 미리 구성 되어 있습니다. 디버깅 하는 가장 쉬운 방법 이며 초기 디버깅 및 테스트에 이상적입니다.

앱을 실행 하도록 구성 된 로컬 IIS 서버 (버전 8.0 이상)에서 ASP.NET 또는 ASP.NET Core 앱을 디버그할 수도 있습니다. 로컬 IIS에서 디버깅 하려면 다음 요구 사항을 충족 해야 합니다.

<a name="iis"></a>
- Visual Studio를 설치할 때 **개발 시간 IIS 지원** 을 선택 합니다. 필요한 경우 Visual Studio 설치 관리자를 다시 실행 하 고, **수정**을 선택 하 고,이 구성 요소를 추가 합니다.
- 관리자 권한으로 Visual Studio를 실행 하 고 있어야 합니다.
- ASP.NET 및/또는 ASP.NET Core의 적절 한 버전을 사용 하 여 IIS를 설치 하 고 올바르게 구성 합니다. 자세한 내용 및 지침에 대해서는 iis [8.0 ASP.NET 3.5 and ASP.NET 4.5를 사용 하는 iis](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 [Windows에서 호스트 ASP.NET Core](/aspnet/core/host-and-deploy/iis/index)를 참조 하세요.
- 앱이 오류 없이 IIS에서 실행 되는지 확인 합니다.

## <a name="debug-aspnet-apps"></a>ASP.NET 앱 디버그

IIS Express 기본값이 며 미리 구성 되어 있습니다. 로컬 IIS에서 디버깅 하는 경우 [로컬 iis 디버깅의 요구 사항을](#iis)충족 하는지 확인 합니다.

1. Visual Studio **솔루션 탐색기** 에서 ASP.NET 프로젝트를 선택 하 고 **속성** 아이콘을 클릭 한 다음 **Alt**+**enter**키를 누르거나 마우스 오른쪽 단추를 클릭 하 고 **속성**을 선택 합니다.

1. **웹** 탭을 선택 합니다.

1. **속성** 창의 **서버**에서
   - IIS Express의 경우 드롭다운에서 **IIS Express** 를 선택 합니다.
   - 로컬 IIS의 경우
     1. 드롭다운에서 **로컬 IIS** 를 선택 합니다.
     1. IIS에서 앱을 아직 설정 하지 않은 경우 **프로젝트 URL** 필드 옆에 있는 **가상 디렉터리 만들기**를 선택 합니다.

1. **디버거**아래에서 **ASP.NET**을 선택 합니다.

   ![ASP.NET 디버거 설정](media/dbg-aspnet-enable-debugging2.png "ASP.NET 디버거 설정")

1. **파일** > 사용 하 여 **선택한 항목을 저장** 하거나 **Ctrl**+**S** 를 사용 하 여 변경 내용을 저장 합니다.

1. 프로젝트에서 응용 프로그램을 디버그 하려면 일부 코드에서 중단점을 설정 합니다. Visual Studio 도구 모음에서 구성이 **디버그**로 설정 되어 있는지 확인 하 고 원하는 브라우저가 에뮬레이터 필드에 **IIS Express (\<browser 이름 >)** 또는 **로컬 IIS (\<브라우저 이름 >)** 에 표시 되는지 확인 합니다.

1. 디버깅을 시작 하려면 도구 모음에서 **IIS Express (\<browser 이름 >)** 또는 **로컬 IIS (\<브라우저 이름 >)** 를 선택 하 고 **디버그** 메뉴에서 **디버깅 시작** 을 선택 하거나 **F5**키를 누릅니다. 디버거가 중단점에서 일시 중지 됩니다. 디버거가 중단점에 도달할 수 없는 경우 [디버깅 문제 해결](#troubleshoot-debugging)을 참조 하세요.

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core 앱 디버그

IIS Express 기본값이 며 미리 구성 되어 있습니다. 로컬 IIS에서 디버깅 하는 경우 [로컬 iis 디버깅의 요구 사항을](#iis)충족 하는지 확인 합니다.

1. Visual Studio **솔루션 탐색기** 에서 ASP.NET Core 프로젝트를 선택 하 고 **속성** 아이콘을 클릭 하거나 **Alt**+**enter**키를 누르거나 마우스 오른쪽 단추를 클릭 하 고 **속성**을 선택 합니다.

1. **디버그** 탭을 선택합니다.

1. **속성** 창의 **프로필**옆에서
   - IIS Express의 경우 드롭다운에서 **IIS Express** 를 선택 합니다.
   - 로컬 IIS의 경우 드롭다운에서 앱 이름을 선택 하거나 **새로**만들기를 선택 하 고 새 프로필 이름을 만든 다음 **확인**을 선택 합니다.

1. **시작**옆의 드롭다운에서 **IIS Express** 또는 **IIS** 를 선택 합니다.

1. **브라우저 시작** 이 선택 되어 있는지 확인 합니다.

1. **환경 변수**에서 **ASPNETCORE_ENVIRONMENT** 이 **Development**값과 함께 제공 되는지 확인 합니다. 그렇지 않은 경우 **추가** 를 선택 하 고 추가를 선택 합니다.

   ![ASP.NET Core 디버거 설정](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core 디버거 설정")

1. **파일** > 사용 하 여 **선택한 항목을 저장** 하거나 **Ctrl**+**S** 를 사용 하 여 변경 내용을 저장 합니다.

1. 프로젝트에서 응용 프로그램을 디버그 하려면 일부 코드에서 중단점을 설정 합니다. Visual Studio 도구 모음에서 구성이 **디버그**로 설정 되어 있고 **IIS EXPRESS**또는 새 IIS 프로필 이름이 에뮬레이터 필드에 표시 되는지 확인 합니다.

1. 디버깅을 시작 하려면 도구 모음에서 **IIS Express** 또는 **\<IIS 프로필 이름 >** 을 선택 하 고 **디버그** 메뉴에서 **디버깅 시작** 을 선택 하거나 **F5**키를 누릅니다. 디버거가 중단점에서 일시 중지 됩니다. 디버거가 중단점에 도달할 수 없는 경우 [디버깅 문제 해결](#troubleshoot-debugging)을 참조 하세요.

## <a name="troubleshoot-debugging"></a>디버깅 문제 해결

로컬 IIS 디버깅에서 중단점을 진행할 수 없는 경우 다음 단계에 따라 문제를 해결 합니다.

1. IIS에서 웹 앱을 시작 하 고 올바르게 실행 되는지 확인 합니다. 웹 앱을 실행 상태로 둡니다.

2. Visual Studio에서 **디버그 > 프로세스에 연결** 을 선택 하거나 **ctrl**+**alt**+**P**를 누르고 ASP.NET 또는 ASP.NET Core 프로세스 **(일반적으로** w3wp.exe 또는 **dotnet**)에 연결 합니다. 자세한 내용은 [프로세스에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md) 및 [ASP.NET 프로세스의 이름을 찾는 방법](how-to-find-the-name-of-the-aspnet-process.md)을 참조 하세요.

**프로세스에**연결을 사용 하 여 중단점에 연결 하 고 **디버그** > **디버깅** 또는 **F5 키**를 사용 하 여 중단점을 적중 하는 경우 프로젝트 속성에서 설정이 잘못 된 것일 수 있습니다. HOSTS 파일을 사용 하는 경우에도 올바르게 구성 되었는지 확인 합니다.

## <a name="configure-debugging-in-the-webconfig-file"></a>Web.config 파일에서 디버깅 구성

ASP.NET 프로젝트에는 기본적으로 *web.config* 파일이 있습니다 .이 파일에는 응용 프로그램 구성 및 시작 정보 (디버그 설정 포함)가 모두 포함 되어 있습니다. 디버깅을 위해 web.config 파일을 올바르게 구성 *해야 합니다.* 이전 섹션의 **속성** 설정은 *web.config* 파일을 업데이트 하지만 수동으로 구성할 수도 있습니다.

> [!NOTE]
> ASP.NET Core 프로젝트는 처음에 *web.config* 파일을 포함 하지 않지만 응용 프로그램 구성 및 시작 정보에 대해 *Appsettings* 및 *launchsettings. json* 파일을 사용 합니다. 앱을 배포 하면 프로젝트에 *web.config 파일이 생성* 되지만 일반적으로 디버그 정보는 포함 되지 않습니다.

> [!TIP]
> 배포 *프로세스에서 web.config 설정을 업데이트할* 수 있으므로 디버깅을 시도 하기 전에 web.config가 디버깅을 위해 *구성 되었는지 확인* 해야 합니다.

**디버깅을 위해 web.config *파일을* 수동으로 구성 하려면 다음을 수행 합니다.**

1. Visual Studio에서 ASP.NET 프로젝트의 *web.config* 파일을 엽니다.

2. *Web.config는 XML* 파일 이므로 태그로 표시 된 중첩 된 섹션을 포함 합니다. `configuration/system.web/compilation` 섹션을 찾습니다. `compilation` 요소가 존재 하지 않는 경우 만듭니다.

3. `compilation` 요소의 `debug` 특성이 `true`으로 설정 되어 있는지 확인 합니다. `compilation` 요소가 `debug` 특성을 포함 하지 않는 경우이를 추가 하 고 `true`으로 설정 합니다.

   기본 IIS Express 서버 대신 로컬 IIS를 사용 하는 경우 `compilation` 요소의 `targetFramework` 특성 값이 IIS 서버의 프레임 워크와 일치 하는지 확인 합니다.

   *Web.config 파일의* `compilation` 요소는 다음 예제와 같습니다.

   > [!NOTE]
   > 이 예제는 *web.config* 파일의 일부입니다. 일반적으로 `configuration` 및 `system.web` 요소에 추가 XML 섹션이 있고 `compilation` 요소에는 다른 특성 및 요소가 포함 될 수도 있습니다.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]가 *web.config* 파일의 변경 내용을 자동으로 검색하고 새 구성 설정을 적용합니다. 변경 내용을 적용 하려면 컴퓨터를 다시 시작 하거나 IIS 서버를 다시 시작 하지 않아도 됩니다.

*웹* 사이트에는 여러 개의 가상 디렉터리 및 하위 디렉터리가 포함 될 수 있으며 각 디렉터리에 web.config 파일이 있습니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] apps는 URL 경로의 상위 수준에 있는 *web.config* 파일의 구성 설정을 상속 합니다. 계층 구조 *web.config* 파일 설정은 계층 구조에서 아래의 모든 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 앱에 적용 됩니다. 계층 구조에서 더 낮은 web.config *파일에* 다른 구성을 설정 하면 상위 파일의 설정이 재정의 됩니다.

예를 들어 <em>www.microsoft.com/aaa/web.config</em>에서 `debug="true"` 지정 하는 경우 *aaa* 폴더 또는 *aaa* 의 모든 하위 폴더에 있는 모든 앱이 해당 설정을 상속 합니다. 단, 해당 앱 중 하나가 해당 web.config를 사용 하 여 설정을 재정의 하는 경우는 예외입니다 *.* 파일과.

## <a name="publish-in-debug-mode-using-the-file-system"></a>파일 시스템을 사용 하 여 디버그 모드로 게시

앱을 IIS에 게시 하는 방법에는 여러 가지가 있습니다. 이러한 단계에서는 파일 시스템을 사용 하 여 디버그 게시 프로필을 만들고 배포 하는 방법을 보여 줍니다. 이렇게 하려면 관리자 권한으로 Visual Studio를 실행 해야 합니다.

> [!IMPORTANT]
> 코드를 변경 하거나 다시 작성 하는 경우 이러한 단계를 반복 하 여 다시 게시 해야 합니다.

1. Visual Studio에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **게시**를 선택 합니다.

3. **IIS, FTP** 등을 선택 하 고 **게시**를 클릭 합니다.

    ![IIS에 게시](media/dbg-aspnet-local-iis.png "IIS에 게시")

4. **Customprofile** 대화 상자에서 **게시 방법**으로 **파일 시스템**을 선택 합니다.

5. **대상 위치**에서 **찾아보기** ( **...** )를 선택 합니다.

   - ASP.NET에 대해 **로컬 IIS**를 선택 하 고 앱에 대해 만든 웹 사이트를 선택한 다음 **열기**를 선택 합니다.

     ![ASP.NET에 IIS에 게시](media/dbg-aspnet-local-iis1.png "IIS에 ASP.NET 게시")

   - ASP.NET Core에서 **파일 시스템**을 선택 하 고 앱에 대해 설정한 폴더를 선택한 후 **열기**를 선택 합니다.

1. **새로 만들기**를 선택합니다.

1. **구성**아래의 드롭다운에서 **디버그** 를 선택 합니다.

1. **저장**을 선택합니다.

1. **게시** 대화 상자에서 **customprofile** (또는 방금 만든 프로필의 이름)이 표시 되는지 확인 하 고 **LastUsedBuildConfiguration** 이 **디버그**로 설정 되어 있는지 확인 합니다.

1. **게시**를 선택합니다.

    ![IIS에 게시](media/dbg-aspnet-local-iis-select-site.png "IIS에 게시")

> [!IMPORTANT]
> 디버그 모드는 앱의 성능을 크게 줄입니다. 최상의 성능을 위해 *web.config* 에서 `debug="false"`를 설정 하 고 프로덕션 앱을 배포 하거나 성능 측정을 수행할 때 릴리스 빌드를 지정 합니다.

## <a name="see-also"></a>참조
- [ASP.NET 디버깅: 시스템 요구 사항](aspnet-debugging-system-requirements.md)
- [방법: 사용자 계정으로 작업자 프로세스 실행](how-to-run-the-worker-process-under-a-user-account.md)
- [방법: ASP.NET 프로세스의 이름 찾기](how-to-find-the-name-of-the-aspnet-process.md)
- [배포된 웹 애플리케이션 디버그](debugging-deployed-web-applications.md)
- [연습: Web Form 디버그](walkthrough-debugging-a-web-form.md)
- [방법: ASP.NET 예외 디버그](how-to-debug-aspnet-exceptions.md)
- [웹 애플리케이션 디버그: 오류 및 문제 해결](debugging-web-applications-errors-and-troubleshooting.md)
