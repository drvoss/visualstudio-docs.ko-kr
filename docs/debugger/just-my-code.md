---
title: 내 코드만 사용 하 여 사용자 코드를 디버그 | Microsoft Docs
ms.date: 02/13/2019
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edb78ed49add85b35f3fb89b4ba424d44f52bf8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905801"
---
# <a name="debug-only-user-code-with-just-my-code"></a>내 코드만 사용 하 여 사용자 코드만 디버깅

*내 코드만* 기능은 Visual Studio 디버깅는 자동으로 단계 시스템, 프레임 워크 및 기타 비 사용자 코드를 호출 합니다. 에 **호출 스택** Just My Code 창에 이러한 호출을 축소 **[External Code]** 프레임입니다.

.NET framework에서 다르게 작동는 내 코드만 C++, 및 JavaScript 프로젝트입니다.

## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> 내 코드만 사용 또는 사용 안 함

대부분의 프로그래밍 언어에 대 한 내 코드만 옵션은 기본적으로 사용 됩니다.

- Visual Studio에서 내 코드만 아래 사용할지 **도구** > **옵션** (또는 **디버그** > **옵션**) > **디버깅** > **일반**를 선택 하거나 선택 취소 **내 코드만**합니다.

![옵션 대화 상자에서 내 코드만 사용 하도록 설정](../debugger/media/dbg_justmycode_options.png "내 코드만 사용")

> [!NOTE]
> **내 코드만 사용** 모든 언어로 모든 Visual Studio 프로젝트에 적용 되는 전역 설정입니다.

## <a name="just-my-code-debugging"></a>내 코드만 디버깅

