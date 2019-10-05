---
title: 왕복 확장 하는 방법
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 392a0157522f5baa8e8736d52c940b31c0a44cde
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826037"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>방법: 확장을 Visual Studio 2017 및 Visual Studio 2015와 호환 되도록

이 문서에서는 확장성 프로젝트를 Visual Studio 2015와 Visual Studio 2017 간의 왕복 하는 방법을 설명 합니다. 이 업그레이드를 완료 한 후 프로젝트를 열고, 빌드, 설치를 Visual Studio 2015 및 Visual Studio 2017 둘 다에서 실행 됩니다. 참조로 Visual Studio 2015와 Visual Studio 2017 간의 왕복 수 있는 일부 확장 프로그램에서 확인할 수 있습니다 합니다 [VS SDK 확장성 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples)합니다.

만 Visual Studio 2017에서 빌드 하지만 Visual Studio 2015 및 Visual Studio 2017 둘 다에서 실행 하려면 VSIX 출력 하려는 경우 다음을 참조 합니다 [확장 마이그레이션 문서](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)합니다.

> [!NOTE]
> Visual Studio의 버전 간에 변경으로 인해 다른 버전에서 작동 되는 몇 가지 사항 작동 하지 않습니다. 액세스 하려는 기능은 버전 모두에서 사용할 수 있습니다 하거나 확장 해야 예기치 않은 결과입니다.

라운드트립 VSIX에이 문서의 완료 단계의 개요는 다음과 같습니다.

1. 올바른 NuGet 패키지를 가져옵니다.
2. 확장 매니페스트를 업데이트 합니다.
    * 설치 대상
    * 전제 조건
3. CSProj를 업데이트 합니다.
    * `<MinimumVisualStudioVersion>`를 업데이트합니다.
    * 추가 된 `<VsixType>` 속성입니다.
    * 디버깅 속성 추가 `($DevEnvDir)` 3 회입니다.
    * 빌드 도구 및 대상을 가져오기에 대 한 조건을 추가 합니다.

4. 빌드 및 테스트

## <a name="environment-setup"></a>환경 설정

이 문서에서는 다음이 컴퓨터에 설치 되어 있다고 가정 합니다.

* VS SDK가 설치 된 visual Studio 2015
* 확장성 워크 로드가 설치 된 visual Studio 2017

## <a name="recommended-approach"></a>권장 되는 방법

대신 Visual Studio 2017의 Visual Studio 2015를 사용 하 여이 업그레이드를 시작 하는 것이 좋습니다. Visual Studio 2015에서 개발의 주요 장점은 Visual Studio 2015에서 사용할 수 없는 어셈블리를 참조 하지 않도록 확인 하는 것입니다. Visual Studio 2017에서 개발할 경우 Visual Studio 2017에만 존재 하는 어셈블리에 대 한 종속성을 발생할 수 있는 위험이 있습니다.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Project.json에 대 한 참조가 없으므로 확인

이 문서의 뒷부분에서 조건부 import 문을에 삽입 됩니다 여 * *.csproj* 파일입니다. 이 NuGet 참조에 저장 된 경우 작동 하지 않습니다 *project.json*합니다. 따라서 것이 좋습니다. 모든 NuGet 참조를 이동 합니다 *packages.config* 파일입니다.
프로젝트에 포함 된 경우는 *project.json* 파일:

* 에 대 한 참조를 기록해 *project.json*합니다.
* **솔루션 탐색기**를 삭제 합니다 *project.json* 프로젝트의 파일. 이 삭제 합니다 *project.json* 파일과 프로젝트에서 제거 합니다.
* NuGet 참조를 프로젝트에 다시 추가 합니다.
  * 마우스 오른쪽 단추로 클릭 합니다 **솔루션** 선택한 **솔루션용 NuGet 패키지 관리**합니다.
  * Visual Studio에서 자동으로 만듭니다는 *packages.config* 파일입니다.

