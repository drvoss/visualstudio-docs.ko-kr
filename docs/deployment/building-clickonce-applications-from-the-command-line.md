---
title: 명령줄에서 ClickOnce 응용 프로그램 빌드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797207"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>명령줄에서 ClickOnce 애플리케이션 빌드
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]IDE (통합 개발 환경)에서 생성 된 경우에도 명령줄에서 프로젝트를 빌드할 수 있습니다. 실제로 .NET Framework만 설치 된 다른 컴퓨터에 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]를 사용 하 여 만든 프로젝트를 다시 빌드할 수 있습니다. 따라서 자동화 된 프로세스를 사용 하 여 빌드를 재현할 수 있습니다. 예를 들어 중앙 빌드 랩에서 또는 프로젝트 자체 빌드 범위를 벗어나는 고급 스크립팅 기술을 사용할 수 있습니다.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>MSBuild를 사용 하 여 ClickOnce 응용 프로그램 배포 재현
 명령줄에서 msbuild/target: publish를 호출 하면 MSBuild 시스템에서 프로젝트를 빌드하고 publish 폴더에 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 만들도록 지시 합니다. 이는 IDE에서 **게시** 명령을 선택 하는 것과 같습니다.

 이 명령은 Visual Studio 명령 프롬프트 환경의 경로에 있는 *msbuild.exe*를 실행 합니다.

 "대상"은 명령을 처리 하는 방법에 대 한 MSBuild에 대 한 표시기입니다. 키 대상은 "빌드" 대상과 "게시" 대상입니다. 빌드 대상은 IDE에서 빌드 명령을 선택 하거나 F5 키를 누르는 것과 같습니다. 프로젝트를 빌드 하려는 경우 `msbuild`를 입력 하 여이를 달성할 수 있습니다. 빌드 대상이 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]에서 생성 된 모든 프로젝트의 기본 대상이 기 때문에이 명령이 작동 합니다. 즉, 빌드 대상을 명시적으로 지정할 필요가 없습니다. 따라서 `msbuild`를 입력 하면 `msbuild /target:build`입력 하는 것과 동일한 작업이 수행 됩니다.

 `/target:publish` 명령은 MSBuild에 게시 대상을 호출 하도록 지시 합니다. 게시 대상은 빌드 대상에 따라 다릅니다. 즉, 게시 작업은 빌드 작업의 상위 집합입니다. 예를 들어 Visual Basic 또는 C# 소스 파일 중 하나를 변경한 경우 게시 작업을 통해 해당 어셈블리가 자동으로 다시 작성 됩니다.

 Mage.exe 명령줄 도구를 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 매니페스트를 만드는 전체 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포를 생성 하는 방법에 대 한 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요.

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>MSBuild를 사용 하 여 기본 ClickOnce 응용 프로그램 만들기 및 빌드

#### <a name="to-create-and-publish-a-clickonce-project"></a>ClickOnce 프로젝트를 만들고 게시 하려면

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

    **Windows 데스크톱 응용 프로그램** 프로젝트 템플릿을 선택 하 고 프로젝트의 이름을 `CmdLineDemo`합니다.

1. **빌드** 메뉴에서 **게시** 명령을 클릭 합니다.

    이 단계에서는 프로젝트가 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 배포를 만들도록 적절히 구성 되어 있는지 확인 합니다.

    게시 마법사가 나타납니다.

1. 게시 마법사에서 **마침**을 클릭 합니다.

    Visual Studio에서 *게시*라는 기본 웹 페이지를 생성 하 고 표시 합니다.

1. 프로젝트를 저장 하 고 저장 된 폴더 위치를 기록해 둡니다.

   위의 단계는 처음 게시 된 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 프로젝트를 만듭니다. 이제 IDE 외부에서 빌드를 재현할 수 있습니다.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>명령줄에서 빌드를 재현 하려면

1. [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]을 종료합니다.

