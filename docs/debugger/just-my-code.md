---
title: 내 코드만를 사용 하 여 사용자 코드 디버그 | Microsoft Docs
ms.date: 02/13/2019
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c1d474b388dd8f116eb53febb8a472d4c5b8150
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536002"
---
# <a name="debug-only-user-code-with-just-my-code"></a>내 코드만를 사용 하 여 사용자 코드 디버그

*내 코드만* 는 시스템, 프레임 워크 및 기타 사용자가 아닌 코드에 대 한 호출을 자동으로 한 단계씩 수행 하는 Visual Studio 디버깅 기능입니다. **호출 스택** 창에서 이러한 호출을 **[External Code]** 프레임으로 축소 내 코드만 합니다.

내 코드만는 .NET, C++및 JavaScript 프로젝트에서 다르게 작동 합니다.

## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> 내 코드만 사용 또는 사용 안 함

대부분의 프로그래밍 언어에서 내 코드만은 기본적으로 사용 하도록 설정 되어 있습니다.

- Visual Studio에서 내 코드만를 사용 하거나 사용 하지 않도록 설정 하려면 **도구**  > **옵션** (또는 **디버그**  > **옵션**)에서 **디버깅**  > **일반**으로 > **사용**을 선택 하거나 선택 취소 합니다.

![옵션 대화 상자에서 내 코드만 사용](../debugger/media/dbg_justmycode_options.png "내 코드만 사용")

> [!NOTE]
> **내 코드만 사용** 은 모든 언어의 모든 Visual Studio 프로젝트에 적용 되는 전역 설정입니다.

## <a name="just-my-code-debugging"></a>내 코드만 디버깅

