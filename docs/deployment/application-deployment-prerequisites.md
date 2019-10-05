---
title: 응용 프로그램 배포 필수 구성 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8206e199acc3ccb76cf89603d48bed0173129218
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746055"
---
# <a name="application-deployment-prerequisites"></a>애플리케이션 배포 필수 구성 요소

응용 프로그램을 설치 하 고 성공적으로 실행 하도록 먼저 응용 프로그램을 대상 컴퓨터에 종속 되어 있는 모든 구성 요소를 설치 합니다. 사용 하 여 생성 하는 예를 들어, 대부분의 응용 프로그램입니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework에 대 한 종속성입니다. 이 경우 응용 프로그램을 설치 하기 전에 올바른 버전의 공용 언어 런타임 대상 컴퓨터에 있는 이어야 합니다.

 이러한 필수 구성이 요소를 선택할 수 있습니다 합니다 **필수 조건 대화 상자** 설치의 일부로.NET Framework 및 모든 다른 재배포 가능 패키지를 설치 합니다. 이러한 방식을 *부트스트래핑*이라고 합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows 실행 프로그램을 생성 *Setup.exe*, 라고도 *부트스트래퍼*합니다. 부트스트래퍼는 애플리케이션을 실행하기 전에 이러한 필수 구성 요소를 설치합니다. 이러한 필수 구성이 요소를 선택 하는 방법에 대 한 자세한 내용은 참조 하세요. [필수 조건 대화 상자](../ide/reference/prerequisites-dialog-box.md)합니다.

 각 필수 구성 요소는 부트스트래퍼 패키지입니다. 부트스트래퍼 패키지는 필수 구성 요소를 설치 하는 방법을 설명 하는 매니페스트 파일을 포함 하는 파일과 디렉터리의 그룹입니다. 애플리케이션 필수 구성 요소가 **필수 구성 요소 대화 상자**에 나와 있지 않으면 사용자 지정 부트스트래퍼 패키지를 만들어 Visual Studio에 추가할 수 있습니다. 그런 다음, **필수 구성 요소 대화 상자**에서 해당 필수 구성 요소를 선택할 수 있습니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)합니다.

 부트스트래핑은 ClickOnce 배포에 기본적으로 사용됩니다. ClickOnce 배포용으로 생성된 부트스트래퍼는 서명되어 있습니다. 구성 요소의 부트스트랩 비활성화할 수 있지만 요소의 올바른 버전의 모든 대상 컴퓨터에 이미 설치 되어 있는 경우에 합니다.

## <a name="bootstrapping-and-clickonce-deployment"></a>부트스트래핑 및 ClickOnce 배포
 클라이언트 컴퓨터에 응용 프로그램을 설치 하기 전에 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 클라이언트 응용 프로그램 매니페스트에 지정 된 요구 사항이 있는지 검사 합니다. 여기에 다음 요구 사항을 포함 됩니다.

- 필요한 최소 버전의 공용 언어 런타임. 애플리케이션 매니페스트에서 어셈블리 종속성으로 지정합니다.

- 애플리케이션에 필요한 Windows 운영 체제의 최소 버전. `<osVersionInfo>` 요소를 사용하여 애플리케이션 매니페스트에서 지정합니다. (참조 [ \<종속성 > 요소](../deployment/dependency-element-clickonce-application.md).)

