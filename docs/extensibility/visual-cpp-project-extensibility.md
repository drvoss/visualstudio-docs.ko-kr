---
title: Visual C++ 확장성 프로젝트
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10869ad290b0b8df614d25d792d0b3ed1e88eb17
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825562"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ Project 시스템 확장성 및 도구 통합

시각적 개체 C++ .vcxproj 파일에 대 한 프로젝트 시스템을 사용 합니다. 기반이 되는 [Visual Studio 공통 프로젝트 시스템 (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) 추가 정보와 C++ 새 도구를 쉽게 통합에 대 한 특정 확장 지점 아키텍처를 빌드하고 플랫폼을 대상으로 합니다.

## <a name="c-msbuild-targets-structure"></a>C++MSBuild 대상 구조

모든.vcxproj 파일을 이러한 파일을 가져옵니다.

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

이러한 파일을 거의 정의 자체입니다. 대신, 이러한 속성 값에 따라 다른 파일 가져오는:

- `$(ApplicationType)`

   예를 들면 다음과 같습니다. Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   이 해야 유효한 버전 문자열 형식.build.revision]].

   예를 들면 다음과 같습니다. 1.0, 10.0.0.0

- `$(Platform)`

   빌드 아키텍처 라는 이유 때문에 "플랫폼"입니다.

   예를 들면 다음과 같습니다. Win32, x86, x64, ARM

- `$(PlatformToolset)`

   예: v140, v141, v141_xp, llvm

이러한 속성 값에서 폴더 이름을 지정 합니다 `$(VCTargetsPath)` 루트 폴더:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*응용 프로그램 유형*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*플랫폼*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*플랫폼*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

합니다 `$(VCTargetsPath)` \\ *플랫폼* \\ 폴더는 때 `$(ApplicationType)` 는 빈 Windows 데스크톱 프로젝트에 대 한 합니다.

### <a name="add-a-new-platform-toolset"></a>새 플랫폼 도구 집합을 추가 합니다.

예를 들어, "MyToolset" 기존 Win32 플랫폼을 위한 새 도구 집합을 추가 하려면 만듭니다는 *MyToolset* 아래에 폴더 `$(VCTargetsPath)`  *\\플랫폼\\Win32\\ PlatformToolsets\\* 를 만들고 *Toolset.props* 하 고 *Toolset.targets* 파일입니다.

아래에 있는 각 폴더 이름의 *PlatformToolsets* 나타나는 **프로젝트 속성** 으로 사용할 수 있는 대화 상자 **플랫폼 도구 집합** 지정 된 플랫폼의 경우 다음과 같이:

![프로젝트 속성 페이지 대화 상자에서 플랫폼 도구 집합 속성](media/vc-project-extensibility-platform-toolset-property.png "프로젝트 속성 페이지 대화 상자에서는 플랫폼 도구 집합 속성")

유사한 만들어야 *MyToolset* 폴더 및 *Toolset.props* 하 고 *Toolset.targets* 각 기존 플랫폼 폴더의 파일이 도구이 집합을 지원 합니다.

### <a name="add-a-new-platform"></a>새 플랫폼 추가

예를 들어, "MyPlatform"가, 새 플랫폼을 추가 하려면 만듭니다는 *MyPlatform* 아래에 폴더 `$(VCTargetsPath)`  *\\플랫폼\\* 를 만들어  *Platform.default.props*, *Platform.props*, 및 *Platform.targets* 파일입니다. 만들 수도 `$(VCTargetsPath)`  *\\플랫폼\\* <strong><em>MyPlatform</em></strong> *\\PlatformToolsets\\*  폴더에 하나 이상의 도구 집합을 만듭니다.

아래에 있는 모든 폴더 이름을 *플랫폼* 각각에 대 한 폴더 `$(ApplicationType)` 및 `$(ApplicationTypeRevision)` 사용할 수 있는 IDE에 표시 **플랫폼** 프로젝트에 대 한 선택입니다.

![새 프로젝트 플랫폼 대화 상자에서 새 플랫폼을 선택](media/vc-project-extensibility-new-project-platform.png "새 프로젝트 플랫폼 대화 상자에서 새 플랫폼을 선택")

### <a name="add-a-new-application-type"></a>새 응용 프로그램 유형을 추가합니다