디버깅 세션 중에 **모듈** 창에는 디버거가 내 코드 (사용자 코드)로 처리 하는 코드 모듈과 해당 기호 로딩 상태를 보여 줍니다. 자세한 내용은 [디버거를 앱에 연결 하는 방법](../debugger/debugger-tips-and-tricks.md#modules_window)에 대 한 자세한 정보를 참조 하세요.

![모듈 창의 사용자 코드](../debugger/media/dbg_justmycode_module.png "모듈 창의 사용자 코드")

**호출 스택** 또는 **작업** 창에서 사용자가 사용 하지 않는 코드를 `[External Code]` 레이블이 지정 된 회색으로 표시 된 주석이 추가 된 코드 프레임으로 축소 내 코드만 합니다.

![호출 스택 창의 외부 코드 프레임](../debugger/media/dbg_justmycode_externalcode.png "외부 코드 프레임")

>[!TIP]
>**모듈**, **호출 스택**, **작업**또는 대부분의 다른 디버깅 창을 열려면 디버깅 세션에 있어야 합니다. 디버깅 하는 동안 **디버그**  > **창**에서 열려는 창을 선택 합니다.

<a name="BKMK_Override_call_stack_filtering"></a>축소 된 **[External code]** 프레임에서 코드를 보려면 **호출 스택** 또는 **작업** 창을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **외부 코드 표시** 를 선택 합니다. 확장 된 외부 코드 줄은 **[External code**] 프레임을 대체 합니다.

![호출 스택 창에 외부 코드 표시](../debugger/media/dbg_justmycode_showexternalcode.png "외부 코드 표시")

> [!NOTE]
> **외부 코드 표시** 사용자가 연 모든 언어의 모든 프로젝트에 적용 되는 현재 사용자 프로파일러 설정입니다.

**호출 스택** 창에서 확장 된 외부 코드 줄을 두 번 클릭 하면 소스 코드에서 호출 하는 코드 줄이 녹색으로 강조 표시 됩니다. Dll 또는 다른 모듈을 찾을 수 없거나 로드할 수 없는 경우 기호 또는 소스를 찾을 수 없음 페이지가 열립니다.

## <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET 내 코드만

.NET 프로젝트에서 내 코드만는 기호 ( *.pdb*) 파일 및 프로그램 최적화를 사용 하 여 사용자 코드와 사용자가 사용 하지 않는 코드를 분류 합니다. .NET 디버거는 최적화 된 이진 파일과 로드 되지 않은 *.pdb* 파일을 사용자 코드가 아닌 코드로 간주 합니다.

세 가지 컴파일러 특성은 .NET 디버거가 사용자 코드로 간주 되는 항목에도 영향을 줍니다.

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>은 적용 되는 코드가 사용자 코드가 아님을 디버거에 지시 합니다.
- <xref:System.Diagnostics.DebuggerHiddenAttribute>가 적용된 코드는 내 코드만 옵션을 해제했더라도 디버거에서 숨겨집니다.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>는 코드를 한 단계씩 실행 하는 대신 적용 되는 코드를 단계별로 실행 하도록 디버거에 지시 합니다.

.NET 디버거는 다른 모든 코드를 사용자 코드로 간주 합니다.

.NET 디버깅 중:

- 코드를 사용 하지 않는 사용자 코드 단계에서 사용자 코드의 다음 줄로 **디버그**  >  한**단계씩 코드 실행** (또는 **F11**) 합니다.
- 사용자가 실행 하지 않는 코드에 대 한 **디버그**  > **프로시저 아웃** **(또는** **F11 + F11**)은 사용자 코드의 다음 줄로 실행 됩니다.

사용자 코드가 더 이상 없으면 디버깅이 종료 되거나 다른 중단점에 도달 하거나 오류가 throw 될 때까지 계속 됩니다.

<a name="BKMK_NET_Breakpoint_behavior"></a>사용자가 만든 코드가 아닌 코드에서 디버거가 중단 된 경우 (예: **디버그**  > **모두 중단** 및 사용자가 사용 하지 않는 코드에서 일시 중지) **소스 없음** 창이 표시 됩니다. 그런 다음 **디버그**  > **단계** 명령을 사용 하 여 사용자 코드의 다음 줄로 이동할 수 있습니다.

사용자가 작성 하지 않은 코드에서 처리 되지 않은 예외가 발생 하면 디버거가 예외가 생성 된 사용자 코드 줄에서 중단 됩니다.

예외에 대해 첫 번째 예외를 사용 하도록 설정 하면 소스 코드에서 호출 하는 사용자 코드 줄이 녹색으로 강조 표시 됩니다. **[외부 코드]** 레이블이 지정 된 프레임을 **호출 스택** 창에 표시 합니다.

## <a name="BKMK_C___Just_My_Code"></a> C++ 내 코드만

Visual Studio 2017 버전 15.8부터 코드 단계별 실행에 대 한 내 코드만도 지원 됩니다. 또한이 기능을 사용 하려면 [/JMC (내 코드만 디버깅)](/cpp/build/reference/jmc) 컴파일러 스위치를 사용 해야 합니다. 스위치는 프로젝트에서 C++ 기본적으로 사용 하도록 설정 됩니다. **호출 스택** 창과 내 코드만의 호출 스택 지원은/JMC 스위치가 필요 하지 않습니다.

<a name="BKMK_CPP_User_and_non_user_code"></a>사용자 코드로 분류 하려면 디버거에서 사용자 코드를 포함 하는 이진 파일에 대 한 PDB를 로드 해야 합니다 ( **모듈** 창을 사용 하 여이를 확인).

**호출 스택** 창과 같은 호출 스택 동작의 경우의 C++ 내 코드만은 이러한 함수만 *사용자 코드가 아닌 코드로*간주 합니다.

- 기호 파일에서 소스 정보가 제거된 함수
- 기호 파일에서 스택 프레임에 해당하는 소스 파일이 없음을 나타내는 함수
- Natjmc 파일에 지정 *\** 된 함수는 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더에 있습니다.

코드 단계별 동작의 경우의 C++ 내 코드만은 이러한 함수만 *사용자 코드가 아닌 코드로*간주 합니다.

- 해당 PDB 파일이 디버거에 로드 되지 않은에 대 한 함수입니다.
- Natjmc 파일에 지정 *\** 된 함수는 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더에 있습니다.

> [!NOTE]
> 내 코드만에서 코드 단계별 실행을 지원 C++ 하려면 Visual Studio 15.8 Preview 3 이상에서 MSVC 컴파일러를 사용 하 여 코드를 컴파일하고/JMC 컴파일러 스위치를 사용 하도록 설정 해야 합니다 (기본적으로 사용 하도록 설정 됨). 자세한 내용은 [호출 스택 및 코드 C++ 실행 동작 사용자 지정](#BKMK_CPP_Customize_call_stack_behavior)(영문) 및이 [블로그 게시물](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/)을 참조 하세요. 이전 컴파일러를 사용 하 여 컴파일된 코드의 경우 *natstepfilter* 파일은 내 코드만와 독립적인 코드 단계별 실행을 사용자 지정 하는 유일한 방법입니다. [단계별 실행 C++ 동작 사용자 지정](#BKMK_CPP_Customize_stepping_behavior)을 참조 하세요.

<a name="BKMK_CPP_Stepping_behavior"></a>디버깅 C++ 하는 동안:

- 코드를 사용 하지 않는 사용자 코드 단계에서 사용자 코드의 다음 줄로 **디버그**  >  한**단계씩 코드 실행** (또는 **F11**) 합니다.
- 사용자가 실행 하지 않는 코드에 대 한 **디버그**  > **프로시저 아웃** **(또는** **F11 + F11**)은 사용자 코드의 다음 줄로 실행 됩니다.

사용자 코드가 더 이상 없으면 디버깅이 종료 되거나 다른 중단점에 도달 하거나 오류가 throw 될 때까지 계속 됩니다.

사용자가 만든 코드가 아닌 코드에서 디버거가 중단 되는 경우 (예: **디버그**  > **모두 중단** 및 사용자가 아닌 코드에서 일시 중지), 단계별 실행은 사용자가 만든 코드를 사용 하지 않습니다.

디버거가 예외에 도달 하면 사용자 또는 사용자가 사용 하지 않는 코드에 있든 관계 없이 예외가 발생 합니다. **예외 설정** 대화 상자에서 **사용자가 처리 하지 않은** 옵션은 무시 됩니다.

### <a name="BKMK_CPP_Customize_call_stack_behavior"></a>호출 C++ 스택 및 코드 실행 동작 사용자 지정

프로젝트 C++ 의 경우 **호출 스택** 창에서 사용자 코드로 처리 하는 모듈, 소스 파일 및 함수를 *\* natjmc* 파일에 지정 하 여 지정할 수 있습니다. 최신 컴파일러를 사용 하는 경우이 사용자 지정은 코드 단계별 실행에도 적용 됩니다 ( [ C++ 내 코드만](#BKMK_CPP_User_and_non_user_code)참조).

- Visual Studio 컴퓨터의 모든 사용자에 대해 사용자가 지정 하지 않은 코드를 지정 하려면 *natjmc* 파일을 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더에 추가 합니다.
- 개별 사용자에 대해 사용자가 지정 하지 않은 코드를 지정 하려면 *natjmc* 파일을 *%USERPROFILE%\My 문서 \\ < Visual Studio 버전 \> \visualizers 도우미* 폴더에 추가 합니다.

*Natjmc* 파일은 다음 구문을 사용 하는 XML 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">

  <!-- Modules -->
  <Module Name="ModuleSpec" />
  <Module Name="ModuleSpec" Company="CompanyName" />

  <!-- Files -->
  <File Name="FileSpec"/>

  <!-- Functions -->
  <Function Name="FunctionSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />

</NonUserCode>

```

 **모듈 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 모듈의 전체 경로입니다. Windows 와일드 카드 문자 `?` (0 개 또는 한 개의 문자)를 사용 하 고 `*` (0 개 이상의 문자)를 사용할 수 있습니다. 예를 들어 개체에 적용된<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> 모든 드라이브에서 *\3rdParty\UtilLibs* 의 모든 모듈을 외부 코드로 처리 하도록 디버거에 지시 합니다.|
|`Company`|(선택 사항) 실행 파일에 포함된 모듈을 게시하는 회사의 이름입니다. 이 특성을 사용하여 모듈을 구분할 수 있습니다.|

 **파일 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 외부 코드로 처리할 소스 파일의 전체 경로입니다. 경로를 지정할 때 Windows 와일드 카드 문자 `?` 및 `*`를 사용할 수 있습니다.|

 **함수 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 외부 코드로 처리할 함수의 정규화된 이름입니다.|
|`Module`|(선택 사항) 함수를 포함하는 모듈의 이름 또는 전체 경로입니다. 이 특성을 사용하여 동일한 이름을 가진 함수를 구분할 수 있습니다.|
|`ExceptionImplementation`|`true`로 설정된 경우 이 함수 대신 예외를 발생시킨 함수가 호출 스택에 표시됩니다.|

### <a name="BKMK_CPP_Customize_stepping_behavior"></a>내 코드만 C++ 설정에 관계 없이 단계별 실행 동작 사용자 지정

프로젝트 C++ 에서 *natstepfilter 파일 \** 에 사용자가 작성 하지 않은 코드로 나열 하 여 프로시저 단위로 실행 되도록 함수를 지정할 수 있습니다. *Natstepfilter 파일 \** 에 나열 된 함수는 내 코드만 설정에 종속 되지 않습니다.

- 모든 로컬 Visual Studio 사용자에 대해 사용자가 지정 하지 않은 코드를 지정 하려면 *natstepfilter* 파일을 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더에 추가 합니다.
- 개별 사용자에 대해 사용자가 지정 하지 않은 코드를 지정 하려면 *natstepfilter* 파일을 *%USERPROFILE%\My 문서 \\ < Visual Studio 버전 \> \visualizers 도우미* 폴더에 추가 합니다.

*Natstepfilter* 파일은 다음 구문을 사용 하는 XML 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">
    <Function>
        <Name>FunctionSpec</Name>
        <Action>StepAction</Action>
    </Function>
    <Function>
        <Name>FunctionSpec</Name>
        <Module>ModuleSpec</Module>
        <Action>StepAction</Action>
    </Function>
</StepFilter>

```

|요소|설명|
|-------------|-----------------|
|`Function`|필수 요소. 하나 이상의 함수를 사용자가 작성하지 않은 함수로 지정합니다.|
|`Name`|필수 요소. 일치시킬 전체 함수 이름을 지정하는 ECMA 262 형식의 정규식입니다. 예를 들면,<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> `MyNS::MyClass`의 모든 메서드를 사용자가 작성하지 않은 코드로 간주하도록 디버거에 지시합니다. 일치 항목 찾기에서는 대/소문자를 구분합니다.|
|`Module`|(선택 사항) 함수를 포함하는 모듈의 전체 경로를 지정하는 ECMA 262 형식의 정규식입니다. 일치 항목 찾기에서는 대/소문자를 구분하지 않습니다.|
|`Action`|필수 요소. 대/소문자를 구분하는 다음 값 중 하나입니다.<br /><br /> `NoStepInto`-디버거에 함수를 실행 하도록 지시 합니다.<br /> `StepInto`-함수를 한 단계씩 실행 하 고 일치 하는 함수에 대 한 다른 `NoStepInto`를 재정의 하도록 디버거에 지시 합니다.|

## <a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript 내 코드만

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript 내 코드만 옵션은 다음 분류 중 하나로 코드를 분류하여 단계별 실행 및 호출 스택 표시를 제어합니다.

|||
|-|-|
|**MyCode**|사용자가 소유하고 제어하는 사용자 코드입니다.|
|**LibraryCode**|정기적으로 사용 하 고 앱이 올바르게 작동 하기 위해 사용 하는 라이브러리의 사용자가 만든 코드 (예: WinJS 또는 jQuery)입니다.|
|**UnrelatedCode**|사용자가 소유 하지 않으며 앱이 올바르게 작동 하지 않는 응용 프로그램에 사용자 코드가 아닌 코드를 사용 합니다. 예를 들어 광고를 표시 하는 광고 SDK는 UnrelatedCode 수 있습니다. UWP 프로젝트에서 HTTP 또는 HTTPS URI에서 앱에 로드 되는 모든 코드는 UnrelatedCode 간주 됩니다.|

JavaScript 디버거는 다음과 같은 순서로 사용자 또는 비 사용자로 코드를 분류 합니다.

1. 기본 분류입니다.
   - 호스트에서 제공 하는 `eval` 함수에 문자열을 전달 하 여 실행 되는 스크립트는 **Mycode**입니다.
   - @No__t_0 생성자에 문자열을 전달 하 여 실행 되는 스크립트는 **라이브러리 코드**입니다.
   - WinJS 또는 Azure SDK와 같은 프레임 워크 참조의 스크립트는 **라이브러리 코드**입니다.
   - @No__t_0, `setImmediate` 또는 `setInterval` 함수에 문자열을 전달 하 여 실행 되는 스크립트는 **UnrelatedCode**입니다.

2. *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* 파일의 모든 Visual Studio JavaScript 프로젝트에 대해 지정 된 분류입니다.

3. 현재 프로젝트의 *mycode. json* 파일의 분류입니다.

각 분류 단계는 이전 단계를 재정의합니다.

기타 모든 코드는 **MyCode**로 분류됩니다.

*Mycode json* 이라는 *Json* 파일을 JavaScript 프로젝트의 루트 폴더에 추가 하 여 기본 분류를 수정 하 고 특정 파일 및 url을 사용자 또는 사용자가 아닌 코드로 분류할 수 있습니다. [JavaScript 내 코드만 사용자 지정](#BKMK_JS_Customize_Just_My_Code)을 참조 하세요.

<a name="BKMK_JS_Stepping_behavior"></a>JavaScript 디버깅 중:

- 함수가 사용자가 아닌 코드 이면 **디버그**  >  한 단계씩 코드**실행** (또는 **F11**키)은 **디버그**  > **프로시저 단위 실행** ( **F10**)과 동일 하 게 동작 합니다.
- 단계가 사용자가 아닌 사용자 (**라이브러리 코드** 또는 **UnrelatedCode**) 코드에서 시작 하는 경우 단계별 실행은 내 코드만 사용 하도록 설정 되지 않은 것 처럼 일시적으로 동작 합니다. 사용자 코드로 돌아갈 때 내 코드만 단계별 실행이 다시 설정 됩니다.
- 사용자 코드 단계로 인해 현재 실행 컨텍스트가 벗어나면 디버거가 실행 된 다음 사용자 코드 줄에서 중지 됩니다. 예를 들어 콜백이 **LibraryCode** 코드에서 실행되는 경우 사용자 코드의 다음 줄이 실행될 때까지 디버거가 계속됩니다.
- 사용자 코드의 다음 줄에서 **프로시저 실행** (또는 **이동** +**F11**)이 중지 됩니다.

사용자 코드가 더 이상 없으면 디버깅이 종료 되거나 다른 중단점에 도달 하거나 오류가 throw 될 때까지 계속 됩니다.

코드에 설정 된 중단점은 항상 적중 되지만 코드는 분류 됩니다.

- @No__t_0 키워드가 **라이브러리 코드**에서 발생 하는 경우 디버거는 항상 중단 합니다.
- @No__t_0 키워드가 **UnrelatedCode**에서 발생 하면 디버거가 중지 되지 않습니다.

<a name="BKMK_JS_Exception_behavior"></a>**Mycode** 또는 **라이브러리 코드** 코드에서 처리 되지 않은 예외가 발생 하면 디버거가 항상 중단 됩니다.

**UnrelatedCode**에서 처리 되지 않은 예외가 발생 하 고 **Mycode** 또는 **라이브러리 코드가** 호출 스택에 있으면 디버거가 중단 됩니다.

예외에 대해 첫 번째 예외를 사용 하도록 설정 하 고 **라이브러리 코드** 또는 **UnrelatedCode**에서 예외가 발생 하면입니다.

- 예외가 처리되었으면 디버거가 중단되지 않습니다.
- 예외가 처리되지 않았으면 디버거가 중단됩니다.

### <a name="BKMK_JS_Customize_Just_My_Code"></a>JavaScript 내 코드만 사용자 지정

단일 JavaScript 프로젝트에 대 한 사용자 코드 및 사용자가 지정 되지 않은 코드를 분류 하려면 프로젝트의 루트 폴더에 *mycode. json* 이라는 *json* 파일을 추가 하면 됩니다.

이 파일의 사양은 기본 분류와 *mycode. 기본* 파일을 재정의 합니다. *Mycode json* 파일은 모든 키 값 쌍을 나열할 필요가 없습니다. **Mycode** **, library 및** **관련** 없는 값은 빈 배열 일 수 있습니다.

*Mycode. json* 파일은 다음 구문을 사용 합니다.

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function 및 ScriptBlock**

**Eval**, **Function** 및 **ScriptBlock** 키 값 쌍은 동적으로 생성된 코드의 분류 방법을 결정합니다.

|||
|-|-|
|**Eval**|호스트에서 제공하는 `eval` 함수에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 Eval 스크립트는 **MyCode**로 분류됩니다.|
|**Function**|`Function` 생성자에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 Function 스크립트는 **LibraryCode**로 분류됩니다.|
|**ScriptBlock**|`setTimeout`, `setImmediate` 또는 `setInterval` 함수에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 ScriptBlock 스크립트는 **UnrelatedCode**로 분류됩니다.|

다음 키워드 중 하나로 값을 변경할 수 있습니다.

- `MyCode`는 스크립트를 **MyCode**로 분류합니다.
- `Library`는 스크립트를 **LibraryCode**로 분류합니다.
- `Unrelated`는 스크립트를 **UnrelatedCode**로 분류합니다.

**MyCode, Libraries 및 Unrelated**

**MyCode**, **Libraries** 및 **Unrelated** 키 값 쌍은 분류에 포함할 URL 또는 파일을 지정합니다.

|||
|-|-|
|**MyCode**|**MyCode**로 분류된 URL 또는 파일의 배열입니다.|
|**라이브러리**|**LibraryCode**로 분류된 URL 또는 파일의 배열입니다.|
|**Unrelated**|**UnrelatedCode**로 분류된 URL 또는 파일의 배열입니다.|

URL 또는 파일 문자열에는 0 개 이상의 문자와 일치 하는 하나 이상의 `*` 문자가 있을 수 있습니다. `*`는 정규식 `.*`와 동일 합니다.
