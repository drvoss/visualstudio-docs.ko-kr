---
title: Live Unit Testing FAQ
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 41d5248106b831accf4d71f97aeaeb72fdbc5018
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68662017"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing 질문과 대답

## <a name="latest-features"></a>최신 기능

**Live Unit Testing은 정기적으로 개선 및 향상됩니다. 최신의 새로운 기능과 향상된 기능에 대한 정보를 어떻게 찾을 수 있나요?**

Live Unit Testing의 적용된 새로운 기능과 향상된 기능에 대한 자세한 내용은 [Live Unit Testing의 새로운 기능](live-unit-testing-whats-new.md)을 참조하세요.

## <a name="supported-frameworks-and-versions"></a>지원되는 프레임워크 및 버전

**Live Unit Testing에서 지원하는 테스트 프레임워크와 지원되는 최소 버전은 어떻게 되나요?**

Live Unit Testing은 다음 테이블에 나열된 세 가지 인기 있는 단위 테스트 프레임워크를 사용합니다. 해당 어댑터와 프레임워크를 지원하는 최소 버전은 테이블에 나열됩니다. 단위 테스트 프레임워크는 NuGet.org에서 모두 사용할 수 있습니다.

|테스트 프레임워크  |Visual Studio 어댑터 최소 버전  |프레임워크 최소 버전  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio 버전 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter 버전 3.7.0 |NUnit 버전 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-미리 보기 |MSTest.TestFramework 1.0.5-미리 보기 |

`Microsoft.VisualStudio.QualityTools.UnitTestFramework`를 참조하는 이전 MSTest 기반 테스트 프로젝트가 있고 최신 MSTest NuGet 패키지로 이동하지 않으려면 Visual Studio 2017 버전 15.4 이상으로 업그레이드하세요.

경우에 따라 Live Unit Testing이 작동하기 위해 솔루션의 프로젝트에서 참조하는 NuGet 패키지를 명시적으로 복원해야 합니다. 솔루션의 명시적 빌드를 수행하거나(최상위 Visual Studio 메뉴에서 **빌드**, **솔루션 다시 빌드**를 선택) 또는 Living Unit Testing을 활성화하기 전에 솔루션을 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 복원**을 선택해서 패키지를 복원합니다.

## <a name="net-core-support"></a>.NET Core 지원

**Live Unit Testing은 .NET Core와 호환되나요?**

예. Live Unit Testing은 .NET Core 및 .NET Framework와 호환됩니다. Visual Studio 2017 버전 15.3에서 .NET Core 지원이 추가되었습니다. .NET Core에 대한 Live Unit Testing 지원이 필요한 경우 이 버전 이상의 Visual Studio로 업그레이드합니다.

## <a name="configuration"></a>구성

**Live Unit Testing을 설정해도 작동하지 않는 이유는 무엇인가요?**

**출력 창**(Live Unit Testing 드롭다운을 선택한 경우)은 Live Unit Testing이 작동하지 않는 이유를 설명합니다. 다음과 같은 이유로 Live Unit Testing이 작동하지 않을 수 있습니다.

- 솔루션의 프로젝트에서 참조하는 NuGet 패키지가 복원되지 않은 경우 Live Unit Testing은 작동하지 않습니다. Live Unit Testing을 설정하기 전에 솔루션을 명시적으로 빌드하거나 솔루션의 NuGet 패키지를 복원하면 이 문제가 해결되어야 합니다.