새 응용 프로그램 유형을 추가 하려면 만듭니다는 *MyApplicationType* 아래에 폴더 `$(VCTargetsPath)` *\\응용 프로그램 유형\\* 만들고를 *Defaults.props* 파일이 있습니다. 하나 이상의 수정 응용 프로그램 유형에 대 한 필요를 만들 수도 있으므로 `$(VCTargetsPath)`  *\\응용 프로그램 종류\\MyApplicationType\\1.0* 폴더를 만들어는  *Defaults.props* 파일이 있습니다. 또한 만들어야를 `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\플랫폼* 폴더 플랫폼이 하나 이상 만듭니다.

`$(ApplicationType)` 및 `$(ApplicationTypeRevision)` 속성 사용자 인터페이스에 표시 되지 않습니다. 프로젝트 템플릿에 지정 되 고 프로젝트가 만들어진 후 변경할 수 없습니다.

## <a name="the-vcxproj-import-tree"></a>.Vcxproj 가져오기 트리

Microsoft는 가져오기 트리의 간소화 된 C++ props 및 targets 파일 다음과 같습니다.

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*기본값*\\\*. *속성* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*응용 프로그램 종류*\\`$(ApplicationType)`\\*Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*응용 프로그램 종류*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*응용 프로그램 종류*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*플랫폼* \\ `$(Platform)` \\  *Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*기본값*\\\*. *속성*

Windows 데스크톱 프로젝트를 정의 하지는 않습니다 `$(ApplicationType)`이므로 가져오기

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*기본값*\\\*. *속성* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platforms*\\`$(Platform)`\\*Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*기본값*\\\*. *속성*

사용 하 여는 `$(_PlatformFolder)` 보유 하는 속성을 `$(Platform)` 플랫폼 폴더 위치입니다. 이 속성은

> `$(VCTargetsPath)`\\*플랫폼*\\`$(Platform)`

Windows 데스크톱 앱 및

> `$(VCTargetsPath)`\\*응용 프로그램 종류*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*플랫폼*\\`$(Platform)`

그 외 모든 합니다.

Props 파일은이 순서 대로 가져옵니다.

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *속성* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *속성*

대상 파일은이 순서 대로 가져옵니다.

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *대상* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*.*targets*

프로그램 도구 집합에 대 한 몇 가지 기본 속성을 정의 하는 경우에 적절 한 ImportBefore 및 ImportAfter 폴더에 파일을 추가할 수 있습니다.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>작성자 Toolset.props 파일과 Toolset.targets

*Toolset.props* 하 고 *Toolset.targets* 파일에는이 도구 집합을 사용 하는 경우 빌드 중 발생 하는 완전히 제어할 수 있습니다. IDE 사용자 인터페이스의 콘텐츠 등의 일부는 사용 가능한 디버거를 제어할 수도 있습니다는 **속성 페이지** 대화 상자 및 프로젝트 동작의 일부 다른 측면입니다.

전체 빌드 프로세스 도구 집합을 재정의할 수 있지만 일반적으로 원하는를 수정 하거나 일부 빌드 단계를 추가 하거나 기존 빌드 프로세스의 일부로 다른 빌드 도구를 사용 하 여 도구 집합입니다. 이러한 목표를 달성 하는 많은 일반적인 props 및 targets 파일에 도구 집합을 가져올 수 있습니다. 원하는 작업을 수행 하 여 도구 집합에 따라 이러한 파일을 가져오기로 또는 예제로 사용 하 여 유용할 수 있습니다.

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

  이 파일 기본 빌드 프로세스의 주요 부분을 정의 하 고 가져옵니다.

  - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

  - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

  - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   대상 Windows 및 Microsoft 컴파일러를 사용 하는 도구 집합에 대 한 기본값을 설정 합니다.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   이 파일 Windows SDK 위치를 결정 하 고 Windows를 대상으로 하는 앱에 대 한 몇 가지 중요 한 속성을 정의 합니다.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>기본값을 사용 하 여 도구 집합 관련 대상 통합 C++ 빌드 프로세스

기본 C++ 빌드 프로세스에 정의 되어 *Microsoft.CppCommon.targets*합니다. 대상에 있는 모든 특정 빌드 도구를 호출 하지 마세요 기본 빌드 단계, 순서 및 종속성 지정 합니다.

C++ 빌드에 다음 대상으로 표현 되는 세 가지 주요 단계:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

빌드 단계가 독립적으로 실행할 수 있습니다, 되므로 한 번에 실행 하는 대상 항목 그룹 및 다른 단계의 일부로 실행 되는 대상에서 정의 된 속성을 사용할 수 없습니다. 이러한 분할이 특정 빌드 성능 최적화를 허용합니다. 기본적으로 사용 되지 않습니다, 하지만 이러한 구분을 수용 하는 것이 좋습니다 것입니다.

각 단계 내에서 실행 되는 대상은 이러한 속성에 의해 제어 됩니다.

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

각 단계에는 또한 속성 전후에 있습니다.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

참조 된 *Microsoft.CppBuild.targets* 각 단계에 포함 된 대상에 대 한 예제 파일:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

보면 경우 대상에 같은 `_ClCompile`, 자체에서 직접 아무일도 하지 않는 있지만 대신 비롯 한 다른 대상에 따라 달라 집니다 보면 `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` 및 다른 빌드 도구 관련 대상의 빈 대상은으로 정의 됩니다 *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

때문에 `ClCompile` 대상이 비어 있는 경우 도구 집합으로 재정의 되지 않는 한 실제 빌드 작업이 수행 되지 합니다. 도구 집합 대상을 재정의할 수는 `ClCompile` 대상, 즉, 이러한 다른 포함할 수 있습니다 `ClCompile` 가져오면 정의 *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Visual Studio 플랫폼 간 지원을 구현 하기 전에 만든 이름과 달리는 `ClCompile` 대상 CL.exe를 호출할 필요가 없습니다. 적절 한 MSBuild 작업을 사용 하 여 gcc, Clang, 다른 컴파일러를 호출할 수도 것입니다.

`ClCompile` 대상 제외한 모든 종속성이 없어야 합니다 `SelectClCompile` IDE에서 작업을 단일 파일로 컴파일 명령에 필요한 대상입니다.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>MSBuild 도구 집합 대상에서 사용 하는 작업

실제 빌드 도구를 호출 하려면 대상 MSBuild 작업을 호출 해야 합니다. 기본 방법이 [Exec 작업](../msbuild/exec-task.md) 실행할 명령줄을 지정할 수 있습니다. 그러나 빌드 도구 일반적으로 여러 가지 옵션을 입력 합니다. 및에 특별 한 작업을 해야 할 것 있으므로 증분 빌드에 대 한 추적 출력을 추가 합니다. 예를 들어를 `CL` 작업 CL.exe 스위치를 MSBuild 속성을 변환, 응답 파일에 기록 하 고 CL.exe를 호출 합니다. 또한 후속 증분 빌드에 대 한 모든 입력 및 출력 파일을 추적합니다. 자세한 내용은 [증분 빌드 및 최신 검사](#incremental-builds-and-up-to-date-checks)합니다.

Microsoft.Cpp.Common.Tasks.dll 이러한 작업을 구현합니다.

- `BSCMake`

- `CL`

- `ClangCompile` (clang gcc 스위치)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (Exec 같은 하지만 입력 및 출력 추적을 사용 하 여)

- `SetEnv`

- `GetOutOfDateItems`

도구가 있는 경우는 기존 도구와 동일한 작업을 수행 하는 및 유사한 명령줄 스위치 (마찬가지로 clang-cl와 CL)을 둘 다 동일한 태스크를 사용할 수 있습니다.

빌드 도구에 대 한 새 작업을 만들려는 경우 다음 옵션 중에서 선택할 수 있습니다.

1. 이 작업을 거의 사용 하면, 몇 초 빌드에 대 한 중요 하지 MSBuild 'inline' 작업을 사용할 수 있습니다.

   - Xaml 작업 (예: 사용자 지정 빌드 규칙)

     Xaml 작업 선언의 한 예제를 보려면 `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*, 사용법, 참조 `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*합니다.

   - [코드 작업](../msbuild/msbuild-inline-tasks.md)

1. 일반 MSBuild를 사용 하 여 작업 성능 향상 하거나 더 복잡 한 기능이 필요 합니다 [쓰기 작업](../msbuild/task-writing.md) 프로세스입니다.

   모든 입력 및 도구의 출력은 에서처럼 도구 명령줄에 나열 되 면 합니다 `CL`, `MIDL`, 및 `RC` 경우 및 자동 입력 및 출력 파일 추적 및.tlog 파일 만들기를 하려는 경우 작업을 에서파생`Microsoft.Build.CPPTasks.TrackedVCToolTask`클래스입니다. 기본에 대 한 설명서는 현재 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) 클래스에 있는 예제 없거나의 세부 정보에 대 한 설명서는 `TrackedVCToolTask` 클래스입니다. 이 특정 관심 됩니다, 경우 음성 요청에 추가 [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html)합니다.

## <a name="incremental-builds-and-up-to-date-checks"></a>증분 빌드 및 최신 검사

기본 MSBuild 증분 빌드를 사용 하 여 대상 `Inputs` 고 `Outputs` 특성입니다. 이러한 값을 지정 하는 경우 모든 출력 보다 최신 타임 스탬프가 입력 중 하나가 있으면만 MSBuild 대상을 호출 합니다. 소스 파일 종종 포함 또는 다른 파일을 가져오고 빌드 도구 생성 도구 옵션에 따라 다른 출력이, 때문에 가능한 모든 입력을 지정 하기가 어렵습니다 및 MSBuild 대상에 출력 합니다.

이 문제를 관리 하는 C++ 빌드 다른 기술을 사용 하 여 증분 빌드를 지원 합니다. 대부분의 대상 입력 및 출력을 지정 하 고 결과적으로 빌드하는 동안 항상 실행 하지 않습니다. 대상에서 호출 하는 작업 모두에 대 한 정보 입력 및 출력을 쓸 *tlog* .tlog 확장명을 가진 파일입니다. 새로운 최신 기능 및.tlog 파일 변경 내용과 다시 작성 해야 하는 경우를 확인 하는 이후 빌드에서 사용 됩니다. 또한.tlog 파일은 IDE에서 기본 빌드 최신 검사에 대 한 유일한 원본입니다.

모든 입력 및 출력을 확인 하려면 기본 도구 작업 tracker.exe를 사용 하며 [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) MSBuild에서 제공 하는 클래스입니다.

Microsoft.Build.CPPTasks.Common.dll 정의 `TrackedVCToolTask` 공용 추상 기본 클래스입니다. 대부분의 기본 도구 작업은이 클래스에서 파생 됩니다.

Visual Studio 2017 업데이트 15.8부터 사용할 수는 `GetOutOfDateItems` Microsoft.Cpp.Common.Tasks.dll 알려진 입력과 출력을 사용 하 여 사용자 지정 대상에 대 한.tlog 파일을 생성 하기 위해 구현 하는 작업입니다.
사용 하 여 이러한를 만들 수는 또는 `WriteLinesToFile` 작업 합니다. 참조를 `_WriteMasmTlogs` 에서 대상 `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* 예입니다.