> [!NOTE]
> 마우스 오른쪽 단추로 클릭 하 여 추가 해야 할 수 프로젝트가 EnvDTE 패키지에 포함 하는 경우 **참조** 선택 **참조 추가** 적절 한 참조를 추가 합니다. NuGet 패키지를 사용 하 여 프로젝트를 빌드하는 동안 오류를 만들 수 있습니다.

## <a name="add-appropriate-build-tools"></a>적절 한 빌드 도구 추가

빌드 및 디버그를 적절 하 게 처리할 수 있게 빌드 도구 추가 되도록 해야 합니다. Microsoft는이 호출된 Microsoft.VisualStudio.Sdk.BuildTasks에 대 한 어셈블리를 만들었습니다.

을 빌드하고 Visual Studio 2015 및 2017 둘 다에서 VSIXv3를 배포 하려면 다음 NuGet 패키지는 필요 합니다.

버전 | 작성된 도구
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

이를 수행하려면:

* Microsoft.VisualStudio.Sdk.BuildTasks.14.0 NuGet 패키지를 프로젝트에 추가 합니다.
* 프로젝트가 Microsoft.VSSDK.BuildTools 없으면 추가 합니다.
* Microsoft.VSSDK.BuildTools 버전 확인 15.x 이상.

## <a name="update-extension-manifest"></a>확장 매니페스트 업데이트

### <a name="1-installation-targets"></a>1. 설치 대상

Visual Studio는 VSIX 빌드에 대 한 대상 버전을 지시 해야 합니다. 일반적으로 이러한 참조는 버전 14.0 (Visual Studio 2015), 버전 15.0 (Visual Studio 2017) 또는 버전 16.0 (Visual Studio 2019). 경우에 두 버전을 대상으로 해야 하므로 확장 둘 다 설치 된 VSIX를 구축 하려고 합니다. 빌드 및 14.0 보다 이전 버전에서 설치 하려면 VSIX를 하려는 경우이 가능; 이전 버전 번호를 설정 하 여 그러나 버전 10.0 더 이상 지원 되지.

* 엽니다는 *source.extension.vsixmanifest* Visual Studio에서 파일입니다.
* 엽니다는 **설치 대상** 탭 합니다.
* 변경 된 **버전 범위** 를 [14.0, 17.0). ' [' 붙여넣습니다 14.0 및 모든 버전을 포함 하도록 Visual Studio를 알려 줍니다. ')'를, 모든 버전을 포함 하도록 Visual Studio 하지만 포함 하지 않는 버전 17.0 지시 합니다.
* Visual Studio의 모든 인스턴스를 닫고 모든 변경 내용을 저장 합니다.