- 어셈블리 매니페스트에서 어셈블리 종속성 선언을 통해 지정 된 대로 전역 어셈블리 캐시 (GAC)에 미리 설치 해야 하는 모든 어셈블리의 최소 버전입니다.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 누락 된 필수 구성 요소를 검색할 수 있습니다 하 고 부트스트래퍼를 사용 하 여 필수 구성 요소를 설치할 수 있습니다. 자세한 내용은 [방법: ClickOnce 애플리케이션으로 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)를 참조하세요.

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 및 *MageUI.exe*와 같은 도구를 통해 생성된 매니페스트의 값을 변경하려면 텍스트 편집기에서 애플리케이션 매니페스트를 편집한 다음, 애플리케이션 및 배포 매니페스트를 모두 다시 서명해야 합니다. 자세한 내용은 [방법: 애플리케이션 및 배포 매니페스트 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조하세요.

 Visual Studio 및 ClickOnce를 사용하여 애플리케이션을 배포하는 경우 기본적으로 선택되는 부트스트래퍼 패키지는 솔루션의 .NET Framework 버전에 따라 달라집니다. 그러나 대상 .NET Framework 버전을 변경하는 경우에는 **필수 구성 요소 대화 상자**에서 옵션을 수동으로 업데이트해야 합니다.

|대상 .NET Framework|선택되는 부트스트래퍼 패키지|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포에서 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 게시 마법사를 통해 생성되는 *Publish.htm* 페이지는 애플리케이션만 설치하는 링크 또는 애플리케이션 및 부트스트래핑된 구성 요소를 모두 설치하는 링크를 가리킵니다.

 Visual Studio의 게시 페이지 또는 ClickOnce 게시 마법사를 사용하여 부트스트래퍼를 생성하면 *Setup.exe*가 자동으로 서명됩니다. 그러나 고객의 인증서를 사용하여 부트스트래퍼에 서명을 하려는 경우에는 나중에 이 파일에 서명할 수 있습니다.

## <a name="bootstrapping-and-msbuild"></a>부트스트래핑 및 MSBuild
 사용 하지 않는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 하지만 대신 명령줄에서 응용 프로그램을 컴파일, 만들 수 있습니다는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Microsoft Build Engine (MSBuild) 작업을 사용 하 여 응용 프로그램을 부트스트랩 합니다. 자세한 내용은 [GenerateBootstrapper 작업](../msbuild/generatebootstrapper-task.md)합니다.

 부트스트래핑을 수행하는 대신 Microsoft Systems Management Server(SMS) 등의 전자 소프트웨어 배포 시스템을 사용하여 구성 요소를 미리 배포할 수도 있습니다.

## <a name="bootstrapper-setupexe-command-line-arguments"></a>부트스트래퍼(Setup.exe) 명령줄 인수
 합니다 *Setup.exe* 에서 생성 된 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] MSBuild 작업을 다음 명령줄 인수 집합을 지원 합니다. 다른 모든 인수는 응용 프로그램 설치 관리자에 전달 됩니다.

 부트스트래퍼 옵션을 변경 하는 경우 서명 되지 않은 부트스트래퍼 변경한 다음 나중에 부트스트래퍼 파일에 서명 해야 합니다.

| 명령줄 인수 | 설명 |
| - | - |
| **-?, -h, -help** | 도움말 대화 상자를 표시합니다. |
| **-url, -componentsurl** | 이 설치를 위한 저장된 URL 및 구성 요소 URL을 표시합니다. |
| **-url=** `location` | *Setup.exe*가 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션을 찾을 URL을 설정합니다. |
| **-componentsurl=** `location` | URL을 설정 하는 *Setup.exe* 는.NET Framework와 같은 종속성을 찾습니다. |
| **-homesite=** `true` **&#124;** `false` | 때 `true`, 공급 업체의 사이트에서 기본 위치에서 종속성을 다운로드 합니다. 이 설정을 재정의 합니다 **-componentsurl** 설정 합니다. 때 `false`에 의해 지정 된 URL에서 종속성을 다운로드 **-componentsurl**합니다. |

## <a name="operating-system-support"></a>운영 체제 지원
 Visual Studio 부트스트래퍼 제한 된 기능을 사용 하 여 낮은 유지 관리 서버 환경을 제공 하므로 Windows Server 2008 Server Core 또는 Windows Server 2008 R2 Server Core에서 지원 되지 않습니다. 예를 들어 Server Core 설치 옵션을 전체.NET Framework에 종속 된 Visual Studio 기능을 실행할 수 없습니다는.NET Framework 3.5 Server Core 프로필을 지원 합니다.

## <a name="see-also"></a>참고자료
- [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)