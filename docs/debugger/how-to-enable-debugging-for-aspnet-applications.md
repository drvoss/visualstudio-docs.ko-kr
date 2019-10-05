---
title: ASP.NET 앱에 대 한 디버깅을 사용 하도록 설정 | Microsoft Docs
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
ms.openlocfilehash: d383c559e605392b01ba2c476fd4ed5ae5d48625
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848335"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio에서 ASP.NET 또는 ASP.NET Core 앱 디버그

Visual Studio에서 ASP.NET 및 ASP.NET Core 앱을 디버그할 수 있습니다. ASP.NET 및 ASP.NET Core 중 다른 프로세스 실행 하는지 여부 및이 IIS Express 또는 로컬 IIS 서버에서.

>[!NOTE]
>다음 단계 및 설정을 로컬 서버에서 앱 디버깅에 적용 됩니다. 서버에서는 원격 IIS에서 앱을 디버그할 **프로세스에 연결**, 이러한 설정을 무시 합니다. 자세한 내용 및 IIS에서 원격 디버깅 ASP.NET 앱에 대 한 지침을 참조 하세요 [IIS 컴퓨터의 원격 디버그 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 하거나 [원격 디버그 ASP.NET Core 원격 IIS 컴퓨터](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)합니다.

기본 제공 IIS Express 서버 Visual Studio를 사용 하 여 포함 되어 있습니다. IIS Express는 ASP.NET 및 ASP.NET Core 프로젝트에 대 한 기본 디버그 서버 및 미리 구성 합니다. 디버그 초기 디버깅 및 테스트에 적합 하기 가장 쉬운 방법입니다.

또한 앱을 실행 하도록 구성 된 로컬 IIS 서버 (버전 8.0 이상)에서 ASP.NET 또는 ASP.NET Core 앱을 디버그할 수 있습니다. 로컬 IIS를 디버깅 하려면 다음 요구 사항을 충족 해야 합니다.

<a name="iis"></a>
- 선택 **개발 시간 IIS 지원** Visual Studio를 설치 하는 경우. (필요한 경우 Visual Studio 설치 관리자를 다시 실행을 선택 합니다 **수정**,이 구성 요소를 추가 합니다.)
- 관리자 권한으로 Visual Studio를 실행 합니다.
- 설치 하 고 올바르게 ASP.NET 및/또는 ASP.NET Core의 적절 한 버전을 사용 하 여 IIS를 구성 합니다. 자세한 내용 및 지침을 참조 하세요 [IIS 8.0를 사용 하 여 ASP.NET 3.5 및 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 하거나 [IIS 사용 하 여 Windows에서 ASP.NET Core 호스팅](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index)합니다.
- 앱이 IIS에서 오류 없이 실행 해야 합니다.

## <a name="debug-aspnet-apps"></a>ASP.NET 앱 디버그

IIS Express가 기본값 및 미리 구성 합니다. 로컬 IIS에서 디버깅 하는 경우 충족 하는지 확인 합니다 [로컬 IIS 디버깅에 대 한 요구 사항](#iis)합니다.

1. Visual Studio에서 ASP.NET 프로젝트를 선택 **솔루션 탐색기** 을 클릭 합니다 **속성** 아이콘을 눌러 **Alt**+**Enter**를 마우스 오른쪽 단추로 클릭 하 고 선택 하거나 **속성**합니다.

1. 선택 된 **웹** 탭 합니다.

1. 에 **속성** 창 아래에 있는 **서버**,
   - IIS express의 경우 선택 **IIS Express** 드롭다운 목록에서.
   - 로컬 IIS에 대 한
     1. 선택 **로컬 IIS** 드롭다운 목록에서.
     1. 다음에 **프로젝트 URL** 필드를 선택한 **가상 디렉터리 만들기**IIS에서 앱을 아직 설정 하지 않은 경우.

1. 아래 **디버거**를 선택 **ASP.NET**합니다.

   ![ASP.NET 디버거 설정을](media/dbg-aspnet-enable-debugging2.png "ASP.NET 디버거 설정")

1. 사용 하 여 **파일** > **선택한 항목 저장** 하거나 **Ctrl**+**S** 모든 변경 내용을 저장 합니다.

1. 프로젝트에서 앱을 디버깅 하려면 코드에서 중단점을 설정 합니다. Visual Studio 도구 모음에서 구성 설정 되어 있는지 확인 **디버그**, 원하는 브라우저에 표시 됩니다 **IIS Express (\<브라우저 이름 >)** 또는 **(로컬IIS\< 브라우저 이름 >)** 에뮬레이터 필드에서입니다.

1. 디버깅을 시작 하려면 선택 **IIS Express (\<브라우저 이름 >)** 하거나 **로컬 IIS (\<브라우저 이름 >)** 도구 모음에서 선택 **디버깅시작**에서 **디버그** 메뉴 또는 키를 누릅니다 **F5**합니다. 디버거는 중단점에서 일시 중지합니다. 디버거는 중단점을 적중할 수 없습니다, 하는 경우 참조 [문제 해결 디버깅](#troubleshoot-debugging)합니다.

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core 앱 디버그

IIS Express가 기본값 및 미리 구성 합니다. 로컬 IIS에서 디버깅 하는 경우 충족 하는지 확인 합니다 [로컬 IIS 디버깅에 대 한 요구 사항](#iis)합니다.

1. Visual Studio에서 ASP.NET Core 프로젝트를 선택 **솔루션 탐색기** 을 클릭 합니다 **속성** 아이콘을 눌러 **Alt**+**Enter**를 마우스 오른쪽 단추로 클릭 하 고 선택 하거나 **속성**합니다.

1. **디버그** 탭을 선택합니다.

1. 에 **속성** 창에서 다음을 **프로필**,
   - IIS express의 경우 선택 **IIS Express** 드롭다운 목록에서.
   - 로컬 IIS에 대 한 드롭다운 목록에서 앱 이름을 선택 하거나 선택 **새로 만들기**새 프로필 이름을 만들고 선택 **확인**합니다.

1. 옆에 **시작**, 선택 **IIS Express** 하거나 **IIS** 드롭다운 목록에서.

1. 했는지 **브라우저 실행** 을 선택 합니다.

1. 아래 **환경 변수**, 했는지 **ASPNETCORE_ENVIRONMENT** 값이 있으면 **개발**합니다. 그렇지 않은 경우 **추가** 추가 합니다.

   ![ASP.NET Core 디버거 설정](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core 디버거 설정")

1. 사용 하 여 **파일** > **선택한 항목 저장** 하거나 **Ctrl**+**S** 모든 변경 내용을 저장 합니다.

1. 프로젝트에서 앱을 디버깅 하려면 코드에서 중단점을 설정 합니다. Visual Studio 도구 모음에서 구성 설정 되어 있는지 확인 **디버그**, 및 **IIS Express**, 에뮬레이터 필드에 새 IIS 프로필 이름을 표시 합니다.

1. 디버깅을 시작 하려면 선택 **IIS Express** 하거나  **\<IIS 프로필 이름 >** 도구 모음에서 선택 **디버깅 시작** 에서 **디버그** 메뉴나 press **F5**합니다. 디버거는 중단점에서 일시 중지합니다. 디버거는 중단점을 적중할 수 없습니다, 하는 경우 참조 [문제 해결 디버깅](#troubleshoot-debugging)합니다.

## <a name="troubleshoot-debugging"></a>디버깅 문제 해결

로컬 IIS 디버깅 중단점을 진행할 수 없습니다, 하는 경우 문제를 해결 하려면 다음이 단계를 수행 합니다.

1. IIS에서 웹 앱을 시작 하 고 올바르게 실행 되는지 확인 합니다. 웹 앱을 실행 중인 상태로 둡니다.

2. Visual Studio에서 선택 **디버그 > 프로세스에 연결** 누르거나 **Ctrl**+**Alt**+**P**, 및 ASP.NET 또는 ASP.NET Core 프로세스에 연결 (일반적으로 **w3wp.exe** 하거나 **dotnet.exe**). 자세한 내용은 [프로세스에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md) 하 고 [ASP.NET 프로세스의 이름을 찾는 방법](how-to-find-the-name-of-the-aspnet-process.md)합니다.

연결 하 고 사용 하 여 중단점을 적중 수 있는지 **프로세스에 연결**에서 아닌 **디버그** > **디버깅 시작** 또는 **F5**, 설정이 프로젝트 속성에서 아마도 올바르지 않습니다. 호스트 파일을 사용 하는 경우에이 제대로 구성 되어 있는지 확인 합니다.

## <a name="configure-debugging-in-the-webconfig-file"></a>Web.config 파일에서 디버깅 구성

ASP.NET 프로젝트 *web.config* 기본적으로 정보가 포함 된 파일 모두 앱 구성 및 실행, 디버그 설정을 포함 합니다. 합니다 *web.config* 디버깅에 대 한 파일을 올바르게 구성 되어야 합니다. **속성** 설정 섹션의 이전 업데이트에는 *web.config* 파일인 있지만 수동으로 구성할 수 있습니다 하 합니다.

> [!NOTE]
> ASP.NET Core 프로젝트를 처음에 있지 않은 *web.config* 파일을 사용 하 여 *appsettings.json* 하 고 *launchSettings.json* 앱 구성 및 시작에 대 한 파일 정보입니다. 앱 배포를 만듭니다는 *web.config* 파일 또는 프로젝트의 파일 되지만 디버그 정보를 일반적으로 포함 되지 않습니다.

> [!TIP]
> 배포 프로세스를 업데이트할 수 있습니다는 *web.config* 설정 하므로 디버그 하기 전에 해야 합니다 *web.config* 디버깅을 위해 구성 됩니다.

**수동으로 구성 하는 *web.config* 디버깅에 대 한 파일:**

1. Visual Studio에서 ASP.NET 프로젝트를 엽니다 *web.config* 파일입니다.

2. *Web.config* 은 XML 파일, 따라서 태그로 표시 하는 중첩 된 섹션이 포함 되어 있습니다. `configuration/system.web/compilation` 섹션을 찾습니다. (경우는 `compilation` 만들가 존재 하지 않는 요소입니다.)

3. 있는지 확인 합니다 `debug` 특성을 `compilation` 로 설정 된 `true`. (경우 합니다 `compilation` 요소를 포함 하지 않습니다는 `debug` 특성, 추가 및로 설정 `true`.)

   로컬 IIS 기본 IIS Express 서버 대신를 사용 하는 경우 확인 합니다 `targetFramework` 특성 값에는 `compilation` IIS 서버에서 프레임 워크를 일치 하는 요소가 합니다.

   `compilation` 의 요소를 *web.config* 파일은 다음과 같이 표시 합니다.

   > [!NOTE]
   > 이 예제는 부분 *web.config* 파일입니다. 일반적으로 추가 XML 섹션은는 `configuration` 하 고 `system.web` 요소 및 `compilation` 특성 및 요소가 다른 요소를 포함할 수도 있습니다.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]가 *web.config* 파일의 변경 내용을 자동으로 검색하고 새 구성 설정을 적용합니다. 컴퓨터나 변경 내용을 적용 하려면 IIS 서버를 다시 시작할 필요가 없습니다.

웹 사이트를 사용 하 여 여러 가상 디렉터리 및 하위 디렉터리를 포함할 수 있습니다 *web.config* 각각에서 파일입니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 앱 구성 설정을 상속할 *web.config* 파일 URL 경로의 상위 수준에 있습니다. 계층적 *web.config* 파일 설정은 모든 적용 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 그 아래의 계층 구조에서 앱. 다른 구성에서 설정 된 *web.config* 계층 구조의 하위 파일은 더 높은 파일의 설정을 재정의 합니다.

예를 들어 지정 하는 경우 `debug="true"` 에 <em>www.microsoft.com/aaa/web.config</em>, 모든 앱에는 *aaa* 폴더 또는 하위 폴더에 *aaa* 해당 설정을 상속 이러한 앱 중 하나를 고유한 설정을 재정의 하는 경우를 제외 하 고 *web.config* 파일입니다.

## <a name="publish-in-debug-mode-using-the-file-system"></a>파일 시스템을 사용 하 여 디버그 모드에서 게시

IIS에 앱을 게시 하는 방법은 여러 가지입니다. 이러한 단계에는 만들고 디버그 파일 시스템을 사용 하 여 게시 프로필을 배포 하는 방법을 보여 줍니다. 이 위해 실행 해야 Visual Studio를 관리자 권한으로 합니다.

> [!IMPORTANT]
> 프로그램 코드 또는 다시 작성을 변경한 경우에 다시 게시 하려면 다음이 단계를 반복 해야 합니다.

1. Visual Studio에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **게시**합니다.

3. 선택할 **IIS, FTP 등** 클릭 **게시**합니다.

    ![IIS에 게시](media/dbg-aspnet-local-iis.png "IIS에 게시")

4. 에 **CustomProfile** 대화 상자에서에 대 한 **메서드를 게시**, 선택 **파일 시스템**입니다.

5. 에 대 한 **대상 위치**를 선택 **찾아보기** (**...** ).

   - ASP.NET에 대 한 선택 **로컬 IIS**, 앱에 대해 만든 웹 사이트를 선택 하 고 선택한 **오픈**합니다.

     ![IIS에 ASP.NET 게시할](media/dbg-aspnet-local-iis1.png "ASP.NET을 IIS에 게시")

   - ASP.NET Core에 대 한 선택 **파일 시스템**를 앱에 대 한 설정 하 고 선택한 폴더를 선택 **오픈**합니다.

1. **새로 만들기**를 선택합니다.

1. 아래 **Configuration**를 선택 **디버그** 드롭다운 목록에서.

1. **저장**을 선택합니다.

1. 에 **게시** 대화 상자에서 있는지 **CustomProfile** (또는 방금 만든 프로필의 이름) 표시 및 **LastUsedBuildConfiguration** 로 설정 되어  **디버그**합니다.

1. **게시**를 선택합니다.

    ![IIS에 게시](media/dbg-aspnet-local-iis-select-site.png "IIS에 게시")

> [!IMPORTANT]
> 디버그 모드에는 앱의 성능을 크게 줄여 줍니다. 최상의 성능을 위해 설정 `debug="false"` 에 *web.config* 프로덕션 앱을 배포 하거나 성능을 측정 하는 경우에 릴리스 빌드를 지정 합니다.

## <a name="see-also"></a>참고자료
- [ASP.NET 디버깅: 시스템 요구 사항](aspnet-debugging-system-requirements.md)
- [방법: 사용자 계정으로 작업자 프로세스 실행](how-to-run-the-worker-process-under-a-user-account.md)
- [방법: ASP.NET 프로세스의 이름 찾기](how-to-find-the-name-of-the-aspnet-process.md)
- [배포된 웹 애플리케이션 디버그](debugging-deployed-web-applications.md)
- [연습: Web form 디버깅](walkthrough-debugging-a-web-form.md)
- [방법: ASP.NET 예외 디버그](how-to-debug-aspnet-exceptions.md)
- [웹 애플리케이션 디버그: 오류 및 문제 해결](debugging-web-applications-errors-and-troubleshooting.md)
