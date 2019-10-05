---
title: ClickOnce를 사용 하 여 multitarget 앱 배포
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 38418a1ca11c23ab12d64deadfb91079bc957493
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747488"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>방법: ClickOnce를 사용하여 여러 버전의 .NET Framework에서 실행할 수 있는 애플리케이션 배포
ClickOnce 배포 기술을 사용 하 여 여러 버전의.NET Framework를 대상으로 하는 응용 프로그램을 배포할 수 있습니다. 그러려면 생성 하 고 응용 프로그램 및 배포 매니페스트를 업데이트 합니다.

> [!NOTE]
> 여러 버전의.NET Framework를 대상으로 응용 프로그램을 변경 하기 전에 여러 버전의.NET Framework를 사용 하 여 응용 프로그램을 실행 해야 합니다. 버전 공용 언어 런타임은.NET Framework 2.0,.NET Framework 3.0 및.NET Framework 3.5와.NET Framework 4 간에 다릅니다.

 이 프로세스에는 다음 단계가 필요합니다.

1. 응용 프로그램 및 배포 매니페스트를 생성 합니다.

2. 여러.NET Framework 버전을 나열 하려면 배포 매니페스트를 변경 합니다.

3. 변경 된 *app.config* 는 호환 가능한.NET Framework 런타임 버전을 나열 하는 파일입니다.

4. .NET Framework 어셈블리와 종속 어셈블리를 표시 하도록 응용 프로그램 매니페스트를 변경 합니다.

5. 응용 프로그램 매니페스트에 서명 합니다.

6. 업데이트 및 배포 매니페스트에 서명 합니다.

### <a name="to-generate-the-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트를 생성 하려면

- 프로젝트 디자이너의 게시 페이지 또는 게시 마법사를 사용 하 여를 응용 프로그램을 게시 하 여 응용 프로그램 및 배포 매니페스트 파일을 생성 합니다. 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) 나 [프로젝트 디자이너, 게시 페이지](../ide/reference/publish-page-project-designer.md)합니다.

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>여러.NET Framework 버전을 나열 하려면 배포 매니페스트를 변경 하려면

1. 게시 디렉터리에서 Visual Studio에서 XML 편집기를 사용 하 여 배포 매니페스트를 엽니다. 배포 매니페스트에 합니다 *.application* 파일 이름 확장명입니다.

2. 사이 XML 코드를 대체 합니다 `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` 및 `</compatibleFrameworks>` 응용 프로그램에 대해 지원 되는.NET Framework 버전을 나열 하는 xml 요소입니다.

     다음 표에서 사용 가능한.NET Framework 버전 및 배포 매니페스트에 추가할 수 있는 해당 XML의 일부를 보여 줍니다.

    |.NET Framework 버전|XML|
    |----------------------------|---------|
    |4 클라이언트|\<framework targetVersion = "4.0" 프로필 "클라이언트" supportedRuntime = = "4.0.30319" / >|
    |4 전체|\<framework targetVersion = "4.0" 프로필 "전체" supportedRuntime = = "4.0.30319" / >|
    |3.5 클라이언트|\<framework targetVersion = "3.5" 프로필 "클라이언트" supportedRuntime = = "2.0.50727" / >|
    |3.5 전체|\<framework targetVersion = "3.5" 프로필 "전체" supportedRuntime = = "2.0.50727" / >|
    |3.0|\<프레임워크 targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>호환 가능한.NET Framework 런타임 버전을 나열 하려면 app.config 파일을 변경 하려면

1. 솔루션 탐색기에서 엽니다는 *app.config* Visual Studio에서 XML 편집기를 사용 하 여 파일입니다.

2. 사이 XML 코드를 바꿉니다 (또는 추가)를 `<startup>` 및 `</startup>` 응용 프로그램에 대해 지원 되는.NET Framework 런타임을 나열 하는 xml 요소입니다.

     다음 표에서 사용 가능한.NET Framework 버전 및 배포 매니페스트에 추가할 수 있는 해당 XML의 일부를 보여 줍니다.

    |.NET framework 런타임 버전|XML|
    |------------------------------------|---------|
    |4 클라이언트|\<supportedRuntime 버전="v4.0.30319" sku=".NETFramework,버전=v4.0,Profile=Client" />|
    |4 전체|\<supportedRuntime 버전="v4.0.30319" sku=".NETFramework,버전=v4.0" />|
    |3.5 전체|\<supportedRuntime 버전="v2.0.50727"/>|
    |3.5 클라이언트|\<supportedRuntime 버전="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>.NET Framework 어셈블리와 종속 어셈블리를 표시 하기 위해 응용 프로그램 매니페스트를 변경 하려면

1. 게시 디렉터리에서 Visual Studio에서 XML 편집기를 사용 하 여 응용 프로그램 매니페스트를 엽니다. 배포 매니페스트에 합니다 *.manifest* 파일 이름 확장명입니다.

2. 추가 `group="framework"` sentinel 어셈블리에 대 한 종속성 XML (`System.Core`, `WindowsBase`합니다 `Sentinel.v3.5Client`, 및 `System.Data.Entity`). 예를 들어, XML은 다음과 같아야 합니다.

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. 버전 번호를 업데이트 합니다 `<assemblyIdentity>` 최소 공통 분모는.NET Framework의 버전 번호를 Microsoft.Windows.CommonLanguageRuntime에 대 한 요소입니다. 예를 들어, 응용 프로그램에서.NET Framework 3.5 및.NET Framework 4를 대상으로 하는 경우 2.0.50727.0 사용 하 여 버전 번호 및 XML 다음과 같이 표시 됩니다.

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>매니페스트를 업데이트 하 고 응용 프로그램 및 배포에 다시 서명

- 업데이트 및 응용 프로그램 및 배포 매니페스트에 다시 서명 합니다. 자세한 내용은 [방법: 애플리케이션 및 배포 매니페스트 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조하세요.

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks > 요소](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<종속성 > 요소](../deployment/dependency-element-clickonce-application.md)
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [구성 파일 스키마](/dotnet/framework/configure-apps/file-schema/index)
