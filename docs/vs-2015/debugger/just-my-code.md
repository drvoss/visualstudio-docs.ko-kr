---
title: 내 코드만 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823949"
---
# <a name="just-my-code"></a>내 코드만
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework 언어를 사용하는 개발자는 시스템, 프레임워크 및 사용자가 작성하지 않은 기타 호출을 건너뛰고 호출 스택 화면에서 해당 호출을 축소하는 내 코드만 디버거 기능에 익숙합니다. 내 코드만 옵션이 C++ 및 JavaScript 언어까지 확장되었습니다. 이 항목에서는 .NET Framework, 네이티브 C++ 및 JavaScript 프로젝트에서 내 코드만을 사용하는 방법의 기본 사항에 대해 설명합니다.  
  
## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> 내 코드만 사용 또는 사용 안 함  
 를 사용 하거나 내 코드만 사용 하지 않도록 설정 하려면 선택 **옵션 및 설정** 에 **디버그** 메뉴. 에 **디버깅** / **일반** 노드를 선택 하거나 선택 취소 **내 코드만**합니다.  
  
 ![옵션 대화 상자에서 내 코드만 사용 하도록 설정](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> 합니다 **내 코드만** 설정은 모든 언어로 모든 Visual Studio 프로젝트에 적용 되는 전역 설정입니다.  
  
### <a name="BKMK_Override_call_stack_filtering"></a> 호출 스택 필터링 재정의  
 호출 스택 및 작업 창과 같은 호출 스택 표시에서 내 코드만 옵션은 사용자가 작성하지 않은 코드를 `[External Code]` 레이블이 있는 주석이 추가된 프레임으로 축소합니다. 축소 된 프레임을 보려면 **외부 코드 포시** 호출 스택 상황에 맞는 메뉴에 표시 합니다.  
  
> [!NOTE]
> 합니다 **외부 코드 포시** 설정은 현재 사용자의 프로파일러에 저장 됩니다. 이 사용자가 여는 모든 언어의 프로젝트에 모두 적용됩니다.  
  
## <a name="BKMK__NET_Framework_Just_My_Code"></a> .NET framework 내 코드만  
  
### <a name="BKMK_NET_User_and_non_user_code"></a> 사용자 및 사용자가 아닌 코드  
 사용자 코드에서 사용자 코드가 아닌을 구분 하려면 내 코드만 "기호 (.pdb) 파일 및 프로그램 최적화에" 찾습니다. 이진이 최적화되었거나 .pdb 파일을 사용할 수 없는 경우 디버거에서 코드를 사용자가 작성하지 않은 코드로 간주합니다.  
  
 다음 세 가지 특성도 디버거에서 내 코드로 간주되는 항목에 영향을 줍니다.  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>가 적용된 코드는 내 코드가 아님을 디버거에 알립니다.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute>가 적용된 코드는 내 코드만 옵션을 해제했더라도 디버거에서 숨겨집니다.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>가 적용된 코드는 디버거에서 한 단계씩 실행되지 않고 단계별로 실행됩니다.  
  
  다른 모든 코드는 사용자 코드로 간주됩니다.  
  
### <a name="BKMK_NET_Stepping_behavior"></a> 단계별 실행 동작  
 경우 있습니다 **단계씩** (바로 가기 키: 다음 사용자 문 코드 디버거 단계 F11) 비 사용자 코드입니다. 경우 있습니다 **프로시저 나가기** (키보드: Shift + F11) 디버거가 사용자 코드의 다음 줄을 실행 합니다. 사용자 코드가 없는 경우 앱이 종료되거나, 중단점이 적중되거나, 예외가 발생할 때까지 실행이 계속됩니다.  
  
### <a name="BKMK_NET_Breakpoint_behavior"></a> 중단점 동작  
 내 코드만 사용 하는 경우 선택할 수 있습니다 **모두 중단** (키보드: Ctrl + Alt + Break) 위치에서 실행을 중지 하 고 표시할 사용자 코드가 없는 경우. 이 경우 소스 없음 창이 표시됩니다. 단계별 실행 명령을 선택하면 디버거에서 사용자 코드의 다음 줄로 이동합니다.  
  
### <a name="BKMK_NET_Exception_behavior"></a> 예외 동작  
 사용자가 작성하지 않은 코드에서 처리되지 않은 예외가 발생할 경우 디버거는 예외가 생성된 사용자 코드의 줄에서 중단됩니다.  
  
 예외에 대해 첫째 예외가 설정된 경우 사용자 코드 줄이 녹색으로 강조 표시됩니다. 호출 스택 표시는 레이블이 있는 주석이 달린된 프레임이 **[External Code]** 합니다.  
  
## <a name="BKMK_C___Just_My_Code"></a> C++ 내 코드만  
  
### <a name="BKMK_CPP_User_and_non_user_code"></a> 사용자 및 사용자가 아닌 코드  
 단계별 실행 동작이 호출 스택 동작과 독립적이므로 C++ 내 코드만 옵션은 .NET Framework 및 JavaScript 내 코드만 옵션과 다릅니다.  
  
 **호출 스택**  
  
 기본적으로 디버거는 호출 스택 창에서 다음 함수를 사용자가 작성하지 않은 코드로 간주합니다.  
  
- 기호 파일에서 소스 정보가 제거된 함수  
  
- 기호 파일에서 스택 프레임에 해당하는 소스 파일이 없음을 나타내는 함수  
  
- `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 폴더의 `*.natjmc` 파일에 지정된 함수  
  
  **단계별 실행**  
  
  기본적으로 `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 폴더의 `*.natstepfilter` 파일에 지정된 함수만 사용자가 작성하지 않은 코드로 간주됩니다.  
  
  고유한 `.natstepfilter` 및 `.natjmc`를 만들어 `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`의 단계별 실행 및 호출 스택 창 동작을 사용자 지정할 수 있습니다.  
  
### <a name="BKMK_CPP_Stepping_behavior"></a> 단계별 실행 동작  
 경우 있습니다 **단계씩** (바로 가기 키: 사용자 코드에서 사용자 코드의 다음 줄으로 코드 디버거 단계 F11) 비 사용자 코드입니다. 경우 있습니다 **프로시저 나가기** (키보드: Shift + F11) 디버거가 사용자 코드의 다음 줄을 실행 합니다. 사용자 코드가 없는 경우 앱이 종료되거나, 중단점이 적중되거나, 예외가 발생할 때까지 실행이 계속됩니다.  
  
 사용자가 작성하지 않은 코드에서 디버거가 중단된 경우(예를 들어 모두 중단 명령이 사용자가 작성하지 않은 코드에서 중지된 경우) 사용자가 작성하지 않은 코드에서 단계별 실행이 계속됩니다.  
  
### <a name="BKMK_CPP_Exception_behavior"></a> 예외 동작  
 디버거가 예외를 적중한 경우 사용자 코드에 있든, 사용자가 작성하지 않은 코드에 있든 관계없이 예외에서 중지됩니다. 합니다 **user-unhandled** 옵션에 **예외** 대화 상자는 무시 됩니다.  
  
### <a name="BKMK_CPP_Customize_stepping_behavior"></a> 단계별 실행 동작을 사용자 지정  
 `*.natstepfilter` 파일에 사용자가 작성하지 않은 코드로 나열하여 프로시저 단위로 실행할 함수를 지정할 수 있습니다.  
  
- Visual Studio 컴퓨터의 모든 사용자에 대 한 비 사용자 코드를 지정 하려면.natstepfilter 파일을 추가 합니다 `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 폴더입니다.  
  
- 개별 사용자에 대 한 비 사용자 코드를 지정 하려면.natstepfilter 파일을 추가 합니다 `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` 폴더입니다.  
  
  .natstepfilter 파일은이 구문 사용 하 여 xml 파일:  
  
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
|함수|필수 요소. 하나 이상의 함수를 사용자가 작성하지 않은 함수로 지정합니다.|  
|`Name`|필수 요소. 일치시킬 전체 함수 이름을 지정하는 ECMA 262 형식의 정규식입니다. 예를 들어:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> `MyNS::MyClass`의 모든 메서드를 사용자가 작성하지 않은 코드로 간주하도록 디버거에 지시합니다. 일치 항목 찾기에서는 대/소문자를 구분합니다.|  
|`Module`|선택 사항입니다. 함수를 포함하는 모듈의 전체 경로를 지정하는 ECMA 262 형식의 정규식입니다. 일치 항목 찾기에서는 대/소문자를 구분하지 않습니다.|  
|`Action`|필수 요소. 대/소문자를 구분하는 다음 값 중 하나입니다.<br /><br /> -   `NoStepInto`  -일치 하는 함수를 디버거에 지시 합니다.<br />-   `StepInto`  – 다른 재정의 일치 하는 함수로 한 단계씩 코드를 디버거에서 `NoStepInto` 일치 하는 함수에 대 한 합니다.|  
  
### <a name="BKMK_CPP_Customize_call_stack_behavior"></a> 호출 스택 동작 사용자 지정  
 `*.natjmc` 파일에 지정하여 호출 스택에서 사용자가 작성하지 않은 코드로 처리할 모듈, 소스 파일 및 함수를 지정할 수 있습니다.  
  
- Visual Studio 컴퓨터의 모든 사용자에 대 한 비 사용자 코드를 지정 하려면.natjmc 파일을 추가 합니다 `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 폴더입니다.  
  
- 개별 사용자에 대 한 비 사용자 코드를 지정 하려면.natjmc 파일을 추가 합니다 `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` 폴더입니다.  
  
  .natjmc 파일은이 구문 사용 하 여 xml 파일:  
  
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
|`Name`|필수 요소. 모듈의 전체 경로입니다. Windows 와일드 카드 문자 `?`(0개 또는 한 개의 문자) 및 `*`(0개 이상의 문자)를 사용할 수 있습니다. 예를 들면 다음과 같습니다.<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> 는 드라이브의 `\3rdParty\UtilLibs`에 있는 모든 모듈을 외부 코드로 처리하도록 디버거에 지시합니다.|  
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
  
## <a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript 내 코드만  
  
### <a name="BKMK_JS_User_and_non_user_code"></a> 사용자 및 사용자가 아닌 코드  
 **코드 분류**  
  
 JavaScript 내 코드만 옵션은 다음 분류 중 하나로 코드를 분류하여 단계별 실행 및 호출 스택 표시를 제어합니다.  
  
|||  
|-|-|  
|**MyCode**|사용자가 소유하고 제어하는 사용자 코드입니다.|  
|**LibraryCode**|사용자가 정기적으로 사용하며 애플리케이션이 제대로 작동하는 데 필요한, 사용자가 작성하지 않은 라이브러리의 코드(예: WinJS 또는 jQuery)입니다.|  
|**UnrelatedCode**|응용 프로그램 에서만 실행 될 수 있는 비 사용자 코드가 소유 하지 않은 및 응용 프로그램이 올바르게 (예: 광고를 표시 하는 광고 SDK) 함수를 직접 의존 하지 않습니다. Windows 스토어 프로젝트에서는 HTTP 또는 HTTPS URI에서 앱으로 로드된 모든 코드도 UnrelatedCode로 간주됩니다.|  
  
 JavaScript 디버거는 이러한 유형의 코드를 자동으로 분류합니다.  
  
- 호스트에서 제공 하는 문자열을 전달 하 여 실행 되는 스크립트 `eval` 함수는 기밀로 **MyCode**합니다.  
  
- 문자열을 전달 하 여 실행 되는 스크립트를 `Function` 생성자로 분류 됩니다 **LibraryCode**합니다.  
  
- WinJS 또는 Azure SDK와 같은 프레임 워크 참조에 포함 된 스크립트는 기밀로 **LibraryCode**합니다.  
  
- 문자열을 전달 하 여 실행 되는 스크립트를 `setTimeout`, `setImmediate`, 또는 `setInterval` 기능으로 분류 됩니다 **UnrelatedCode**합니다.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`은 모든 Visual Studio JavaScript 프로젝트에 대해 기타 사용자 코드 및 사용자가 작성하지 않은 코드를 지정합니다.  
  
  프로젝트의 루트 폴더에 `mycode.json`이라는 .json 파일을 추가하여 기본 분류를 수정하고 특정 파일 및 URL을 분류할 수 있습니다.  
  
  기타 모든 코드는 **MyCode**로 분류됩니다.  
  
### <a name="BKMK_JS_Stepping_behavior"></a> 단계별 실행 동작  
  
- 함수를 사용자가 아닌 경우 (**MyCode**) 코드 **단계씩** (바로 가기 키: F11) 처럼 **프로시저 단위 실행** (키보드: F10)입니다.  
  
- 비 사용자의 단계를 시작 하는 경우 (**LibraryCode** 또는 **UnrelatedCode**) 코드, 내 코드만 사용 하지 않는 경우에 따라 동작 일시적으로 단계별로 실행 합니다. 사용자 코드로 돌아가는 즉시 내 코드만 단계별 실행이 다시 사용됩니다.  
  
- 사용자 코드의 단계로 인해 현재 실행 컨텍스트를 벗어나는 경우(예: 이벤트 처리기의 마지막 줄에서 단계 수행) 디버거가 사용자 코드의 실행된 다음 줄에서 중지됩니다. 예를 들어 콜백이 실행 되 면 **LibraryCode** 코드 디버거가 사용자 코드의 다음 줄이 실행 될 때까지 계속 합니다.  
  
- **프로시저 나가기** (키보드: Shift + F11) 사용자 코드의 다음 줄에서 중지 합니다. 사용자 코드가 없는 경우 앱이 종료되거나, 중단점이 적중되거나, 예외가 발생할 때까지 실행이 계속됩니다.  
  
### <a name="BKMK_JS_Breakpoint_behavior"></a> 중단점 동작  
  
- 코드에서 설정된 중단점은 해당 코드의 분류에 관계없이 항상 적중됩니다.  
  
- `debugger` 키워드가  
  
  - **LibraryCode** 코드 디버거가 항상 중단 합니다.  

  - **UnrelatedCode** 코드에서 디버거가 중지 되지 않습니다.  
  
### <a name="BKMK_JS_Exception_behavior"></a> 예외 동작  
 처리되지 않는 예외가  
  
- **MyCode** 나 **LibraryCode** 코드 디버거가 항상 중단 합니다.  
  
- **UnrelatedCode** 코드 및 **MyCode** 하거나 **LibraryCode** 코드는 호출 스택에서 디버거가 중단 합니다.  
  
  예외 대화 상자에서 예외에 대해 첫째 예외가 사용 되 고 예외가 throw 됩니다 **LibraryCode** 하거나 **UnrelatedCode** 코드:  
  
- 예외가 처리되었으면 디버거가 중단되지 않습니다.  
  
- 예외가 처리되지 않았으면 디버거가 중단됩니다.  
  
### <a name="BKMK_JS_Customize_Just_My_Code"></a> 내 코드만 사용자 지정  
 단일 Visual Studio 프로젝트에 대해 사용자 코드 및 사용자가 작성하지 않은 코드를 분류하려면 프로젝트의 루트 폴더에 `mycode.json`이라는 .json 파일을 추가합니다.  
  
 분류는 다음 순서대로 수행됩니다.  
  
1. 기본 분류  
  
2. `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` 파일 분류  
  
3. 현재 프로젝트의 `mycode. json` 파일 분류  
  
   각 분류 단계는 이전 단계를 재정의합니다. 모든 키 값 쌍을 나열 하지 않아도.json 파일 및 **MyCode**를 **라이브러리**, 및 **Unrelated** 값에 빈 배열 될 수 있습니다.  
  
   내 코드 .json 파일은 다음 구문을 사용합니다.  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function 및 ScriptBlock**  
  
 **Eval**, **함수**, 및 **ScriptBlock** 키/값 쌍 결정 하는 방법을 동적으로 생성 된 코드 분류 됩니다.  
  
|||  
|-|-|  
|**Eval**|호스트에서 제공하는 `eval` 함수에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 Eval 스크립트는 **MyCode**로 분류됩니다.|  
|**함수**|`Function` 생성자에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 Function 스크립트는 **LibraryCode**로 분류됩니다.|  
|**ScriptBlock**|`setTimeout`, `setImmediate` 또는 `setInterval` 함수에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 ScriptBlock 스크립트는 **UnrelatedCode**로 분류됩니다.|  
  
 다음 키워드 중 하나로 값을 변경할 수 있습니다.  
  
- `MyCode`는 스크립트를 **MyCode**로 분류합니다.  
  
- `Library`는 스크립트를 **LibraryCode**로 분류합니다.  
  
- `Unrelated`는 스크립트를 **UnrelatedCode**로 분류합니다.  
  
  **MyCode, Libraries 및 Unrelated**  
  
  합니다 **MyCode**를 **라이브러리**, 및 **Unrelated** url 또는 파일 분류에 포함 하려는 키/값 쌍 지정:  
  
|||  
|-|-|  
|**MyCode**|Url 또는으로 분류 되는 파일의 배열을 **MyCode**합니다.|  
|**라이브러리**|Url 또는으로 분류 되는 파일의 배열을 **LibraryCode**합니다.|  
|**Unrelated**|Url 또는으로 분류 되는 파일의 배열을 **UnrelatedCode**합니다.|  
  
 URL 또는 파일 문자열에는 0개 이상의 문자와 일치하는 `*` 문자가 하나 이상 포함될 수 있습니다. `*`는 `.*` 정규식과 동일합니다.
