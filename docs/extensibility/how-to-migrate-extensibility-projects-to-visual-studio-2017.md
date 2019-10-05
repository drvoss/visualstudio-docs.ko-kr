---
title: '방법: Visual Studio 2017로 확장성 프로젝트 마이그레이션 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: f5edad198727ea33d3bf293fa0ee1baf3afb5b3b
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823896"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>방법: Visual Studio 2017로 확장성 프로젝트 마이그레이션

이 문서에서는 Visual Studio 2017로 확장성 프로젝트를 업그레이드 하는 방법에 설명 합니다. 프로젝트 파일을 업데이트 하는 방법을 설명 하는, 하는 것 외에도 또한 확장 매니페스트 버전 2 (VSIX v2)에서 새 버전 3 VSIX 매니페스트 형식 (VSIX v3)로 업그레이드 하는 방법을 설명 합니다.

## <a name="install-visual-studio-2017-with-required-workloads"></a>필요한 워크 로드를 사용 하 여 Visual Studio 2017 설치

설치에 다음 워크 로드에 포함 되어 있는지 확인 합니다.

* .NET 데스크톱 개발
* Visual Studio 확장 개발

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017에서 VSIX 솔루션을 열으십시오

모든 VSIX 프로젝트에는 Visual Studio 2017에는 주 버전 단방향 업그레이드가 필요 합니다.

프로젝트 파일 (예를 들어 * *.csproj*) 업데이트 됩니다.

* MinimumVisualStudioVersion-이제 15.0으로 설정 합니다.
* OldToolsVersion (하는 경우 이전에 존재)-이제 14.0으로 설정

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet 패키지를 업데이트 합니다.

> [!Note]
> 솔루션이 Microsoft.VSSDK.BuildTools NuGet 패키지를 참조 하지 않으면이 단계를 건너뛸 수 있습니다.

새 VSIX v3의 확장 프로그램을 빌드하려면 (버전 3) 형식으로 솔루션 해야 새 VSSDK Build Tools를 사용 하 여 빌드해야 합니다. 이 Visual Studio 2017을 사용 하 여 설치할 수 있지만 v2 VSIX 확장 NuGet 통해 이전 버전에 대 한 참조를 보유할 수 있습니다. 그렇다면 Microsoft.VSSDK.BuildTools NuGet 패키지 솔루션에 대 한 업데이트를 수동으로 설치 해야 합니다.

Microsoft.VSSDK.BuildTools NuGet 참조를 업데이트 합니다.

* 선택한 솔루션을 마우스 오른쪽 단추로 클릭 **솔루션용 NuGet 패키지 관리**합니다.
* 로 이동 합니다 **업데이트** 탭 합니다.
* 선택 **Microsoft.VSSDK.BuildTools (최신 버전)** 합니다.
* 키를 눌러 **업데이트**합니다.