![설치 대상 이미지](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. 필수 구성 요소를 추가 합니다 *extension.vsixmanifest* 파일

필수 구성 요소로 Visual Studio 핵심 편집기 필요합니다. Visual Studio를 열고 업데이트 된 매니페스트 디자이너를 사용 하 여 필수 구성 요소를 삽입 합니다.

이렇게 하려면 수동으로.

* 파일 탐색기에서 프로젝트 디렉터리로 이동 합니다.
* 엽니다는 *extension.vsixmanifest* 텍스트 편집기를 사용 하 여 파일입니다.
* 다음 태그를 추가 합니다.

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 파일을 저장한 후 닫습니다.

> [!NOTE]
> Visual Studio 2017의 모든 버전과 호환 되는지 확인 하는 필수 구성 요소 버전을 수동으로 편집 해야 합니다. 디자이너는 최소 버전 (예를 들어 15.0.26208.0) Visual Studio의 현재 버전으로 삽입 때문입니다. 그러나 다른 사용자가 이전 버전 수 없으므로 수동으로 편집 하려면이를 15.0입니다.

이 시점에서 매니페스트 파일은 다음과 같이 표시 됩니다.

![필수 구성 요소 예제](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>프로젝트 파일 (myproject.csproj) 수정

이 단계를 수행 하는 동안 열려는 수정 된.csproj에 대 한 참조 하는 것이 좋습니다. 몇 가지 예제를 찾을 수 있습니다 [여기](https://github.com/Microsoft/VSSDK-Extensibility-Samples)합니다. 모든 확장성 샘플을 찾습니다 합니다 *.csproj* 참조에 대 한 파일 및 다음 단계를 실행 합니다.

* 프로젝트 디렉터리를 이동할 **파일 탐색기**합니다.
* 엽니다는 *myproject.csproj* 텍스트 편집기를 사용 하 여 파일입니다.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. 업데이트 된 MinimumVisualStudioVersion

* 최소 visual studio 버전으로 `$(VisualStudioVersion)` 조건문에 대 한 추가 합니다. 존재 하지 않는 경우 이러한 태그를 추가 합니다. 태그 아래와 같이 설정 되었는지 확인 합니다.

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. VsixType 속성을 추가 합니다.

* 다음 태그를 추가 `<VsixType>v3</VsixType>` 속성 그룹입니다.

> [!NOTE]
> 이 추가 하는 것이 좋습니다. 아래는 `<OutputType></OutputType>` 태그입니다.

### <a name="3-add-the-debugging-properties"></a>3. 디버깅 속성 추가

* 다음 속성 그룹을 추가 합니다.

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 다음 코드 예제에서의 모든 인스턴스를 삭제 합니다 *.csproj* 파일 *. csproj.user* 파일:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. 빌드 도구 가져오기에 조건 추가

* 추가 조건부 명령문을 추가 합니다 `<import>` Microsoft.VSSDK.BuildTools 참조 하는 태그입니다. 삽입 `'$(VisualStudioVersion)' != '14.0' And` 조건문 맨 앞에 있습니다. 이러한 문은 머리글과 바닥글을 csproj 파일에 표시 됩니다.

예:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* 추가 조건부 명령문을 추가 합니다 `<import>` 는 Microsoft.VisualStudio.Sdk.BuildTasks.14.0 있는 태그입니다. 삽입 `'$(VisualStudioVersion)' == '14.0' And` 조건문 맨 앞에 있습니다. 이러한 문은 머리글과 바닥글을 csproj 파일에 표시 됩니다.

예를 들어:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* 추가 조건부 명령문을 추가 합니다 `<Error>` Microsoft.VSSDK.BuildTools 참조 하는 태그입니다. 삽입 하 여이 작업을 수행할 `'$(VisualStudioVersion)' != '14.0' And` 조건문 맨 앞에 있습니다. 이러한 문은 csproj 파일의 바닥글에 표시 됩니다.

예를 들어:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* 추가 조건부 명령문을 추가 합니다 `<Error>` 는 Microsoft.VisualStudio.Sdk.BuildTasks.14.0 있는 태그입니다. 삽입 `'$(VisualStudioVersion)' == '14.0' And` 조건문 맨 앞에 있습니다. 이러한 문은 csproj 파일의 바닥글에 표시 됩니다.

예:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Csproj 파일을 저장 하 고 닫습니다.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 및 Visual Studio 2017에서 확장 설치를 테스트 합니다.

이 시점에서 프로젝트는 Visual Studio 2015와 Visual Studio 2017에서 설치할 수 있는 VSIXv3 만들 준비 해야 합니다.

* Visual Studio 2015에서 프로젝트를 엽니다.
* 프로젝트를 빌드하고 확인 VSIX 올바르게 빌드되는지 출력에서 합니다.
* 프로젝트 디렉터리로 이동 합니다.
* 엽니다는 *\bin\Debug* 폴더입니다.
* VSIX 파일을 두 번 클릭을 Visual Studio 2015 및 Visual Studio 2017에 확장을 설치 합니다.
* 확장을 볼 수 있는지 확인 **도구** > **확장 및 업데이트** 에 **설치 된** 섹션입니다.
* 실행/작동 하는지 확인 하려면 확장을 사용 하려고 시도 합니다.

![VSIX 찾기](media/finding-a-VSIX-example.png)

> [!NOTE]
> 메시지와 함께 프로젝트가 응답 하지 않는 경우 **파일을 열어**, Visual Studio를 강제 종료, 프로젝트 디렉터리로 이동, 숨겨진된 폴더를 표시 및 삭제 합니다 *.vs* 폴더입니다.