## <a name="tlog-files"></a>.tlog 파일

.Tlog 파일의 세 가지 종류가 있습니다: *읽을*, *작성*, 및 *명령줄*. .Tlog 파일 읽기 및 쓰기는 증분 빌드 및 IDE에서 최신 검사에 사용 됩니다. 증분 빌드에서 명령줄.tlog 파일 에서만 사용 됩니다.

MSBuild는 이러한 도우미 클래스를.tlog 파일 읽기 및 쓰기를 제공 합니다.

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

합니다 [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) 읽기 액세스 및.tlog 파일을 작성 하 고, 입력 또는 출력이 없는 경우 출력을 보다 최신인을 식별 하는 클래스를 사용할 수 있습니다. 최신 검사에 사용 됩니다.

명령줄 빌드에 사용 하는 방법에 대 한 정보를 포함 하는 명령줄.tlog 파일입니다. 내부 형식을 생성 하는 MSBuild 태스크에 의해 결정 됩니다 있도록만 증분 빌드를 최신 상태가 아닌 검사에 사용 됩니다.

### <a name="read-tlog-format"></a>읽기.tlog 형식

*읽기* .tlog 파일 (\*.read.\*합니다. tlog) 소스 파일 및 해당 종속성에 대 한 정보를 포함 합니다.