디버깅 세션 중에 **모듈** 디버거 내 코드 (사용자)를 처리 하는 모듈의 기호 상태 로드와 함께 코드 창 표시 합니다. 자세한 내용은 [더 디버거가 앱에 연결 하는 방법을 잘 알고 싶다면](../debugger/debugger-tips-and-tricks.md#modules_window)합니다.

![모듈 창에서 사용자 코드](../debugger/media/dbg_justmycode_module.png "모듈 창에서 사용자 코드")

에 **호출 스택** 또는 **태스크** 레이블이 지정 된 주석이 추가 된 코드 회색 프레임 창을, Just My Code 축소 사용자 코드가 아닌 `[External Code]`.

![호출 스택 창에서 외부 코드 프레임](../debugger/media/dbg_justmycode_externalcode.png "외부 코드 프레임")

>[!TIP]
>열려는 합니다 **모듈**, **호출 스택**를 **작업**, 디버깅 세션에서 해야 디버깅 다른 대부분의 windows 또는 합니다. 아래에서 디버깅 하는 동안 **디버그** > **Windows**를 열려는 windows를 선택 합니다.

<a name="BKMK_Override_call_stack_filtering"></a> 축소 된 코드를 보려면 **[External Code]** 프레임을 마우스 오른쪽 단추로 클릭 합니다 **호출 스택** 또는 **태스크** 창에서 선택한 **외부 코드 포시**상황에 맞는 메뉴입니다. 대신 확장 된 외부 코드 줄을 사용 합니다 **[External Code**] 프레임입니다.

![호출 스택 창에서 외부 코드 표시](../debugger/media/dbg_justmycode_showexternalcode.png "외부 코드 표시")

> [!NOTE]
> **외부 코드 표시** 현재 사용자 프로파일러 설정 하는 사용자가 열려 있는 모든 언어로 모든 프로젝트에 적용 된다는 점입니다.

에 있는 확장 된 외부 코드 줄을 두 번 클릭 합니다 **호출 스택** 창에 소스 코드에서 녹색에서 호출 코드 줄이 강조 표시 합니다. Dll 또는 다른 모듈을 찾을 수 없거나 로드에 대 한 기호 또는 소스를 찾을 수 없습니다 페이지가 열릴 수 있습니다.

## <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET framework 내 코드만

.NET Framework 프로젝트에서 내 코드만 사용 하 여 기호 (*.pdb*) 파일 및 프로그램 최적화 사용자 및 사용자가 아닌 코드를 분류 합니다. .NET Framework 디버거 이진 파일을 최적화 하 고 로드를 고려 *.pdb* 비 사용자 코드 파일.

또한 세 가지 컴파일러 특성은 사용자 코드로 간주.NET 디버거가 영향을 줍니다.

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> 코드에 적용 되는 사용자 코드 없습니다 디버거에 지시 합니다.
- <xref:System.Diagnostics.DebuggerHiddenAttribute>가 적용된 코드는 내 코드만 옵션을 해제했더라도 디버거에서 숨겨집니다.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> 디버거에서 코드를 한 단계씩 실행 하는 대신에 적용 되는 코드를 단계별로 실행 합니다.

.NET Framework 디버거는 사용자 코드로 다른 모든 코드를 고려 합니다.

.NET Framework 디버깅 중:

- **디버그** > **단계씩** (또는 **F11**) 사용자 코드의 다음 줄으로 코드를 통해 사용자 코드가 아닌 단계에 있습니다.
- **디버그** > **나가기** (또는 **Shift**+**F11**) 비 사용자 코드에서 사용자 코드의 다음 줄을 실행 합니다.

더 이상 사용자 코드가 있으면 종료 또는 다른 중단점을 적중, 오류를 throw 될 때까지 계속 디버깅 합니다.

<a name="BKMK_NET_Breakpoint_behavior"></a> 비 사용자 코드에서 디버거가 중단 하는 경우 (사용 하는 예를 들어 **디버그** > **모두 중단** 비 사용자 코드에서 일시 중지 하 고), **소스 없음** 창이 나타납니다. 사용할 수는 **디버그** > **단계** 사용자 코드의 다음 줄으로 이동 하는 명령입니다.

비 사용자 코드에서 처리 되지 않은 예외가 발생 하는 경우 디버거는 예외가 생성 되었습니다. 여기서 사용자 코드 줄에서 중단 됩니다.

첫 번째 예외는 예외에 대 한 사용 하는 경우 호출 사용자 코드 줄에는 소스 코드에서 녹색으로 강조 표시 됩니다. 합니다 **호출 스택** 레이블이 지정 된 주석이 추가 된 프레임 창에 표시 됩니다 **[External Code]** 합니다.

## <a name="BKMK_C___Just_My_Code"></a> C++ 내 코드만

부터 Visual Studio 2017 버전 15.8, 코드에 대 한 내 코드만 단계별 실행도 지원 됩니다. 이 기능에도 사용 해야 합니다 [(내 코드만 디버깅) /JMC](/cpp/build/reference/jmc) 컴파일러 스위치입니다. 스위치에는 기본적으로 사용 됩니다 C++ 프로젝트입니다. 에 대 한 **호출 스택** 창과 호출 스택 지원 내 코드만 /JMC 스위치가 필요 하지 않습니다.

<a name="BKMK_CPP_User_and_non_user_code"></a> 사용자 코드로 분류 되려면, 사용자 코드가 포함 된 이진 파일에 대 한 PDB 디버거에서 로드 해야 합니다 (사용 합니다 **모듈** 이 확인란을 선택 하는 창).

같은 호출 스택 동작에 대 한 합니다 **호출 스택** 창에서 내 코드만 C++ 고려 되도록 이러한 함수만 *사용자 코드가 아닌*:

- 기호 파일에서 소스 정보가 제거된 함수
- 기호 파일에서 스택 프레임에 해당하는 소스 파일이 없음을 나타내는 함수
- 함수에 지정 된  *\*.natjmc* 파일을 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더입니다.

내 코드만, 코드 단계별 실행 동작에 대 한 C++ 를 이러한 함수에만 고려 *사용자 코드가 아닌*:

- 해당 PDB 파일이 로드 되지 않은 디버거에서 함수입니다.
- 함수에 지정 된  *\*.natjmc* 파일을 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더입니다.

> [!NOTE]
> 코드에서 내 코드만 단계별 실행 지원에 대 한 C++ Visual Studio 15.8 미리 보기 3 이상에서는 MSVC 컴파일러를 사용 하 여 코드 컴파일 및 /JMC 컴파일러 스위치를 사용할 수 있어야 합니다 (기본적으로 사용 됩니다). 자세한 내용은 참조 하세요. [사용자 지정 C++ 호출 스택 및 코드 단계별 실행 동작](#BKMK_CPP_Customize_call_stack_behavior))이 [블로그 게시물](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/)합니다. 이전 컴파일러를 사용 하 여 컴파일된 코드에 대 한 *.natstepfilter* Just My Code 독립적인 코드를 단계별로 실행 사용자 지정 하는 유일한 방법은 파일이 있습니다. 참조 [사용자 지정 C++ 단계별 실행 동작](#BKMK_CPP_Customize_stepping_behavior)합니다.

<a name="BKMK_CPP_Stepping_behavior"></a> 중 C++ 디버깅:

- **디버그** > **단계씩** (또는 **F11**) 사용자 코드의 다음 줄으로 코드를 통해 사용자 코드가 아닌 단계에 있습니다.
- **디버그** > **나가기** (또는 **Shift**+**F11**) 비 사용자 코드에서 사용자 코드의 다음 줄을 실행 합니다.

더 이상 사용자 코드가 있으면 종료 또는 다른 중단점을 적중, 오류를 throw 될 때까지 계속 디버깅 합니다.

비 사용자 코드에서 디버거가 중단 하는 경우 (사용 하는 예를 들어 **디버그** > **모두 중단** 및 비 사용자 코드에서 일시 중지), 비 사용자 코드에서 계속 단계별로 실행 합니다.

디버거가 예외에 도달 여부와 관계 없이 사용자 또는 비 사용자 코드에서 예외를 중지 합니다. **사용자가 처리 하지 않은** 옵션을 **예외 설정** 대화 상자는 무시 됩니다.

### <a name="BKMK_CPP_Customize_call_stack_behavior"></a> 사용자 지정 C++ 호출 스택 및 코드 단계별 실행 동작

에 대 한 C++ 프로젝트를 소스 파일 및 함수 모듈을 지정할 수 있습니다는 **호출 스택** 창에 지정 하 여 사용자 코드가 아닌 취급  *\*.natjmc* 파일입니다. 이 사용자 지정 코드 최신 컴파일러를 사용 하는 경우 단계별 실행에 적용 됩니다 (참조 [ C++ 내 코드만](#BKMK_CPP_User_and_non_user_code)).

- Visual Studio 컴퓨터의 모든 사용자에 대 한 비 사용자 코드를 지정 하려면 다음을 추가 합니다 *.natjmc* 파일을 합니다 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더.
- 개별 사용자에 대 한 비 사용자 코드를 지정 하려면 다음을 추가 합니다 *.natjmc* 파일을 합니다 *%USERPROFILE%\My 문서\\< Visual Studio 버전\>\Visualizers* 폴더.

A *.natjmc* 파일은이 구문 사용 하 여 XML 파일:

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
|`Name`|필수 요소. 모듈의 전체 경로입니다. Windows 와일드 카드 문자를 사용할 수 있습니다 `?` (0 개 이상의 문자) 및 `*` (0 개 이상의 문자). 예를 들면 다음과 같습니다.<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> 모든 모듈에서 처리 하도록 디버거에 지시 *\3rdParty\UtilLibs* 외부 코드로 모든 드라이브에서.|
|`Company`|선택 사항입니다. 실행 파일에 포함된 모듈을 게시하는 회사의 이름입니다. 이 특성을 사용하여 모듈을 구분할 수 있습니다.|

 **파일 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 외부 코드로 처리할 소스 파일의 전체 경로입니다. 경로를 지정할 때 Windows 와일드 카드 문자 `?` 및 `*`를 사용할 수 있습니다.|

 **함수 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 외부 코드로 처리할 함수의 정규화된 이름입니다.|
|`Module`|선택 사항입니다. 함수를 포함하는 모듈의 이름 또는 전체 경로입니다. 이 특성을 사용하여 동일한 이름을 가진 함수를 구분할 수 있습니다.|
|`ExceptionImplementation`|`true`로 설정된 경우 이 함수 대신 예외를 발생시킨 함수가 호출 스택에 표시됩니다.|

### <a name="BKMK_CPP_Customize_stepping_behavior"></a> 사용자 지정 C++ 내 코드만 설정의 독립적인 단계별 실행 동작

C++ 프로젝트의 경우 함수에 대 한 비 사용자 코드로 나열 하는 조치 단계를 지정할 수 있습니다  *\*.natstepfilter* 파일입니다. 에 나열 된 함수  *\*.natstepfilter* 파일 내 코드만 설정에 종속 되지 않습니다.

- 모든 로컬 Visual Studio 사용자에 대 한 비 사용자 코드를 지정 하려면 다음을 추가 합니다 *.natstepfilter* 파일을 합니다 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더.
- 개별 사용자에 대 한 비 사용자 코드를 지정 하려면 다음을 추가 합니다 *.natstepfilter* 파일을 합니다 *%USERPROFILE%\My 문서\\< Visual Studio 버전\>\Visualizers* 폴더.

A *.natstepfilter* 파일은이 구문 사용 하 여 XML 파일:

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
|`Name`|필수 요소. 일치시킬 전체 함수 이름을 지정하는 ECMA 262 형식의 정규식입니다. 예를 들어:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> `MyNS::MyClass`의 모든 메서드를 사용자가 작성하지 않은 코드로 간주하도록 디버거에 지시합니다. 일치 항목 찾기에서는 대/소문자를 구분합니다.|
|`Module`|선택 사항입니다. 함수를 포함하는 모듈의 전체 경로를 지정하는 ECMA 262 형식의 정규식입니다. 일치 항목 찾기에서는 대/소문자를 구분하지 않습니다.|
|`Action`|필수 요소. 대/소문자를 구분하는 다음 값 중 하나입니다.<br /><br /> `NoStepInto`  -함수를 디버거에 지시 합니다.<br /> `StepInto`  -다른 재정의 함수를 한 단계씩 실행 하도록 디버거에 지시 `NoStepInto` 일치 하는 함수에 대 한 합니다.|

## <a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript 내 코드만

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript 내 코드만 옵션은 다음 분류 중 하나로 코드를 분류하여 단계별 실행 및 호출 스택 표시를 제어합니다.

|||
|-|-|
|**MyCode**|사용자가 소유하고 제어하는 사용자 코드입니다.|
|**LibraryCode**|정기적으로 사용 하는 라이브러리 및 앱에서 사용자 이외의 코드는 올바르게 (예: WinJS 또는 jQuery) 함수에 의존 합니다.|
|**UnrelatedCode**|소유한 앱 및 앱에서 사용자 이외의 코드는 제대로 작동 하려면 의존 하지 않습니다. 예를 들어, 광고를 표시 하는 SDK는 광고 UnrelatedCode 수 있습니다. UWP 프로젝트에서 HTTP 또는 HTTPS URI에서 앱에 로드 되는 모든 코드는 코드도 UnrelatedCode로 간주 합니다.|

JavaScript 디버거는 사용자 또는 사용자가 아닌이 순서 대로 코드를 분류합니다.

1. 기본 분류 합니다.
   - 호스트에서 제공 하는 문자열을 전달 하 여 실행 되는 스크립트 `eval` 함수는 **MyCode**합니다.
   - 문자열을 전달 하 여 실행 되는 스크립트를 `Function` 생성자 **LibraryCode**합니다.
   - WinJS 또는 Azure SDK와 같은 프레임 워크 참조에서 스크립트가 **LibraryCode**합니다.
   - 문자열을 전달 하 여 실행 되는 스크립트를 `setTimeout`, `setImmediate`, 또는 `setInterval` 함수는 **UnrelatedCode**합니다.

2. 모든 Visual Studio JavaScript 프로젝트에 대 한 지정 된 분류 합니다 *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* 파일입니다.

3. 분류 합니다 *mycode.json* 현재 프로젝트의 파일입니다.

각 분류 단계는 이전 단계를 재정의합니다.

기타 모든 코드는 **MyCode**로 분류됩니다.

기본 분류를 수정 하 고 사용자 또는 사용자가 아닌 코드로 추가 하 여 특정 파일 및 Url을 분류할 수를 *.json* 파일인 *mycode.json* JavaScript 프로젝트의 루트 폴더에 있습니다. 참조 [JavaScript 내 코드만 사용자 지정](#BKMK_JS_Customize_Just_My_Code)합니다.

<a name="BKMK_JS_Stepping_behavior"></a> JavaScript 디버깅 중:

- 함수를 비 사용자 코드 이면 **디버그** > **단계씩** (또는 **F11**)와 동일 **디버그**  >  **건너뛰기** (또는 **F10**).
- 비 사용자의 단계를 시작 하는 경우 (**LibraryCode** 하거나 **UnrelatedCode**) 코드 단계별 실행을 일시적으로 처럼 내 코드만 사용 되지 않습니다. 내 코드만 사용자 코드를 다시 실행 하면 단계별 실행이 다시 사용 됩니다.
- 때 현재 실행 컨텍스트를 벗어나지에서 사용자 코드 단계 결과 다음 실행된 사용자 코드 줄에서 디버거가 중지 됩니다. 예를 들어 콜백이 **LibraryCode** 코드에서 실행되는 경우 사용자 코드의 다음 줄이 실행될 때까지 디버거가 계속됩니다.
- **프로시저 나가기** (또는 **Shift**+**F11**) 사용자 코드의 다음 줄에서 중지 합니다.

더 이상 사용자 코드가 있으면 종료 또는 다른 중단점을 적중, 오류를 throw 될 때까지 계속 디버깅 합니다.

코드에 설정 된 중단점이 적중 항상 있지만 코드 분류 됩니다.

- 경우는 `debugger` 키워드에 나오는 **LibraryCode**, 디버거가 항상 중단 합니다.
- 경우는 `debugger` 키워드에 나오는 **UnrelatedCode**, 디버거가 중지 되지 않습니다.

<a name="BKMK_JS_Exception_behavior"></a> 처리 되지 않은 예외가 발생 하는 경우 **MyCode** 하거나 **LibraryCode** 코드 디버거가 항상 중단 합니다.

처리 되지 않은 예외가 발생 하는 경우 **UnrelatedCode**, 및 **MyCode** 또는 **LibraryCode** 호출 스택에서 디버거가 중단 됩니다.

예외에 대해 첫째 예외가 설정 되 고에서 예외가 발생 하는 경우 **LibraryCode** 하거나 **UnrelatedCode**:

- 예외가 처리되었으면 디버거가 중단되지 않습니다.
- 예외가 처리되지 않았으면 디버거가 중단됩니다.

### <a name="BKMK_JS_Customize_Just_My_Code"></a> JavaScript 내 코드만 사용자 지정

사용자 및 사용자 코드가 아닌 단일 JavaScript 프로젝트에 대 한 분류를 추가할 수 있습니다는 *.json* 파일인 *mycode.json* 프로젝트의 루트 폴더에 있습니다.

이 파일의 사양을 기본 분류를 재정의 하며 *mycode.default.wwa.json* 파일입니다. 합니다 *mycode.json* 파일에서 모든 키 값 쌍 목록 필요가 없습니다. 합니다 **MyCode**를 **라이브러리**, 및 **Unrelated** 값에 빈 배열 될 수 있습니다.

*Mycode.json* 파일에는이 구문을 사용 합니다.

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

URL 또는 파일 문자열을 하나 이상 포함할 수도 있습니다 `*` 문자 0 개 이상의 문자를 찾습니다. `*` 정규식 동일 `.*`합니다.