2. Windows **시작** 메뉴에서 **모든 프로그램**을 클릭 하 고 **Microsoft Visual Studio**한 다음 **Visual Studio Tools**하 고 **Visual Studio 명령 프롬프트**를 클릭 합니다. 그러면 현재 사용자의 루트 폴더에서 명령 프롬프트가 열립니다.

3. **Visual Studio 명령 프롬프트**에서 방금 만든 프로젝트의 위치로 현재 디렉터리를 변경 합니다. 예를 들어 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`을 입력합니다.

4. "[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 프로젝트를 만들고 게시 하려면"에 생성 된 기존 파일을 제거 하려면 `rmdir /s publish`입력 합니다.

    이 단계는 선택 사항 이지만, 명령줄 빌드에서 새 파일이 모두 생성 되었는지 확인 합니다.

5. `msbuild /target:publish`을 입력합니다.

   위의 단계는 **Publish**라는 프로젝트의 하위 폴더에 전체 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 배포를 생성 합니다. *Cmdlinedemo. 응용 프로그램이* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포 매니페스트입니다. *0.0.0 CmdLineDemo_1* 폴더에는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트 파일 ( *cmdlinedemo .Exe* 및 *cmdlinedemo. .manifest*)이 포함 되어 있습니다. Setup.exe는 기본적으로 .NET Framework를 설치 하도록 구성 된 *부트스트래퍼입니다.* Dotnetfx.exe 폴더는 .NET Framework에 대 한 재배포 가능 패키지를 포함 합니다. 웹을 통해 또는 UNC 또는 CD/DVD를 통해 응용 프로그램을 배포 하는 데 필요한 전체 파일 집합입니다.
   
> [!NOTE]
> MSBuild 시스템은 출력 위치 (예: `msbuild /t:publish /p:PublishDir="<specific location>"`)를 지정 **하는 데이 옵션을** 사용 합니다.

## <a name="publish-properties"></a>속성 게시
 위의 절차에서 응용 프로그램을 게시 하면 게시 마법사에서 다음 속성이 프로젝트 파일에 삽입 됩니다. 이러한 속성은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 생성 하는 방법에 직접적인 영향을 줍니다.

 *CmdLineDemo.vbproj* / *CmdLineDemo.csproj*에서:

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 이러한 속성은 프로젝트 파일 자체를 변경 하지 않고 명령줄에서 재정의할 수 있습니다. 예를 들어 다음은 부트스트래퍼가 없는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 배포를 빌드합니다.

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 게시 속성은 **프로젝트 디자이너**의 **게시**, **보안**및 **서명** 속성 페이지에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 의해 제어 됩니다. 다음은 응용 프로그램 디자이너의 다양 한 속성 페이지에서 각을 설정 하는 방법에 대 한 설명과 함께 게시 속성에 대 한 설명입니다.

- `AssemblyOriginatorKeyFile` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트에 서명 하는 데 사용 되는 키 파일을 결정 합니다. 이 동일한 키를 사용 하 여 어셈블리에 강력한 이름을 할당할 수도 있습니다. 이 속성은 **프로젝트 디자이너**의 **서명** 페이지에서 설정 합니다.

  **보안** 페이지에 설정 되는 속성은 다음과 같습니다.

- **ClickOnce 보안 설정 사용** [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 매니페스트가 생성 되는지 여부를 결정 합니다. 프로젝트를 처음 만들 때 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 매니페스트 생성은 기본적으로 해제 되어 있습니다. 처음으로 게시 하는 경우 마법사가이 플래그를 자동으로 설정 합니다.

- **Targetzone** [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트로 내보낼 신뢰 수준을 결정 합니다. 가능한 값은 "Internet", "LocalIntranet" 및 "Custom"입니다. 인터넷 및 LocalIntranet를 사용 하면 기본 권한 집합이 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트로 내보내집니다. LocalIntranet은 기본값이 며, 기본적으로 완전 신뢰를 의미 합니다. 사용자 지정은 기본 응용 프로그램 *매니페스트* 파일에 명시적으로 지정 된 권한만 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트로 내보내도록 지정 합니다. *응용 프로그램 매니페스트* 파일은 신뢰 정보 정의만 포함 하는 부분 매니페스트 파일입니다. 이 파일은 **보안** 페이지에서 권한을 구성할 때 프로젝트에 자동으로 추가 되는 숨겨진 파일입니다.

  **게시** 페이지에 설정 된 속성은 다음과 같습니다.

- `PublishUrl`은 IDE에서 응용 프로그램이 게시 되는 위치입니다. `InstallUrl` 또는 `UpdateUrl` 속성이 지정 되지 않은 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트에 삽입 됩니다.

- `ApplicationVersion` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램의 버전을 지정 합니다. 이는 네 자리 버전 번호입니다. 마지막 자릿수가 "*" 인 경우 `ApplicationRevision`는 빌드 시 매니페스트에 삽입 된 값을 대체 합니다.

- 수정 버전을 지정 하 `ApplicationRevision`입니다. IDE에 게시할 때마다 증가 하는 정수입니다. 명령줄에서 수행 되는 빌드에 대해 자동으로 증가 하지 않습니다.

- `Install`는 응용 프로그램이 설치 된 응용 프로그램 인지 아니면 웹에서 실행 되는 응용 프로그램 인지를 결정 합니다.

- `InstallUrl` (표시 되지 않음)는 사용자가 응용 프로그램을 설치 하는 위치입니다. 이 값을 지정 하면 `IsWebBootstrapper` 속성이 설정 된 경우이 값을 *setup.exe* 부트스트래퍼에 구워야 합니다. `UpdateUrl` 지정 되지 않은 경우에도 응용 프로그램 매니페스트에 삽입 됩니다.

- `SupportUrl` (not shown) is the location linked in the **Add/Remove Programs** dialog box for an installed application.

  The following properties are set in the **Application Updates** dialog box, accessed from the **Publish** page.

- `UpdateEnabled` indicates whether the application should check for updates.

- `UpdateMode` specifies either Foreground updates or Background updates.

- `UpdateInterval` specifies how frequently the application should check for updates.

- `UpdateIntervalUnits` specifies whether the `UpdateInterval` value is in units of hours, days, or weeks.

- `UpdateUrl` (not shown) is the location from which the application will receive updates. If specified, this value is inserted into the application manifest.

  The following properties are set in the **Publish Options** dialog box, accessed from the **Publish** page.

- `PublisherName` specifies the name of the publisher displayed in the prompt shown when installing or running the application. In the case of an installed application, it is also used to specify the folder name on the **Start** menu.

- `ProductName` specifies the name of the product displayed in the prompt shown when installing or running the application. In the case of an installed application, it is also used to specify the shortcut name on the **Start** menu.

  The following properties are set in the **Prerequisites** dialog box, accessed from the **Publish** page.

- `BootstrapperEnabled` determines whether to generate the *setup.exe* bootstrapper.

- `IsWebBootstrapper` determines whether the *setup.exe* bootstrapper works over the Web or in disk-based mode.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL, 및 UpdateURL
 The following table shows the four URL options for ClickOnce deployment.

|URL option|설명|
|----------------|-----------------|
|`PublishURL`|Required if you are publishing your ClickOnce application to a Web site.|
|`InstallURL`|옵션. Set this URL option if the installation site is different than the `PublishURL`. For example, you could set the `PublishURL` to an FTP path and set the `InstallURL` to a Web URL.|
|`SupportURL`|옵션. Set this URL option if the support site is different than the `PublishURL`. For example, you could set the `SupportURL` to your company's customer support Web site.|
|`UpdateURL`|옵션. Set this URL option if the update location is different than the `InstallURL`. For example, you could set the `PublishURL` to an FTP path and set the `UpdateURL` to a Web URL.|

## <a name="see-also"></a>참조
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [연습: ClickOnce 애플리케이션 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