캐럿 ( **^** ) 줄의 시작 부분에 하나 이상의 소스를 나타냅니다. 종속성이 동일한 공유 하는 원본의 세로 막대로 구분 됩니다 ( **\|** ).

종속성 파일 자체 줄에 각 원본 뒤에 나열 됩니다. 모든 파일 이름은 전체 경로입니다.

예를 들어, 프로젝트 소스가 있는 것으로 가정 *f:\\테스트\\ConsoleApplication1\\ConsoleApplication1*합니다. 경우 소스 파일 *Class1.cpp*, 여기에 포함

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

그런 다음 *CL.read.1.tlog* 파일 두 종속 뒤에 소스 파일을 포함 합니다.

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

위 예에서 파일 이름을 작성할 필요가 없습니다 이지만 편의 위해 몇 가지 도구가 있습니다.

### <a name="write-tlog-format"></a>.Tlog 형식 쓰기

*작성할* .tlog (\*.write.\*합니다. tlog) 파일 원본 및 출력에 연결합니다.

캐럿 ( **^** ) 줄의 시작 부분에 하나 이상의 소스를 나타냅니다. 여러 원본 세로 막대로 구분 됩니다 ( **\|** ).

출력 파일 원본에서 빌드된 후 자체 줄에 각 원본에 나열 되어야 합니다. 모든 파일 이름은 전체 경로 여야 합니다.

추가 원본 파일을 지정 된 단순 ConsoleApplication 프로젝트에 대 한 예를 들어 *Class1.cpp*의 *link.write.1.tlog* 파일 포함 될 수 있습니다.

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>디자인 타임 빌드