- 프로젝트에서 MSTest 기반 테스트를 사용하는 경우 `Microsoft.VisualStudio.QualityTools.UnitTestFramework`에 대한 참조를 제거하고 최신 MSTest NuGet 패키지, `MSTest.TestAdapter`(1.1.11의 최소 버전 필요) 및 `MSTest.TestFramework`(1.1.11의 최소 버전 필요)에 대한 참조를 추가해야 합니다. 자세한 내용은 [Visual Studio에서 Live Unit Testing 사용](live-unit-testing.md#supported-test-frameworks) 문서의 "지원되는 테스트 프레임워크" 섹션을 참조하세요.

- 솔루션에 있는 하나 이상의 프로젝트에는 NuGet 참조 또는 xUnit, NUnit 또는 MSTest 테스트 프레임워크에 대한 직접 참조가 있어야 합니다. 이 프로젝트도 해당하는 Visual Studio 테스트 어댑터 NuGet 패키지를 참조해야 합니다. Visual Studio 테스트 어댑터는 *.runsettings* 파일을 통해 참조될 수도 있습니다. *.runsettings* 파일에는 다음 예제 같은 항목이 있어야 합니다.

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>업그레이드 후 검사가 올바르지 않음

**Visual Studio 프로젝트에서 참조되는 테스트 어댑터를 지원되는 버전으로 업그레이드한 후 Live Unit Testing에 잘못된 검사가 표시되는 이유는 무엇인가요?**

- 솔루션의 여러 프로젝트에서 NuGet 테스트 어댑터 패키지를 참조하는 경우 각 프로젝트를 지원되는 버전으로 업그레이드해야 합니다.

- 또한 테스트 어댑터 패키지에서 가져온 MSBuild *.props* 파일이 올바르게 업데이트되었는지 확인합니다. 다음과 같이 일반적으로 프로젝트 파일의 위쪽에 있는 가져오기의 NuGet 패키지 버전/경로를 확인합니다.

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>빌드 사용자 지정

**내 Live Unit Testing 빌드를 사용자 지정할 수 있나요?**

"일반적인" 계측되지 않은 빌드에 필요하지 않은 계측(Live Unit Testing)을 위해 빌드하는 사용자 지정 단계가 솔루션에 필요한 경우 프로젝트 또는 *.targets* 파일에 코드를 추가하여 `BuildingForLiveUnitTesting` 속성에 대해 확인하고 사용자 지정 사전/사후 빌드 단계를 수행할 수 있습니다. 또한 특정 빌드 단계(예: 패키지 게시 또는 생성)을 제거하거나 빌드 단계(예: 필수 구성 요소 복사)를 이 프로젝트 속성을 기반으로 하는 Live Unit Testing 빌드에 추가할 수 있습니다. 이 속성을 기반으로 빌드를 사용자 지정하면 일반적인 빌드를 변경하지 않고 Live Unit Testing 빌드에만 영향을 줍니다.

예를 들어 일반적인 빌드 중에 NuGet 패키지를 생성하는 대상이 있을 수 있습니다. 아마도 편집을 모두 완료한 후에 NuGet 패키지를 생성하려고 하지는 않을 것입니다. 따라서 다음과 같은 작업을 실행하여 Live Unit Testing 빌드에서 해당 대상을 해제할 수 있습니다.  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>&lt;OutputPath&gt; 또는 &lt;OutDir&gt;을 포함한 오류 메시지

**Live Unit Testing이 내 솔루션을 빌드하려고 하는 경우 다음 오류가 표시되는 이유는 무엇인가요? “무조건 `<OutputPath>` 또는 `<OutDir>`으로 설정된 것으로 보입니다. Live Unit Testing은 출력 어셈블리에서 테스트를 실행하지 않습니다.”**

솔루션에 대한 빌드 프로세스가 무조건 `<OutputPath>` 또는 `<OutDir>`를 재정의하는 경우에 이 오류가 발생할 수 있습니다. 따라서 `<BaseOutputPath>`의 하위 디렉터리가 아닙니다. 이러한 경우에 빌드 아티팩트가 `<BaseOutputPath>` 아래의 폴더에 배치되도록 이러한 값을 재정의하기 때문에 Live Unit Testing은 작동하지 않습니다. 빌드 아티팩트를 일반적인 빌드에 배치하는 위치를 재정의해야 하는 경우 `<BaseOutputPath>`에 따라 조건부로 `<OutputPath>`를 재정의합니다.

예를 들어 다음과 같이 빌드가 `<OutputPath>`를 재정의하는 경우:

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

그러면 다음 XML로 바꿀 수 있습니다.

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

그렇게 하면 `<OutputPath>`은 `<BaseOutputPath>` 폴더 내에 위치합니다.

`<OutDir>`를 빌드 프로세스에서 직접 재정의하지 않습니다. 특정 위치에 빌드 아티팩트를 배치하는 대신 `<OutputPath>`를 재정의합니다.

## <a name="set-the-location-of-build-artifacts"></a>빌드 아티팩트의 위치 설정

**Live Unit Testing 빌드 아티팩트를 원하는 *.vs* 폴더의 기본 위치 대신 특정 위치로 이동하려고 합니다. 어떻게 변경할 수 있나요?**

`LiveUnitTesting_BuildRoot` 사용자 수준 환경 변수를 Live Unit Testing 빌드 아티팩트를 배치하려는 경로로 설정합니다. 

## <a name="test-explorer-vs-live-unit-testing-test-runs"></a>테스트 탐색기 및 Live Unit Testing 테스트 실행

**테스트 탐색기 창에서 테스트를 실행하는 것과 Live Unit Testing에서 테스트를 실행하는 것은 어떻게 다른가요?**

다음과 같은 몇 가지 차이점이 있습니다.

- **테스트 탐색기** 창에서 테스트를 실행 또는 디버깅하면 일반 이진 파일을 실행합니다. 반면 Live Unit Testing은 계측된 이진 파일을 실행합니다. 계측된 이진 파일을 디버그하려는 경우 테스트 메서드에서 [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch)  메서드 호출을 추가하면 해당 메서드가 실행될 때(Live Unit Testing에서 실행하는 경우 포함)마다 디버거가 시작되고 계측된 이진 파일을 연결하고 디버그할 수 있습니다. 그러나 계측이 대부분의 사용자 시나리오에 대해 투명하고 계측된 이진 파일을 디버그할 필요가 없는 것이 좋습니다.

- Live Unit Testing은 테스트를 실행하기 위해 새 애플리케이션 도메인을 만들지 않지만 **테스트 탐색기** 창에서 실행되는 테스트는 새 애플리케이션 도메인을 만듭니다.

- Live Unit Testing은 각 테스트 어셈블리에서 순차적으로 테스트를 실행합니다. **테스트 탐색기** 창에서 여러 테스트를 병렬로 실행하도록 선택할 수 있습니다.

- Live Unit Testing에서 테스트를 검색하고 실행하려면 `TestPlatform`의 버전 2를 사용하는 반면 **테스트 탐색기** 창은 버전 1을 사용합니다. 그러나 대부분의 경우에는 차이를 알 수 없습니다.

- 현재 **테스트 탐색기**는 기본적으로 STA(단일 스레드 아파트)에서 실행되는 반면 Live Unit Testing은 MTA(다중 스레드 아파트)에서 테스트를 실행합니다. Live Unit Testing의 STA에서 MSTest 테스트를 실행하려면 `MSTest.STAExtensions 1.0.3-beta`에서 찾을 수 있는 `<STATestMethod>` 또는 `<STATestClass>` 특성을 사용하여 NuGet 패키지 테스트 메서드 또는 포함한 클래스를 데코레이트합니다. NUnit의 경우 테스트 메서드를 `<RequiresThread(ApartmentState.STA)>` 특성을 사용하여 데코레이트하고 xUnit의 경우 `<STAFact>` 특성을 사용하여 데코레이트합니다.

## <a name="exclude-tests"></a>테스트 제외

**Live Unit Testing에 참여하지 않도록 테스트를 제외하려면 어떻게 할까요?**

사용자 지정 설정은 [Visual Studio에서 Live Unit Testing 사용](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) 문서의 "테스트 프로젝트 및 테스트 메서드 포함 및 제외" 섹션을 참조하세요. 테스트 포함 또는 제외는 특정 편집 세션에 특정 집합의 테스트를 실행하거나 고유한 개인 기본 설정을 유지하려는 경우에 유용합니다.

솔루션 지정 설정은 Live Unit Testing에서 계측한 메서드, 속성, 클래스 또는 구조를 제외하여 프로그래밍 방식으로 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> 특성을 적용할 수 있습니다. 또한 프로젝트 파일에서 `<ExcludeFromCodeCoverage>` 속성을 `true`로 설정하여 전체 프로젝트를 계측하지 않도록 제외할 수도 있습니다. Live Unit Testing은 계측되지 않는 테스트를 실행하지만 해당 검사를 시각화할 수는 없습니다.

`Microsoft.CodeAnalysis.LiveUnitTesting.Runtime`이 현재 애플리케이션 도메인에 로드되고 원인에 따라 테스트를 사용하지 않도록 설정하는지 여부를 확인할 수도 있습니다. 예를 들어 xUnit을 사용하여 다음과 같은 작업이 가능합니다.

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="win32-pe-headers"></a>Win32 PE 헤더

**Win32 PE 헤더가 Live Unit Testing에서 빌드한 계측된 어셈블리와 다른 이유는 무엇인가요?**

이 문제는 해결되었으며 Visual Studio 2017 버전 15.3 이상에서는 없습니다.

이전 버전의 Visual Studio 2017에서는 알려진 버그로 인해 Live Unit Testing 빌드가 다음 Win32 PE 헤더 데이터를 포함하는 데 실패할 수 있습니다.

- 파일 버전(코드에서 @System.Reflection.AssemblyFileVersionAttribute 로 지정됨)

- Win32 아이콘(명령줄에서 `/win32icon:`로 지정됨)

- Win32 매니페스트(명령줄에서 `/win32manifest:`로 지정됨)

이러한 값을 사용하는 테스트를 Live Unit testing에서 실행하는 경우 실패할 수 있습니다.

## <a name="continuous-builds"></a>연속 빌드

**편집하지 않은 경우에도 Live Unit Testing에서 내 솔루션을 계속 빌드하는 이유는 무엇인가요?**

솔루션의 빌드 프로세스가 솔루션 자체의 일부인 소스 코드를 생성하고 빌드 대상 파일에 적절한 입력 및 출력이 지정되지 않은 경우 편집하지 않더라도 솔루션을 빌드할 수 있습니다. 대상에는 입력 및 출력의 목록이 지정되었으므로 MSBuild는 적절한 최신 검사를 수행하고 새 빌드가 필요한지 여부를 확인할 수 있습니다.

Live Unit Testing은 원본 파일이 변경되었음을 감지할 때마다 빌드하기 시작합니다. 솔루션의 빌드가 원본 파일을 생성하기 때문에 Live Unit Testing은 빌드 무한 루프로 진행됩니다. 그러나 (이전 빌드에서 새로 생성된 원본 파일을 감지한 후에) Live Unit Testing에서 두 번째 빌드를 시작하는 시기를 대상의 입력 및 출력이 확인하면 입력 및 출력 검사는 모든 항목이 최신 상태라고 표시하기 때문에 빌드 루프를 중단시킵니다.  

## <a name="new-process-coverage"></a>새 프로세스 검사

**Live Unit Testing이 테스트에서 만든 새 프로세스의 검사를 캡처하지 않는 이유는 무엇인가요?**

이는 알려진 문제이며 후속 릴리스에서 수정해야 합니다.

## <a name="including-or-excluding-tests-doesnt-work"></a>테스트 포함 또는 제외가 작동하지 않음

**라이브 테스트 집합에서 테스트를 포함하거나 제외한 후에 아무것도 발생하지 않은 이유는 무엇인가요?**

이 문제는 해결되었으며 Visual Studio 2017 버전 15.3 이상에서는 없습니다.

이것은 Visual Studio 2017의 이전 버전에서 알려진 문제입니다. 이 문제를 해결하기 위해 테스트를 포함하거나 제외한 후에 모든 파일을 편집해야 합니다.

## <a name="editor-icons"></a>편집기 아이콘

**Live Unit Testing이 출력 창의 메시지를 기반으로 한 테스트를 실행하는 것처럼 보이는데 편집기에서 아이콘을 확인할 수 없는 이유는 무엇인가요?**

Live Unit Testing이 작동하는 어셈블리가 어떤 이유로든 계측되지 않는 경우 편집기에서 아이콘이 표시되지 않습니다. 예를 들어 Live Unit Testing은 `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`로 설정된 프로젝트와 호환되지 않습니다. 이 경우에 Live Unit Testing이 작동하기 위해 이 설정을 제거하거나 `true`로 변경하도록 빌드 프로세스를 업데이트해야 합니다. 

## <a name="capture-logs"></a>캡처 로그

**파일 버그 보고서에 대한 자세한 로그를 수집하려면 어떻게 할까요?**

자세한 로그를 수집하려면 몇 가지 작업을 수행할 수 있습니다.

- **도구** > **옵션** > **Live Unit Testing**으로 이동하여 로깅 옵션을 **자세한 정보**로 변경합니다. 자세한 정보 로깅을 사용하면 **출력** 창에 자세한 로그가 표시됩니다.

- `LiveUnitTesting_BuildLog` 사용자 환경 변수를 MSBuild 로그를 캡처하는 데 사용하려는 파일의 이름으로 설정합니다. Live Unit Testing 빌드의 자세한 MSBuild 로그 메시지를 해당 파일에서 검색할 수 있습니다.

- `LiveUnitTesting_TestPlatformLog` 사용자 환경 변수를 `1`로 설정하여 테스트 플랫폼 로그를 캡처합니다. Live Unit Testing의 자세한 테스트 플랫폼 로그 메시지를 `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`에서 검색할 수 있습니다.

- `VS_UTE_DIAGNOSTICS`이라는 사용자 수준 환경 변수를 만들고 1(또는 다른 값)로 설정한 다음 Visual Studio를 다시 시작합니다. 이제 Visual Studio의 **출력 - 테스트** 탭에서 여러 로깅이 표시됩니다.

## <a name="see-also"></a>참고 항목

- [유닛 테스트](live-unit-testing.md)