![VSSDK 빌드 도구](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX 확장 매니페스트를 변경합니다.

Visual Studio의 설치를 사용자의 확장을 실행 하는 데 필요한 모든 어셈블리를 갖도록 하려면 확장 매니페스트 파일에서 모든 필수 구성 요소 또는 패키지를 지정 합니다. 사용자가 확장을 설치 하려고 합니다 VSIXInstaller가 모든 필수 구성 요소는 설치 되어 있는지 확인 합니다. 일부 값이 없는 경우 확장 설치 프로세스의 일부로 누락 된 구성 요소를 설치 하려면 사용자 라는 메시지가 표시 됩니다.

> [!Note]
> 여기에 최소한 모든 확장의 필수 구성 요소로 Visual Studio 핵심 편집기 구성 요소를 지정 해야 합니다.

* 확장 매니페스트 파일 편집 (일반적으로 호출 *source.extension.vsixmanifest*).
* 확인 `InstallationTarget` 15.0을 포함 합니다.
* 아래 예에서 같이 필요한 설치 필수 구성 요소를 추가 합니다.
  * 설치 필수 구성 요소에 대 한 구성 요소 Id를 지정 하는 것이 좋습니다.
  * 이 문서의 끝에 있는 섹션을 참조 하세요 [구성 요소 Id를 식별 하는 방법은](#find-component-ids)합니다.

예제:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>옵션: 디자이너를 사용 하 여 VSIX 확장 매니페스트를 변경 하려면

매니페스트 XML을 직접 편집 하는 대신 새 따르면 **필수 구성 요소** 필수 구성 요소를 선택 하 여 매니페스트 디자이너와 XML에서 탭 수 업데이트 됩니다.

> [!Note]
> 매니페스트 디자이너만 하면 현재 Visual Studio 인스턴스에 설치 된 구성 (워크 로드 또는 패키지)를 선택 합니다. 워크 로드, 패키지 또는 현재 설치 되어 있지 않은 구성 요소에 대 한 필수 구성 요소를 추가 해야 할 경우 매니페스트 XML을 직접 편집 합니다.

* 오픈 *source.extension.vsixmanifest [디자인]* 파일입니다.
* 선택 **필수 구성 요소** 누릅니다 탭 **새로 만들기** 단추입니다.

   ![VSIX 매니페스트 디자이너](media/vsix-manifest-designer.png)

* 합니다 **필수 조건 새 추가** 창이 열립니다.

   ![vsix 필수 구성 요소를 추가 합니다.](media/add-vsix-prerequisite.png)

* 드롭다운을 클릭 **이름을** 원하는 필수 구성 요소를 선택 합니다.
* 필요한 경우에 버전을 업데이트 합니다.

   > [!Note]
   > 버전 필드는 최대 범위에 걸쳐 (하지만 제외)를 사용 하 여 현재 설치 된 구성 요소의 버전을 사용 하 여 미리 채워진 될 구성 요소의 다음 주 버전.

   ![roslyn 필수 구성 요소를 추가 합니다.](media/add-roslyn-prerequisite.png)

* **확인**을 누릅니다.

## <a name="update-debug-settings-for-the-project"></a>프로젝트 디버그 설정 업데이트

Visual Studio의 실험적 인스턴스에서 확장 프로그램을 디버그 하려는 경우 확인에 대 한 프로젝트 설정 **디버그** > **작업을 시작** 에 **외부 시작 프로그램:** 값으로 설정 합니다 *devenv.exe* Visual Studio 2017 설치의 파일입니다.

것 처럼 보일 수 있습니다. *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![시작 외부 프로그램](media/start-external-program.png)

> [!Note]
> 디버그 시작 작업은 일반적으로에 저장 합니다 *. csproj.user* 파일입니다. 이 파일은 일반적으로에 포함 합니다 *.gitignore* 파일 하 고 따라서 일반적으로 함께 저장 되지 않습니다 소스 제어 하고자 하는 경우 다른 프로젝트 파일입니다. 이와 같이 솔루션이 소스 제어에서 새가 끌어온 것 프로젝트 시작 작업에 대 한 설정 값이 없는 것입니다. Visual Studio 2017을 사용 하 여 만든 새 VSIX 프로젝트를 *. csproj.user* 현재 Visual Studio 설치 디렉터리를 가리키는 기본값을 사용 하 여 만든 파일입니다. 그러나 v2 VSIX 확장으로 마이그레이션하는 경우 것입니다를 *. csproj.user* 파일에는 이전 Visual Studio 버전의 설치 디렉터리에 대 한 참조가 포함 됩니다. 값을 설정 **디버그** > **작업을 시작** 확장 프로그램을 디버그 하려는 경우 시작 하려면 올바른 Visual Studio 실험적 인스턴스를 사용 하면 됩니다.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>확장 (것으로 잘못 VSIX v3) 빌드되는지 확인 합니다.

* VSIX 프로젝트를 빌드하십시오.
* 생성 된 VSIX를 압축을 풉니다.
  * 기본적으로 VSIX 파일 안에 상주 *bin/Debug* 또는 *bin/Release* 으로 *[YourCustomExtension].vsix*합니다.
  * 이름 바꾸기 *.vsix* 하 *.zip* 내용을 쉽게 볼 수 있습니다.
* 세 개의 파일이 있는지 확인 합니다.
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>모든 필수 설치 되 면 확인

VSIX 설치 필요한 모든 필수 구성 요소를 사용 하 여 컴퓨터에 성공적으로 설치 하는 테스트입니다.

> [!Note]
> 모든 확장을 설치 하기 전에 Visual Studio의 모든 인스턴스를 종료 하세요.

확장을 설치 하려고 시도 합니다.

* On Visual Studio 2017

![Visual Studio 2017에서 VSIX 설치 관리자](media/vsixinstaller-vs-2017.png)

* 선택 사항: 이전 버전의 Visual Studio에서 확인 합니다.
  * 이전 버전과 호환성을 증명합니다.
  * Visual Studio 2012, Visual Studio 2013, Visual Studio 2015에 대해 작동 합니다.
* 선택 사항: 다양 한 버전을 제공 하는 VSIX 설치 관리자 버전 검사를 확인 합니다.
  * (설치) 하는 경우 이전 버전을의 Visual Studio에 포함 되어 있습니다.
  * Visual Studio 2017에 포함 됩니다.

Visual Studio 최근에 열린 경우 다음과 같은 대화 상자가 표시 될 수 있습니다.

![vs를 실행 중인 프로세스](media/vs-running-processes.png)

프로세스 종료를 표시 될 때까지 기다리거나 작업을 수동으로 종료 합니다. 나열 된 이름으로 또는 괄호 안에 나열 된 PID를 사용 하 여 프로세스를 찾을 수 있습니다.

> [!Note]
> 이러한 프로세스는 자동으로 종료 되지 Visual Studio 인스턴스에 실행 되는 동안. 다른 사용자 로부터 비롯-컴퓨터에 Visual Studio의 모든 인스턴스를 종료 한 다음 다시 시도 하 있습니다를 확인 합니다.

## <a name="check-when-missing-the-required-prerequisites"></a>필요한 필수 구성 요소를 누락 하는 경우를 확인 합니다.

* 확장을 설치 하려면 컴퓨터에서 Visual Studio 2017 아닙니다 포함 된 필수 구성 요소 (위)에 정의 된 모든 구성 요소를 시도 합니다.
* 설치 하 게 식별 하는 누락 된 구성 요소/s는 VSIXInstaller에서 필수 구성 요소로 나열 지 확인 합니다.
* 참고: 모든 필수 구성 요소 확장을 사용 하 여 설치 해야 하는 경우 권한 상승 해야 합니다.

![vsixinstaller 누락 된 필수 구성 요소](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>구성 요소 결정

종속성을 조회할 때 종속성 여러 구성 요소를 매핑할 수 있는지 확인할 수 있습니다. 확인 하 여 필수 조건으로 지정 해야 하는 종속성에는 비슷한 기능을 확장 하는 구성 요소를 선택 하는 것이 좋습니다 하 고도 사용자 및 어떤 유형의 구성 요소를 고려해 야 할 가능성이 설치한 또는 하지 않습니다. 설치에 유의 합니다. 빌드를 확장 방식으로 필요한 필수 구성 요소, 확장을 실행할 수 있는 최소만을 충족 하는 위치 및 추가 기능에 대 한 특정 구성 요소 검색 되지 않는 경우에 유휴 상태로 것도 좋습니다.

추가 지침을 제공 하는 몇 가지 일반적인 확장 프로그램 유형 및 해당 제안 된 필수 구성 요소 확인 했습니다.

확장 형식 | 표시 이름 | ID
--- | --- | ---
편집기 | Visual Studio 핵심 편집기 | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 및 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | 관리되는 데스크톱 워크로드 핵심 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
디버거 | Just-In-Time 디버거 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>구성 요소 Id 찾기

에 Visual Studio 제품별로 정렬 된 구성 요소 목록이 [Visual Studio 2017 워크 로드 및 구성 요소 Id](https://aka.ms/vs2017componentIDs)합니다. 매니페스트 내에서에 필수 구성 요소 Id에 대 한 이러한 구성 요소 Id를 사용 합니다.

특정 이진을 포함 하는 구성 요소 확실 하지 않은 경우 다운로드 합니다 [구성 요소 이진 매핑 스프레드시트->](https://aka.ms/vs2017componentid-binaries)합니다.

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Excel 시트에 4 개의 열을 가지 있습니다. **구성 요소 이름**, **ComponentId**합니다 **버전**, 및 **이진 파일 이름 /** 합니다.  검색 하 고 특정 구성 요소 및 이진 파일을 찾을 필터를 사용할 수 있습니다.

모든 참조에 대 한 먼저 핵심 편집기 (Microsoft.VisualStudio.Component.CoreEditor) 구성 요소에서 무엇 인지 확인 합니다.  최소한 핵심 편집기 구성 요소를 모든 확장에 대 한 필수 조건으로 지정할 필요 합니다. 참조 중 남아 있는 핵심 편집기에 있지 않은, 필터를 추가 합니다 **이진 파일 / 파일 이름을** 해당 참조의 하위 집합 중 하나라도 있는 구성 요소를 찾는 섹션.

예를 들면 다음과 같습니다.

* 디버거 확장을 설치 되어 있는 경우 프로젝트에 대 한 참조를 알고 *VSDebugEng.dll* 및 *VSDebug.dll*에서 필터 단추를 클릭 합니다 **이진 파일 / 파일 이름**헤더입니다.  "VSDebugEng.dll"에 대 한 검색 및 선택 *확인*합니다.  다음 필터 단추를 클릭 합니다 **이진 파일 / 파일 이름** 다시 머리글과 "VSDebug.dll"를 검색 합니다.  확인란을 선택 **필터링의 현재 선택 항목을 추가** 선택한 **확인**합니다.  이제 살펴봅니다 합니다 **구성 요소 이름** 가장 하는 구성 요소를 찾을 수 확장 형식이 관련 된 합니다. 이 예제에서는 시간에 하면 선택한는 디버거 및 프로그램 vsixmanifest에 추가 합니다.
* 디버거 요소를 사용 하 여 프로젝트를 처리 하는지 알고 있는 경우에 "디버거에 대" 필터 검색 상자에 이름에는 디버거를 포함 하는 구성 요소를 검색할 수 있습니다.

## <a name="specify-a-visual-studio-2017-release"></a>Visual Studio 2017 릴리스를 지정 합니다.

확장 프로그램에서 Visual Studio 2017의 특정 버전에 필요한 경우 예를 들어, 15.3에 릴리스된 기능에 따라, VSIX에 빌드 번호를 지정 해야 합니다 **에서 InstallationTarget**합니다. 예를 들어, 15.3 릴리스 빌드 번호 '15.0.26730.3'는 있습니다. 릴리스 빌드 번호를 매핑을 볼 수 있습니다 [여기](../install/visual-studio-build-numbers-and-release-dates.md)합니다. 릴리스 번호 '15.3'를 사용 하 여 올바르게 작동 하지 않습니다.

확장 프로그램에 15.3 필요 하거나 선언 합니다 이상 합니다 **버전에서 InstallationTarget** 으로 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