IDE에서.vcxproj 프로젝트 프로젝트에서 추가 정보를 가져오도록 하는 출력 파일을 다시 생성 MSBuild 대상 집합을 사용 합니다. 이러한 대상 중 일부는 디자인 타임 빌드에 사용만 됩니다 있지만 정기적으로 빌드 및 디자인 타임 빌드를 둘 다에 사용 되는 많은 합니다.

디자인 타임 빌드에 대 한 일반 정보는 CPS 설명서를 참조 하십시오. [디자인 타임 빌드](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)합니다. 이 설명서는만 visual 부분적으로 적용 됩니다 C++ 프로젝트입니다.

합니다 `CompileDesignTime` 및 `Compile` 디자인 타임에 언급 된 대상.vcxproj 프로젝트에 대 한 실행 안 함 설명서를 작성 합니다. Visual C++ .vcxproj 프로젝트 디자인 타임 대상 마다를 사용 하 여 IntelliSense 정보를 얻을 수 있습니다.

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense 정보에 대 한 디자인 타임 대상

.Vcxproj 프로젝트에 사용 되는 디자인 타임 대상에 정의 된 `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*합니다.

`GetClCommandLines` 대상이 수집 IntelliSense에 대 한 컴파일러 옵션:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – 디자인 타임 대상, 디자인 타임에 필요한 초기화를 빌드만 합니다. 무엇 보다도 이러한 대상 성능 향상을 위해 일반적인 빌드 기능 중 일부를 비활성화 합니다.

- `ComputeCompileInputsTargets` – 컴파일러 옵션 및 항목을 수정 하는 대상 집합입니다. 디자인 타임 및 일반 빌드에서 이러한 대상을 실행합니다.

대상 호출을 `CLCommandLine` IntelliSense에 사용할 명령줄을 만들 작업입니다. 마찬가지로 이름과 달리 처리할 수 있습니다 CL 옵션 뿐만 아니라 Clang 및 gcc 옵션도 있습니다. 컴파일러 스위치의 형식에 의해 제어 됩니다는 `ClangMode` 속성입니다.

명령줄에서 생성 되는 현재는 `CLCommandLine` 작업 IntelliSense 엔진은 구문 분석을 쉽게 이기 때문에 (Clang 모드) 에서도 CL 스위치 항상 사용 합니다.

되도록 하는 컴파일 전에 실행 일반 또는 디자인 타임 중단 되지 않습니다 대상을 추가 하는 경우 디자인 타임 빌드 또는 성능에 영향을 줍니다. 대상 테스트 하는 가장 간단한 방법은 다음과 같습니다. 개발자 명령 프롬프트를 열고이 명령을 실행 하려면

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

이 명령은 자세한 빌드 로그를 생성 *msbuild.log*, 대상 및 작업에 대 한 요약 성능 끝에 포함 합니다.

사용 하도록 `Condition ="'$(DesignTimeBuild)' != 'true'"` 만 의미가 있는 디자인 타임 빌드 아닌에 일반 빌드에 대 한 모든 작업에서.

### <a name="design-time-targets-that-generate-sources"></a>소스를 생성 하는 디자인 타임 대상

*이 기능은 기본적으로 네이티브 데스크톱 프로젝트에 대해 비활성화 되 고 캐시 된 프로젝트에서 현재 지원 되지 않습니다*합니다.

경우 `GeneratorTarget` 프로젝트 항목에 대 한 메타 데이터가 정의 되어, 대상이 실행 됩니다 자동으로 모두 프로젝트가 로드 되는 경우 및 원본 파일을 변경 하는 경우.

::: moniker range="vs-2017"

예를 들어.cpp or.h를 자동으로 생성 하려면.xaml 파일에서 파일을 `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0"을 제공*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* 파일 정의 엔터티:

::: moniker-end

::: moniker range=">=vs-2019"

