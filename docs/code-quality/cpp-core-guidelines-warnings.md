---
title: C++Core 지침 경고
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 002a82143ca30e87a8e83f3e7e4b7217ab677f11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822502"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Core Guidelines를 이용한 코드검사 사용

C++ Core Guidelines는 이식 가능한 집합 지침, 규칙 및 C++ 전문가가 및 디자이너에서 생성하는 C++에서 코딩 하는 방법에 대 한 모범 사례입니다. Visual Studio는 현재 C++용 코드 분석 도구의 일부로 이러한 규칙의 하위 집합을 지원합니다. 핵심 지침 검사기는 Visual Studio 2017 및 Visual Studio 2019에 기본적으로 설치 되며 [Visual Studio 2015 용 NuGet 패키지로 제공](#vs2015_corecheck)합니다.

## <a name="the-c-core-guidelines-project"></a>C++ Core Guidelines 프로젝트

C++ Core Guidelines를 안전 하 게 하 고 효과적으로 최신 C++를 사용 하는 데는 Bjarne Stroustrup 등에서 생성 합니다. 지침에는 정적 형식 안전성 및 리소스 보안 강조합니다. 제거 하거나 언어의 가장 오류가 발생 하기 쉬운 부분을 최소화 하는 방법을 식별 하며 신뢰할 수 있는 방식으로 코드를 간단 하 게 하는 방법 및 성능이 향상 하는 것이 좋습니다. 이러한 지침 표준 C++ Foundation에서 유지 됩니다. 자세한 내용은 설명서를 참조 [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), C++ Core Guidelines 설명서 프로젝트 파일에 액세스 하고 [GitHub](https://github.com/isocpp/CppCoreGuidelines)합니다.

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>코드 분석에서 C++ Core Check 지침을 사용 하도록 설정

선택 하 여 프로젝트에서 코드 분석을 사용할 수 있습니다를 **빌드에 코드 분석 사용** 에서 확인란을 선택 합니다 **코드 분석** 섹션을 **속성 페이지** 대화 상자 프로젝트입니다.

![코드 분석 일반 설정에 대한 속성 페이지](../code-quality/media/cppcorecheck_codeanalysis_general.png)

C++ Core Check 규칙은 기본 확장 집합 때 실행 하는 코드 분석 규칙을 사용 하도록 설정 합니다. 때문에 C++ Core Check 규칙 개발은, 몇 가지 규칙은 잘 확립 된 및 일부 모든 코드에 대 한 사용할 준비가 되지 않을 수 있습니다 하지만 여전히 없을 수 정보를 제공 합니다. 규칙은 두 개의 그룹으로 나뉩니다: 출시 되 고 실험적입니다. 프로젝트 속성에서 해제 또는 실험적 규칙을 실행할 것인지를 선택할 수 있습니다.

![코드 분석 확장 설정에 대 한 속성 페이지](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

C++ Core Check 규칙 집합을 사용 하지 않도록 설정 하거나, 엽니다는 **속성 페이지** 프로젝트 대화 상자. 아래 **구성 속성**를 확장 하 고 **코드 분석**를 **확장**합니다. 드롭다운 목록 옆에 제어할 **사용 C++ Core Check (릴리스)** 또는 **사용 C++ Core Check (실험적)**, 선택 **예** 또는 **아니요**합니다. 선택 **확인** 하거나 **적용** 변경 내용을 저장 합니다.

## <a name="examples"></a>예제

C++ Core Check 규칙을 찾을 수 있는 문제 중 일부는 다음과 같습니다.

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

이 예제에서는 C++ Core Check 규칙을 찾을 수 있는 경고의 일부를 보여 줍니다.

- C26494 규칙 하세요 (type.5 같습니다. 항상 개체를 초기화 합니다.

- C26485 규칙 Bounds.3 같습니다. 배열-포인터 decay 없습니다.

- C26481 규칙 합니다 (bounds.1 같습니다. 포인터 산술 연산을 사용 하지 마세요. 대신 `span`를 사용하세요.

C++ Core Check 코드 분석 규칙 집합은를 설치 하 고이 코드를 컴파일할 때 사용 하도록 설정 하는 경우 처음 두 개의 경고를 출력 하지만 세 번째 표시 되지 않습니다. 빌드 출력에서 예제 코드는 다음과 같습니다.

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ Core Guidelines 향상하고 안전한 코드를 작성할 수 있도록 하는 것입니다. 그러나 규칙 또는 프로필을 적용 하지 않아야 되는 인스턴스가 있을 경우 쉽습니다 표시 하지 않으려면 코드에서 직접. 사용할 수는 `gsl::suppress` 특성을 검색 하 고 다음 코드 블록에서 규칙의 위반을 보고에서 C++ Core Check를 유지 합니다. 특정 규칙을 표시 하지 않으려면 개별 문을 표시할 수 있습니다. 작성하여 전체 범위 프로필도 억제할 수 있습니다 `[[gsl::suppress(bounds)]]` 특정 규칙 수를 포함 하지 않고 있습니다.

## <a name="supported-rule-sets"></a>지원 되는 규칙 집합

새 규칙은 C++ 핵심 지침 검사기에 추가 되 면 기존 코드에 대 한 생성 되는 경고 수가 늘어날 수 있습니다. 사용 하도록 설정 하는 규칙의 종류를 필터링 하려면 미리 정의 된 규칙 집합을 사용할 수 있습니다. Visual Studio 2017 버전 15.3부터 지원 되는 규칙 집합은 됩니다.

- **소유자 포인터 규칙** 적용 [소유자와 관련 된 리소스 관리 검사\<T >에서 C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)합니다.

- **Const 규칙** 적용 [C++ Core Guidelines의 const 관련 검사](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)합니다.

- **원시 포인터 규칙** 적용 [리소스 관리 검사 C++ Core Guidelines에서 원시 관련이 포인터](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)합니다.

- **고유 포인터 규칙** 적용 [C++ Core Guidelines에서 고유 포인터 의미 체계를 사용 하는 형식 관련 리소스 관리 검사](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)합니다.

- **범위 규칙** 적용 된 [프로필은 C++ Core Guidelines의 범위](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)합니다.

- **형식 규칙** 적용 된 [프로필은 C++ Core Guidelines의 입력](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)합니다.

하나 또는 그룹의 몇 가지 경고를 제한할 수 있습니다. **네이티브 최소** 하 고 **네이티브 권장** 집합 기타 PREfast 검사 하는 것 외에도 C++ Core Check 규칙을 포함 하는 규칙입니다. 사용 가능한 규칙 집합, 프로젝트 속성 대화 상자를 열고 보려면를 선택 **코드 Analysis\General**, 열에서 드롭다운 합니다 **규칙 집합** 콤보 상자 및 선택 **여러 규칙 집합 선택** . Visual Studio에서 규칙 집합을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [코드 분석 규칙 그룹화를 사용 하 여 규칙 집합](using-rule-sets-to-group-code-analysis-rules.md)합니다.

## <a name="macros"></a>매크로

C++ 핵심 지침 검사기 전체 범주의 코드에서 경고를 표시 하지 않으려면 쉽게 해 주는 매크로 정의 하는 헤더 파일을 함께 제공 됩니다.

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

이러한 매크로 규칙 집합에 해당 하 고 경고 번호를 공백으로 구분 된 목록으로 확장 합니다. 적절 한 pragma 구문을 사용 하 여 프로젝트에 대 한 흥미로운 인 유효 규칙 집합 또는 코드 부분을 구성할 수 있습니다. 다음 예제에서는 코드 분석만 상수 한정자를 누락 하는 방법에 대 한 경고는:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>특성

Microsoft Visual C++ 컴파일러는 특성을 표시 하지 않으려면는 GSL 지원을 제한 합니다. 식 및 함수 내에서 블록 문에 대한 경고를 표시 하지 않으려면 사용할 수 있습니다.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>명령줄 옵션을 사용 하 여 분석을 표시 하지 않기

대신 #pragmas, 프로젝트 또는 단일 파일에 대 한 경고를 표시 하지 않으려면 파일의 속성 페이지에서 명령줄 옵션을 사용할 수 있습니다. 예를 들어 경고를 사용 하지 않도록 설정 하는 파일에 대 한 26400:

1. 파일을 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**

2. 선택 **속성 | C/C++ | 명령줄**

3. 에 **추가 옵션** 창에서 추가 `/wd26400`합니다.

명령줄 옵션을 사용 하 여 일시적으로 파일에 대 한 모든 코드 분석을 사용 하지 않도록 지정 하 여 `/analyze-`입니다. 경고가 생성 됩니다 *D9025 재정의 '/analyze'와 ' /analyze-'*, 다시 나중에 코드 분석을 사용 하도록 알림을 합니다.

## <a name="corecheck_per_file"></a> 사용 하도록 설정 합니다 C++ 특정 프로젝트 파일의 핵심 지침 검사기

경우에 따라 수행 중심 코드 분석을 계속 활용 하 여 Visual Studio IDE 유용할 수 있습니다. 다음은 빌드 시간을 저장 하 고 필터 결과를 쉽게 대규모 프로젝트에 사용할 수 있는 샘플 시나리오입니다.

1. 명령 셸에서 다음을 설정 합니다 `esp.extension` 및 `esp.annotationbuildlevel` 환경 변수입니다.
2. 이러한 변수를 상속 하도록 명령 셸에서 Visual Studio를 엽니다.
3. 프로젝트를 로드 하 고 해당 속성을 엽니다.
4. 코드 분석을 사용 하도록 설정 하 고, 적절 한 규칙 집합을 선택 하지만 코드 분석 확장을 사용 하지 마세요.
5. C++ 핵심 지침 검사기를 사용 하 여 분석 하 고 해당 속성을 열고 파일이 있는 위치로 이동 합니다.
6. 선택할 **C /C++명령줄 옵션 \Command** 추가 `/analyze:plugin EspXEngine.dll`
7. 미리 컴파일된 헤더 사용 하지 않도록 설정 (**C /C++헤더 \Precompiled**). 왜냐하면 필요한 경우 후자를 사용 하 여 컴파일된 기본 프로젝트 옵션,이 호환 되지 및 확장 엔진이 미리 컴파일된 헤더에서 해당 내부 정보를 읽을 하려고 할 수 있습니다.
8. 프로젝트를 다시 빌드합니다. 모든 파일에 일반 PREFast 검사를 실행 해야 합니다. 때문에 C++ 를 사용 하도록 구성 되는 파일에만 실행할지, 기본적으로 핵심 지침 검사기 사용 되지 않습니다.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Visual Studio 외부에서 C++ 핵심 지침 검사기를 사용 하는 방법
자동화 된 빌드에 C++ Core Guidelines 검사를 사용할 수 있습니다.

### <a name="msbuild"></a>MSBuild

네이티브 코드 분석 검사기 (PREfast)를 사용 하는 사용자 지정 대상 파일에서 MSBuild 환경에 통합 됩니다. 프로젝트 속성을 사용하여 사용 하도록 설정 하 고 (PREfast 기반)는 C++ 핵심 지침 검사기를 추가할 수 있습니다.

```xml
<PropertyGroup>
  <EnableCppCoreCheck>true</EnableCppCoreCheck>
  <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
  <RunCodeAnalysis>true</RunCodeAnalysis>
</PropertyGroup>
```

Microsoft.Cpp.targets 파일을 가져오기 전에 이러한 속성을 추가 했는지 확인 하십시오. 특정 규칙 집합을 선택 지정 또는 사용자 지정 규칙 집합 만들기 또는 기타 PREfast 검사를 포함 하는 기본 규칙 집합을 사용 합니다.

와 동일한 방식으로 사용하여 C++ Core Checker 지정 된 파일에 대해서만 실행할 수 있습니다 [앞에서 설명한](#corecheck_per_file), 하지만 MSBuild 파일을 사용 합니다. 환경 변수를 사용 하 여 설정할 수는 `BuildMacro` 항목:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

프로젝트 파일을 수정 하지 않으려는 경우에 명령줄에서 속성을 전달할 수 있습니다.

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>비 MSBuild 프로젝트
MSBuild에 종속 되지 않는 빌드 시스템을 사용 하는 경우 검사기를 실행할 수 있습니다 하지만 (나중에 지원 되는 데는 보장 되지 않습니다)는 코드 분석 엔진 구성의 일부 내부에 익숙해지려면 해야 합니다.

몇 가지 환경 변수를 설정 하 고 컴파일러에 대 한 적절 한 명령줄 옵션을 사용 해야 합니다. 컴파일러에 대한 특정 경로 대한 검색, 디렉터리 등을 포함할 필요가 없습니다 있도록 "네이티브 도구 명령 프롬프트" 환경에서 작동 하는 것이 좋습니다.

1. **환경 변수**
   - `set esp.extensions=cppcorecheck.dll` 이 C++ Core Guidelines 모듈을 로드 하도록 엔진에 지시 합니다.
   - `set esp.annotationbuildlevel=ignore` 이 논리 SAL 주석 처리 하는 사용 하지 않도록 설정 합니다. 주석을 코드 분석에 영향을 주지 않습니다는 C++ 핵심 지침 검사기, 아직 처리는 해당 시간 (경우에 따라 시간이 많이). 이 설정은 선택 사항 이지만 권장 됩니다.
   - `set caexcludepath=%include%` 표준 헤더에서 발생 하는 경고를 사용 하지 않도록 설정 하는 것이 좋습니다. 여기에서 자세한 경로 경로 예를 들어 프로젝트에서 일반적인 헤더를 추가할 수 있습니다.
2. **명령줄 옵션**
   - `/analyze`  코드 분석을 활성화 (/analyze도 사용 하는 것이 좋습니다:만 및 /analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` 이 옵션은 PREfast에 코드 분석 확장 엔진을 로드 합니다. 이 엔진을 C++ 핵심 지침 검사기를 차례로 로드합니다.

## <a name="use-the-guideline-support-library"></a>지침 지원 라이브러리를 사용 합니다.

지침 지원 라이브러리는 핵심 지침을 따를 수 있도록 설계 되었습니다. GSL 오류가 구문 보다 안전한 대체 항목으로 대체할 수 있도록 정의 포함 합니다. 예를 들어 바꿀 수 있습니다는 `T*, length` 쌍을 사용 하 여 매개 변수는 `span<T>` 형식입니다. 제공 되는 GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl)합니다. 라이브러리는 오픈 소스는 원본을 보려면, 메모 추가 하거나 기여할 수 있습니다. 프로젝트를 찾을 수 있습니다 [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)합니다.

## <a name="vs2015_corecheck"></a> 사용 된 C++ Visual Studio 2015 프로젝트에서 핵심 확인 지침

Visual Studio 2015를 사용 하는 경우 C++ Core Check 코드 분석 규칙 집합 기본적으로 설치 되지 않습니다. Visual Studio 2015의 C++ Core Check 코드 분석 도구를 사용 하려면 먼저 몇 가지 추가 단계를 수행 해야 합니다. Microsoft는 Nuget 패키지를 사용 하 여 Visual Studio 2015 프로젝트에 대 한 지원을 제공 합니다. 패키지의 이름은 Microsoft.CppCoreCheck, 및에서 사용할 수 있습니다 [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck)합니다. 이 패키지는 최신 Visual Studio 2015 업데이트 1을 사용 하 여 설치 해야 해야 합니다.

또한 패키지는 헤더만 지침 지원 라이브러리 (GSL) 종속성으로 다른 패키지를 설치합니다. GSL에서 GitHub에서 사용할 수 있는 이기도 [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)합니다.

코드 분석 규칙 로드 되는 방식으로 인해 Visual Studio 2015 내에서 확인 하려는 각 C++ 프로젝트로 Microsoft.CppCoreCheck NuGet 패키지를 설치 해야 합니다.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Visual Studio 2015에서 프로젝트에 Microsoft.CppCoreCheck 패키지를 추가 하려면

1. **솔루션 탐색기**, 패키지를 추가 하려면 솔루션에서 프로젝트의 상황에 맞는 메뉴를 열려면 마우스 오른쪽 단추로 클릭 합니다. 선택할 **NuGet 패키지 관리** 열려는 합니다 **NuGet 패키지 관리자**합니다.

2. 에 **NuGet 패키지 관리자** 창, Microsoft.CppCoreCheck 검색 합니다.

    ![Nuget 패키지 관리자 창을 CppCoreCheck 패키지를 보여 줍니다.](../code-quality/media/cppcorecheck_nuget_window.png)

3. Microsoft.CppCoreCheck 패키지를 선택 하 고 다음을 선택 합니다 **설치** 프로젝트에 규칙을 추가 하려면 단추입니다.

   NuGet 패키지를 프로젝트에서 코드 분석을 활성화할 때 호출 되는 프로젝트에 추가 MSBuild.targets 파일을 추가 합니다. .Targets 파일을이 Visual Studio 코드 분석 도구에 추가 확장으로 C++ Core Check 규칙을 추가합니다. 패키지를 설치할 때에 출시되고 실험적 규칙을 사용할지 여부를 속성 페이지 대화 상자를 사용할 수 있습니다.