예를 들어.cpp or.h를 자동으로 생성 하려면.xaml 파일에서 파일을 `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v16.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* 파일 정의 엔터티:

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

사용 하도록 `Task.HostObject` 소스 파일의 저장 되지 않은 콘텐츠를 가져오려는 작업 및 대상을로 등록 해야 [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) pkgdef의 지정 된 프로젝트에 대해:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ Visual Studio IDE의 확장성 프로젝트

시각적 개체 C++ 프로젝트 시스템은 기반으로 합니다 [VS 프로젝트 시스템](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md), 및 해당 확장성 지점을 사용 합니다. 프로젝트 계층 구조 구현은 Visual 관련이 있지만 C++ 기반으로 하지 인 하므로 계층 확장성 프로젝트 항목으로 제한 됩니다.

### <a name="project-property-pages"></a>프로젝트 속성 페이지

일반적인 디자인 정보를 참조 하세요 [VC + + 프로젝트의 Framework 멀티 타기 팅](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/)합니다.

간단히 말해에서 속성 페이지에 표시 합니다 **프로젝트 속성** 대화 상자를 C++ 프로젝트에 의해 정의 됩니다 *규칙* 파일입니다. 규칙 파일 속성 페이지에 표시 하 고 프로젝트에 저장 되는 방법과 파일 속성의 집합을 지정 합니다. 규칙 파일은 Xaml 형식을 사용 하는.xml 파일입니다. 직렬화에 사용 된 형식에 설명 되어 있습니다 [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes)합니다. 프로젝트에서 규칙 파일의 사용에 대 한 자세한 내용은 참조 [속성 페이지 XML 규칙 파일](/cpp/build/reference/property-page-xml-files)합니다.

규칙 파일에 추가 되어야 합니다는 `PropertyPageSchema` 항목 그룹:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` 메타 데이터 제한 규칙 표시 유형 규칙 종류를 제어 하 고 다음이 값 중 하나일 수 있습니다.

`Project` | `File` | `PropertySheet`

CPS는 컨텍스트 형식에 대해 다른 값을 지원 하지만 시각적 개체에 사용 되지 않을 C++ 프로젝트입니다.

세미콜론으로 사용 하 여 규칙에 둘 이상의 컨텍스트에 표시 해야 합니다 ( **;** ) 다음과 같이 상황에 맞는 값을 구분 합니다.

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>규칙 형식 및 기본 형식

이 섹션에서는 사용자 인터페이스에서 규칙을 표시 하는 방법에 영향을 주는 특성을 설명 합니다만 있도록 규칙 형식은 간단 합니다.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

합니다 `PageTemplate` 특성은 규칙에 표시 되는 방식을 정의 합니다 **속성 페이지** 대화 합니다. 특성을 다음이 값 중 하나일 수 있습니다.

| 특성 | Description |
|------------| - |
| `generic` | 모든 속성이 범주 머리글 아래에서 한 페이지에 표시 됩니다.<br/>규칙에 대 한 표시 될 수 있습니다 `Project` 하 고 `PropertySheet` 컨텍스트를 아닌 `File`합니다.<br/><br/> 예제: `$(VCTargetsPath)`\\*1033*\\*general.xml* |
| `tool` | 범주는 하위로 표시 됩니다.<br/>규칙이 모든 컨텍스트에 표시 될 수 있습니다: `Project`, `PropertySheet` 고 `File`입니다.<br/>프로젝트 항목이 있는 경우에 규칙은 프로젝트 속성에 표시 합니다 `ItemType` 에 정의 된 `Rule.DataSource`규칙 이름에 포함 되어 있지 않으면는 `ProjectTools` 항목 그룹입니다.<br/><br/>예제: `$(VCTargetsPath)`\\*1033*\\*clang.xml* |
| `debugger` | 페이지는 디버깅 페이지의 일부로 표시 됩니다.<br/>범주는 현재 무시 됩니다.<br/>규칙 이름이 디버그 시작 관리자 MEF 개체의 일치 해야 `ExportDebugger` 특성입니다.<br/><br/>예제: `$(VCTargetsPath)`\\*1033*\\*debugger\_local\_windows.xml* |
| *custom* | 사용자 지정 템플릿입니다. 템플릿의 이름은 일치 해야 합니다는 `ExportPropertyPageUIFactoryProvider` 특성을 `PropertyPageUIFactoryProvider` MEF 개체입니다. See **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> 예제: `$(VCTargetsPath)`\\*1033*\\*userMacros.xml* |

규칙 속성 그리드 기반 템플릿의 하나를 사용 하는 경우 해당 속성에 대 한 이러한 확장 지점을 사용할 수 있습니다.

- [속성 값 편집기](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [동적 열거형 값 공급자](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>규칙 확장

하려는 경우 기존 규칙을 사용 하지만 추가 하거나 제거 하려면 (즉, 숨기기) 만들 수는 몇 가지 속성을 [확장 규칙](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)합니다.

#### <a name="override-a-rule"></a>규칙을 재정의

아마도 설정 해야 할 프로그램 도구 집합 대부분의 프로젝트 기본 규칙을 사용 하려면 하나 또는 그 중 일부를 바꿉니다. 예를 들어, C를 변경 하려는 /C++ 다른 컴파일러 스위치를 표시 하는 규칙입니다. 이름이 같은 새 규칙을 제공 하 고 기존 규칙과 표시 이름 및에 포함 된 `PropertyPageSchema` 가져오기 작업의 기본 cpp 대상 항목 그룹입니다. 프로젝트에서 지정 된 이름의 하나의 규칙만 사용 되 고 마지막에 포함 된 `PropertyPageSchema` 그룹 wins 항목.

#### <a name="project-items"></a>프로젝트 항목

*ProjectItemsSchema.xml* 파일은 정의 `ContentType` 및 `ItemType` 프로젝트 항목으로 처리 되는 항목에 대 한 값 및 정의 `FileExtension` 에 새 파일이 추가 되는 항목 그룹을 결정 하는 요소.

기본 ProjectItemsSchema 파일을 찾을 `$(VCTargetsPath)` \\ *1033*\\*ProjectItemsSchema.xml*합니다. 를 확장 하려면 만들어야 스키마 파일을 새 이름으로 같은 *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

그런 다음 대상 파일에 추가 합니다.

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

예제: `$(VCTargetsPath)`\\*BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>디버거

Visual Studio에서 디버그 서비스 디버그 엔진에 대 한 확장성을 지원합니다. 자세한 내용은 이러한 샘플을 참조 하세요.

- [MIEngine, lldb 디버깅을 지 원하는 오픈 소스 프로젝트](https://github.com/Microsoft/MIEngine)

- [Visual Studio 디버그 엔진 샘플](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

디버그 세션에 대 한 디버그 엔진 및 기타 속성 지정을 구현 해야 합니다는 [디버그 시작 관리자](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) MEF 구성 요소 추가 `debugger` 규칙입니다. 예를 들어 참조 된 `$(VCTargetsPath)` \\1033\\디버거\_로컬\_windows.xml 파일.

### <a name="deploy"></a>배포

.vcxproj 프로젝트 사용에 대 한 Visual Studio 프로젝트 시스템 확장성 [배포 공급자](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)합니다.

### <a name="build-up-to-date-check"></a>최신 검사 빌드

기본적으로 빌드 최신 검사 해야 읽기.tlog 및 쓰기.tlog 파일을 만들 수는 `$(TlogLocation)` 모든 빌드 입력과 출력에 대 한 빌드 폴더입니다.

사용자 지정 최신 검사를 사용 합니다.

1. 추가 하 여 기본 최신 검사를 사용 하지 않도록 설정 합니다 `NoVCDefaultBuildUpToDateCheckProvider` 의 기능을 *Toolset.targets* 파일:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. 사용자 고유의 구현 [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)합니다.

## <a name="project-upgrade"></a>프로젝트 업그레이드

### <a name="default-vcxproj-project-upgrader"></a>기본.vcxproj 프로젝트 업그레이드 프로그램

기본.vcxproj 프로젝트 업그레이 더 변경 합니다 `PlatformToolset`, `ApplicationTypeRevision`, MSBuild 도구 집합 버전 및.Net framework입니다. 마지막 두는 항상 Visual Studio 버전에 대 한 기본값을 변경 하지만 `PlatformToolset` 및 `ApplicationTypeRevision` 특수 MSBuild 속성으로 제어할 수 있습니다.

업그레이 더 이러한 조건을 사용 하 여 여부는 프로젝트를 업그레이드할 수 있는지 여부를 결정 합니다.

1. 정의 하는 프로젝트에 대 한 `ApplicationType` 고 `ApplicationTypeRevision`를 현재 버전 보다 높은 수정 번호를 사용 하 여 폴더가 있습니다.

1. 속성 `_UpgradePlatformToolsetFor_<safe_toolset_name>` 현재 도구 집합에 대해 정의 된 이며 해당 값은 현재 도구 집합을 사용 하 여 같음 없습니다.

   이러한 속성 이름의  *\<safe_toolset_name >* 밑줄로 대체 하는 모든 영숫자가 아닌 문자를 사용 하 여 도구 집합 이름을 나타냅니다 ( **\_** ).

프로젝트를 업그레이드할 수 있는 경우에 참여할 *솔루션 대상 변경*합니다. 자세한 내용은 [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2)합니다.

프로젝트 이름을 표시 하지 않으려면 **솔루션 탐색기** 프로젝트는 특정 도구를 사용 하는 경우 정의 `_PlatformToolsetShortNameFor_<safe_toolset_name>` 속성입니다.

에 대 한 예제 `_UpgradePlatformToolsetFor_<safe_toolset_name>` 및 `_PlatformToolsetShortNameFor_<safe_toolset_name>` 속성 정의 참조 합니다 *Microsoft.Cpp.Default.props* 파일입니다. 사용의 예 참조는 `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* 파일입니다.

### <a name="custom-project-upgrader"></a>사용자 지정 프로젝트 업그레이드 프로그램

사용자 지정 프로젝트 업그레이드 프로그램 개체를 사용 하려면 다음과 같이 MEF 구성 요소를 구현 합니다.

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

코드를 가져오고 기본.vcxproj 업그레이 더 개체를 호출 합니다.

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` 에 정의 된 *Microsoft.VisualStudio.ProjectSystem.VS.dll* 비슷합니다 `IVsRetargetProjectAsync`합니다.

정의 된 `VCProjectUpgraderObjectName` 프로젝트 시스템에서 사용자 지정 업그레이드 프로그램 개체를 사용 하도록 지시 하는 속성:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>프로젝트 업그레이드를 사용 하지 않도록 설정

프로젝트 업그레이드를 사용 하지 않으려면 사용을 `NoUpgrade` 값:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>프로젝트 캐시 및 확장성

큰 작업할 때 성능을 향상 시키기 위해 C++ Visual Studio 2017에서는 솔루션을 [캐시 프로젝트](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) 도입 되었습니다. 프로젝트 데이터를 사용 하 여 채워지고 메모리로 MSBuild 또는 CPS 프로젝트를 로드 하지 않고 프로젝트를 로드 하는 데 다음 SQLite 데이터베이스로 구현 됩니다.

캐시에서 로드.vcxproj 프로젝트에 없는 CPS 개체 이기 때문에 확장의 MEF 구성 요소는 가져올 `UnconfiguredProject` 또는 `ConfiguredProject` 만들 수 없습니다. 확장성을 지원 하도록 프로젝트 캐시는 Visual Studio에서 프로젝트를 사용 하 여 (또는 사용 하 여 가능성이) MEF 확장을 검색 하는 경우 사용 되지 않습니다.

이러한 프로젝트 형식은 항상 완전히 로드 있으며 CPS 개체를 메모리에 있으므로 모든 MEF 확장에 생성 됩니다.

- 시작 프로젝트

- 정의 한 사용자 지정 프로젝트 업그레이드 프로그램에는 프로젝트는 `VCProjectUpgraderObjectName` 속성

- 정의 하지는 데스크톱 Windows를 대상으로 하는 프로젝트는 `ApplicationType` 속성

- 항목 프로젝트 (.vcxitems) 및 모든 프로젝트 참조 하 여 가져오기를.vcxitems 프로젝트는 공유 합니다.

이러한 조건 중 검색 되 면 한 프로젝트 캐시 생성 됩니다. 답변 하는 데 필요한 MSBuild 프로젝트에서 모든 데이터를 포함 하는 캐시 `get` 쿼리가 `VCProjectEngine` 인터페이스입니다. 즉, 모든 수정에 MSBuild props 및 확장에서 수행 하는 대상 파일 수준 캐시에서 로드 되는 프로젝트에서 작동 합니다.

## <a name="shipping-your-extension"></a>배달 확장 프로그램

VSIX 파일을 만드는 방법에 대 한 자세한 내용은 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)합니다. 예를 들어 특별 한 설치 위치에 파일을 추가 하려면, 아래에 있는 파일을 추가 하는 방법에 대 한 내용은 `$(VCTargetsPath)`를 참조 하세요 [extensions 폴더 외부에 설치](../extensibility/set-install-root.md)합니다.

## <a name="additional-resources"></a>추가 자료

Microsoft 빌드 시스템 ([MSBuild](../msbuild/msbuild.md)) 프로젝트 파일에 대 한 빌드 엔진 및 확장 가능한 XML 기반 형식으로 제공 합니다. 에 대해 알고 있어야 basic을 사용한 [MSBuild 개념](../msbuild/msbuild-concepts.md) 고 하는 방법 [시각적 개체에 대해 MSBuild C++ ](/cpp/build/reference/msbuild-visual-cpp-overview) 시각적 개체를 확장 하기 위해 작동 C++ 프로젝트 시스템.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) CPS 및 시각적 개체에서 사용 되는 Api 확장을 제공 C++ 프로젝트 시스템. CPS MEF를 사용 하는 방법의 개요를 참조 하세요 [CPS 및 MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) 에 [VSProjectSystem MEF 개요](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md)합니다.

빌드 단계 또는 새 파일 형식을 추가 하려면 기존 빌드 시스템을 사용자 지정할 수 있습니다. 자세한 내용은 [MSBuild (Visual C++) 개요](/cpp/build/reference/msbuild-visual-cpp-overview) 하 고 [프로젝트 속성 작업](/cpp/build/working-with-project-properties)합니다.
