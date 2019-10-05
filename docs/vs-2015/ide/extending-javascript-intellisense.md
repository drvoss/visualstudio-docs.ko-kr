---
title: JavaScript IntelliSense 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eea71ffe2b449e0ee5aff893efd05e12e4ecae73
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824925"
---
# <a name="extending-javascript-intellisense"></a>JavaScript IntelliSense 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript IntelliSense 확장성 기능을 사용 하면 타사 라이브러리에 대 한 JavaScript 편집기의 IntelliSense 결과 사용자 지정할 수 있습니다. 이 이러한 라이브러리를 사용 하는 개발자의 환경을 개선할 수 있습니다.  
  
 JavaScript language service 프로젝트에 추가 되는 타사 JavaScript 라이브러리에 대 한 IntelliSense 기능을 제공 합니다. 대부분의 라이브러리에 대 한 문 완성 언어 서비스에서 자동으로 제공 됩니다. 다음 그림은 문 완성의 예제를 보여 줍니다.  
  
 ![문 완성 예제](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 라이브러리는 표준 JavaScript 주석 태그에서 변수, 함수 및 개체에 대 한 설명은 포함 하는 경우 (/ /), 팝업 상자에 설명이 포함 된 정보를 제공 하는 IntelliSense 확장성 기능에서 기본적으로 자동으로 활용 요소는 완성 목록에서 함수 호출에서 여는 괄호를 입력 하면 오른쪽에 나타납니다. 팝업 상자에서 주석을 멤버에 대 한 설명을 포함 합니다. 다음 예제에서는 완성 목록 팝업 상자를 보여 줍니다.  
  
 ![요약 정보 pop의 예제에서는&#45;상자를](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 추가 환경을 개선 하기 위해 개발자, 개발자가 팝업 상자에서 형식 정보를 제공 하는 것이 좋습니다. JavaScript를 사용 하 여 형식 정보를 제공할 수 있습니다 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md) 표준 주석 태그 대신 합니다. 삼중 슬래시 주석 태그 (/ / /) 및 XML 요소로 정의 된 집합을 사용 하 여 XML 문서 주석을 추가 합니다.  
  
 또는 JavaScript IntelliSense 확장성을 사용 하 여 형식 정보를 제공할 수 있습니다. 이 기능을 사용 하면 JavaScript 확장을 만들고 스크립트 컨텍스트를 추가 하 여 IntelliSense 결과 사용자 지정할 수 있습니다. JavaScript 파일에는 확장에 의해 노출 되는 이벤트에 구독을 `intellisense` 언어 서비스의 개체입니다. JavaScript IntelliSense 확장성 라이브러리의 동작 패턴을 JavaScript language service 원하는 수준의 IntelliSense 지원 제공 하는 것을 방지 한 경우 및 선언적 XML 대신 하는 경우 라이브러리에 대 한 기본 솔루션입니다. 문서 주석에 필요 합니다. IntelliSense 결과 사용자 지정 하 여 언어 서비스의 기본 기능을 제한 하는 동작 패턴에 관계 없이 첫 번째 클래스는 IntelliSense 환경을 만들 수 있습니다. 자세한 내용은 [식별자에 대한 문 완성](../ide/statement-completion-for-identifiers.md)을 참조하세요.  
  
## <a name="adding-an-extension-to-the-script-context"></a>스크립트 컨텍스트에 확장을 추가합니다.  
 에서 실행할 IntelliSense 확장에 대 한 현재 스크립트 컨텍스트를 추가 해야 합니다. 자동 검색 메커니즘에 의해 스크립트 컨텍스트에 확장을 자동으로 추가 될 수 있습니다 하거나 추가할 수 있습니다 확장 스크립트 컨텍스트를 수동으로 참조 그룹 또는 참조 지시문을 사용 하 여 합니다.  
  
 자동 검색 메커니즘을 자동으로 파일 명명 규칙을 따르는 확장을 찾을 수 있도록 언어 서비스를 사용 하도록 설정 *libraryname*. intellisense.js, 및는 라이브러리와 같은 디렉터리에 있는 확장을 적용 합니다. 예를 들어, jQuery 라이브러리에 대 한 유효한 확장 jQuery.intellisense.js 것입니다. 더 제한적인 jQuery 확장에 대 한 파일 이름 예: jQuery-1.7.1.intellisense.js (버전별 확장명) 또는 jQuery.ui.intellisense.js (범위가 지정 된 jQuery 라이브러리에 대 한 확장)를 사용할 수 있습니다. 지정 된 라이브러리에 대 한 둘 이상의 확장 없으면 확장의 가장 제한적인 버전이 사용 됩니다.  
  
 모든 JavaScript 프로젝트 파일에 대 한 확장을 사용 하려는 경우에 확장 참조 그룹을 추가 하려면 대신 선택할 수 있습니다. 여러 유형의 참조 그룹, 암시적 참조를 포함 하는 및 전용된 작업자 참조를 포함 하는 경우 확장을 추가 하려면 일반적으로 해야 하거나 암시적 참조 그룹으로 파일을 추가 하려면 **암시적 (Windows)** 하십시오 **암시적 (웹)** 합니다. 코드 편집기에서 열려 있는 각.js 파일의 범위 내에 암시적 참조 됩니다. 이 메서드를 사용 하면 확장 및 확장 보완 되는 파일을 모두 추가 해야 합니다.  
  
 사용 된 **IntelliSense** 페이지를 **옵션** 참조 그룹으로 확장을 추가 하려면 대화 상자. 액세스할 수 있습니다 합니다 **IntelliSense** 를 선택 하 여 페이지 **도구**를 **옵션** 메뉴 모음에서을 차례로 선택 **텍스트 편집기**를 **JavaScript**, **IntelliSense**하십시오 **참조**합니다. 참조 그룹에 대 한 자세한 내용은 참조 하세요. [JavaScript IntelliSense](../ide/javascript-intellisense.md) 하 고 [옵션, 텍스트 편집기, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)합니다.  
  
 파일의 특정 집합에 대 한 확장을 사용 하려는 경우 참조 지시문을 사용 합니다. 이 메서드를 사용 하면 확장 및 확장은 보완 하는 파일을 모두 참조 해야 합니다. 참조 지시문을 사용 하는 방법에 대 한 내용은 [JavaScript IntelliSense](../ide/javascript-intellisense.md)합니다.  
  
## <a name="handling-intellisense-events"></a>IntelliSense 이벤트 처리  
 확장성 기능을 사용 하면 같은 이벤트를 구독 하 여 IntelliSense 결과 사용자 지정할 수 있습니다 합니다 `statementcompletion` 언어 서비스의 이벤트 `intellisense` 개체입니다. 다음 예제에서는 문 완성에서 밑줄로 시작 하는 멤버를 숨기려면 언어 서비스에서 사용 되는 단순한 확장을 보여 줍니다. 이 코드 underscorefilter.js에 포함 된 요소 이며 합니다 \\ \\ *Visual Studio 설치 경로*\JavaScript\References 폴더입니다.  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 위의 코드에서 확장 확인 합니다 [targetName 속성](#TargetName) 및 [대상 속성](#Target) 의 속성을 `statementcompletion` 이벤트 개체와 같은 개체를 제외 하 `this` 및 `window`, 및 유효한 문 완성 목록이 식별할 수 있는지 확인 합니다. 확장 업데이트 문 완성 완성 목록이 식별할 수 있습니다 [속성을 항목](#Items) 밑줄로 시작 하는 멤버를 필터링 하 여 컬렉션입니다.  
  
 추가 예제를 보려면 확인 합니다 \\ \\ *Visual Studio 설치 경로*\JavaScript\References 폴더입니다. 이 폴더에 있는 showPlainComments.js 파일 다른 이벤트를 사용 하 여 표준 JavaScript 주석 태그에 대 한 기본 IntelliSense 지원을 제공 하는 예제를 제공 합니다. (/ /). Underscorefilter.js, 같은 이미 showPlainComments.js 작업 확장으로 사용할 수 있으며 변수, 함수 및 개체에 대 한 코드에서 주석 태그를 사용 하는 경우 결과 IntelliSense 정보를 확인할 수 있습니다. 추가 예제를 보려면 [코드 예제에서는](#CodeExamples)합니다.  
  
> [!WARNING]
> Visual Studio에 포함 된 확장 파일을 수정 하는 경우 JavaScript IntelliSense 또는 확장에서 지 원하는 기능을 비활성화할 수 있습니다.  
  
 확장 프로그램 코드에서 사용 하 여 다음 이벤트 유형에 대 한 처리기를 만들 수 있습니다 `addEventListener`:  
  
- `statementcompletion`문 완료 이벤트에 대 한 처리기를 추가 합니다. 문 완성 또는 마침표 (.), 같은 특수 문자를 입력 한 후 표시 되는 특정 형식에 대 한 멤버 목록을 입력 하는 동안 또는 CTRL + j. 키를 누를 때 표시 되는 식별자의 목록을 제공합니다 처리기 형식의 이벤트 개체를 받는 `CompletionEvent`, 다음 멤버를 지 원하는: [속성 항목](#Items), [대상 속성](#Target)를 [targetName 속성](#TargetName), 및 [범위 속성](#Scope)합니다.  
  
- `signaturehelp`에서 IntelliSense 매개 변수 정보에 대 한 처리기를 추가 합니다. 매개 변수 정보는 개수, 이름 및 함수에 필요한 매개 변수의 형식에 대 한 정보를 제공 합니다. 처리기 형식의 이벤트 개체를 받는 `SignatureHelpEvent`, 다음 멤버를 지 원하는: [대상 속성](#Target), [parentObject 속성](#ParentObject), [functionComments속성](#FunctionComments)하십시오 [functionHelp 속성](#FunctionHelp)합니다.  
  
- `statementcompletionhint`에서 IntelliSense 요약 정보에 대 한 처리기를 추가 합니다. 요약 정보 팝업 상자 코드에서 식별자에 대 한 전체 선언을 보여 줍니다. 처리기 형식의 이벤트 개체를 받는 `CompletionHintEvent`, 다음 멤버를 지 원하는: [completionItem 속성](#CompletionItem), 및 [symbolHelp 속성](#SymbolHelp)합니다.  
  
  문 완성, 매개 변수 정보 및 요약 정보 같은 IntelliSense 기능을 보여 주는 예제를 보려면 [IntelliSense를 사용 하 여](../ide/using-intellisense.md)입니다.  
  
> [!NOTE]
> JavaScript에서 요약 정보를 완성 목록이 오른쪽에 표시 되는 팝업 상자 가리킵니다. 요약 정보를 수동으로 호출할 수 없습니다.  
  
## <a name="intellisenseObject"></a> intellisense 개체  
 다음 표에서 사용할 수 있는 함수는 `intellisense` 개체입니다. `intellisense` 개체를 디자인 타임에만 사용할 수 있습니다.  
  
|함수|Description|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|IntelliSense 이벤트에 대 한 이벤트 처리기를 추가합니다.<br /><br /> `type` 문자열 값이입니다. 유효한 값은 `statementcompletion`, `signaturehelp` 및 `statementcompletionhint`입니다.<br /><br /> `handler` 다음 형식 중 하나의 이벤트 개체를 받는 이벤트 처리기 함수:<br /><br /> -   `CompletionEvent`를 사용 합니다 `statementcompletion` 이벤트입니다.<br />-   `SignatureHelpEvent`를 사용 합니다 `signaturehelp` 이벤트입니다.<br />-   `CompletionHintEvent`를 사용 합니다 `statementcompletionhint` 이벤트입니다.<br /><br /> 이 함수를 사용 하는 예제를 보려면 [코드 예제에서는](#CodeExamples)합니다.|  
|`annotate(obj, doc);`|다른 개체에 문서 주석을 한 개체에서 복사 하 여 개체에 대 한 설명서를 지정 합니다.<br /><br /> `obj` 설명서를 복사 하는 개체를 지정 합니다.<br /><br /> `doc` 설명서를 복사할 개체를 지정 합니다.<br /><br /> 이 함수를 사용 하는 방법을 보여 주는 예제를 보려면 [IntelliSense 주석 추가](#Annotations)합니다.|  
|`getFunctionComments(func);`|지정된 된 함수에 대 한 설명을 반환합니다.<br /><br /> `func` 주석을 반환 되는 함수를 지정 합니다.<br /><br /> 설정할 수 있습니다 합니다 `func` 매개 변수를 사용 하 여 `completionItem.value`입니다.<br /><br /> 반환 된 `functionComments` 개체에는 다음 멤버가 포함 됩니다. `above`, `inside`, 및 `paramComment`. 자세한 내용은 참조는 [functionComments 속성](#FunctionComments) 속성입니다.<br /><br /> `getFunctionComments` 등록 된 이벤트 처리기 중 하나 내 에서만 호출할 수 있습니다 `addEventListener`합니다.<br /><br /> 이 함수를 사용 하는 방법을 보여 주는 예제를 보려면 \\ \\ *Visual Studio 설치 경로*\JavaScript\References\showPlainComments.js 합니다.|  
|`logMessage(msg);`|출력 창에 진단 메시지를 보냅니다.<br /><br /> `msg` 메시지를 포함 하는 문자열입니다.<br /><br /> 이 함수를 사용 하는 방법을 보여 주는 예제를 보려면 [출력 창에 메시지 보내기](#Logging)합니다.|  
|`nullWithCompletionsOf(value);`|완성 목록에 전달 된 개체에 의해 결정 됩니다는 특별 한 null 값을 반환 합니다 `value` 매개 변수입니다.<br /><br /> `value` 반환된 된 값에 대 한 완성 목록을 확인합니다. `value` 모든 형식일 수 있습니다.<br /><br /> 반환 값의 자동 완성 목록에 대 한 완성 목록에 동일 하지만 null 반환 값은 디자인 타임에는 null로 처리 됩니다는 `value` 매개 변수입니다.<br /><br /> 반환 형식은 런타임에 예측할 수 있지만 반환 값은 반환 값에 대 한 IntelliSense를 제공 하는이 함수에 대해 사용할 `null` 디자인 타임.|  
|`redirectDefinition(func, definition);`|매개 변수는 데 도움이 되는 경우 원래 func 함수 대신 제공 된 정의 함수를 사용 하는 IntelliSense 지시 하거나 **정의로 이동** 요청 합니다.<br /><br /> `func` 대상 함수를 지정합니다.<br /><br /> `definition` 매개 변수 정보에 대 한 대상 함수 대신 사용할 함수를 지정 하 고 **정의로 이동**합니다.|  
|`setCallContext(func, thisArg);`|호출 컨텍스트 또는 지정된 된 함수에 대 한 범위를 설정합니다.<br /><br /> `func` 범위를 설정 하는 함수를 지정 합니다.<br /><br /> `thisArg` 개체는 리터럴 여 `this` 멤버에 대 한 새 범위를 지정 하는 키워드를 참조할 수 있습니다. 예를 들어이 매개 변수에 전달할 인수를 포함할 수 있습니다. `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` 비슷한 동작을 제공 `Function.prototype.bind`한다는 점을 제외 하 고 디자인 타임 IntelliSense 지원에 대해서만 사용 합니다. 사용할 수 있습니다 `setCallContext` 함수를 호출 하는 경우는 그렇지 않은 경우에 연결할 수 없음, 코드에 대 한 호출을 시뮬레이션 하는 경우 함수 범위로 설정에 올바른 범위 및 인수를 함수 호출 포함 됩니다.|  
|`undefinedWithCompletionsOf(value);`|완성 목록에 전달 된 개체에 의해 결정 됩니다 특수 정의 되지 않은 값을 반환 합니다 `value` 매개 변수입니다.<br /><br /> `value` 반환된 된 값에 대 한 완성 목록을 확인합니다. `value` 모든 형식일 수 있습니다.<br /><br /> 정의 되지 않은 반환 값은 처리으로 디자인 타임에만 완료 정의 되지 않은 반환 값에 대 한 목록 같습니다에 대 한 완성 목록에는 `value` 매개 변수입니다.<br /><br /> 이 함수에 대 한 한 가지 용도 반환 형식은 런타임에 예측할 수 있지만 반환 값은 디자인 타임에 정의 되지 않습니다. 반환 값에 대 한 IntelliSense를 제공 하는 것입니다.|  
|`version()`|Visual Studio 버전을 반환합니다.|  
  
## <a name="event-members"></a>이벤트 멤버  
 다음 섹션에서는 다음과 같은 이벤트에 대 한 이벤트 개체에 노출 되는 멤버를 설명 합니다. `statementcompletion`, `signaturehelp`, 및 `statementcompletionhint`.  
  
### <a name="CompletionItem"></a> completionItem 속성  
 완성 항목, 요약 정보 팝업 상자를 요청한 대상 이라는 식별자를 반환 합니다. 이 속성은 사용할 수는 `statementcompletionhint` 이벤트 개체 한는 [속성 항목](#Items) 의 속성을 `statementcompletion` 이벤트 개체.  
  
 반환 값: `completionItem` 개체  
  
 다음은의 멤버는 `completionItem` 개체:  
  
- `name`. 읽기/쓰기에 사용 되는 경우는 `items` 컬렉션, 그렇지 않으면 읽기 전용입니다. 완성 항목을 식별 하는 문자열을 반환 합니다.  
  
- `kind`. 읽기/쓰기에 사용 되는 경우는 `items` 컬렉션, 그렇지 않으면 읽기 전용입니다. 완성 항목의 형식을 나타내는 문자열을 반환 합니다. 가능한 값은 메서드, 필드, 속성, 매개 변수, 변수 및 예약.  
  
- `glyph`. 읽기/쓰기에 사용 되는 경우는 `items` 컬렉션, 그렇지 않으면 읽기 전용입니다. 완성 목록에 표시 되는 아이콘을 나타내는 문자열을 반환 합니다. 가능한 값은 `glyph` 다음 형식을 사용: vs:*glyphType*여기서 *glyphType* 언어 독립적인 멤버에 해당 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> 열거형입니다. 예를 들어 `vs:GlyphGroupMethod` 에 대 한 값 중 하나는 `glyph`합니다. 때 `glyph` 을 설정 하지 않으면는 `kind` 속성의 기본 아이콘을 결정 합니다.  
  
- `parentObject`. 읽기 전용입니다. 부모 개체를 반환합니다.  
  
- `value`. 읽기 전용입니다. 완성 항목의 값을 나타내는 개체를 반환 합니다.  
  
- `comments`. 읽기 전용입니다. 필드 또는 변수를 초과 하는 주석이 포함 된 문자열을 반환 합니다.  
  
- `scope`. 읽기 전용입니다. 완성 항목의 범위를 반환합니다. 가능한 값은 전역, 지역 매개 변수 및 멤버입니다.  
  
### <a name="Items"></a> 항목 속성  
 문의 배열을 완성 항목을 가져오거나 설정 합니다. 배열의 각 요소는 [completionItem 속성](#CompletionItem) 개체입니다. 합니다 `items` 속성은 사용할 수는 `statementcompletion` 이벤트 개체입니다.  
  
 반환 값: 배열  
  
### <a name="FunctionComments"></a> functionComments 속성  
 함수에 대 한 설명을 반환합니다. 이 속성은 사용할 수는 `signaturehelp` 이벤트 개체입니다.  
  
 반환 값: `comments` 개체  
  
 다음은의 멤버는 `comments` 개체:  
  
- `above`. 함수 위에 설명을 반환합니다.  
  
- `inside`. 일반적으로 VSDoc 형태로 함수 내부의 주석에 반환합니다.  
  
- `paramComments`. 함수에서 각 매개 변수에 대해 주석을 나타내는 배열을 반환 합니다. 배열의 멤버는 다음과 같습니다.  
  
  - `name`. 매개 변수 이름을 나타내는 문자열을 반환 합니다.  

  - `comment`. 매개 변수 설명이 포함 된 문자열을 반환 합니다.  
  
### <a name="FunctionHelp"></a> functionHelp 속성  
 함수에 대 한 도움말을 반환합니다. 이 속성은 사용할 수는 `signaturehelp` 이벤트 개체입니다.  
  
 반환 값: `functionHelp` 개체  
  
 다음은의 멤버는 `functionHelp` 개체:  
  
- `functionName`. 읽기/쓰기입니다. 함수 이름이 들어 있는 문자열을 반환 합니다.  
  
- `signatures`. 읽기/쓰기입니다. 함수 시그니처 배열을 가져오거나 설정 합니다. 배열의 각 요소는 `signature` 개체입니다. 일부 `signature` 속성을 같은 `locid`를 공용으로 해당 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md) 특성입니다.  
  
  멤버는 `signature` 개체 포함:  

  - `description`. 읽기/쓰기입니다. 함수를 설명 하는 문자열을 반환 합니다.  

  - `locid`. 읽기/쓰기입니다. 함수에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.  

  - `helpKeyword`. 읽기/쓰기입니다. 도움말 키워드를 포함 하는 문자열을 반환 합니다.  

  - `externalFile`. 읽기/쓰기입니다. 멤버 ID를 포함 하는 파일을 나타내는 문자열을 반환 합니다.  

  - `externalid`. 읽기/쓰기입니다. 함수 멤버 ID를 나타내는 문자열을 반환 합니다.  

  - `params`. 읽기/쓰기입니다. 함수의 매개 변수 배열을 가져오거나 설정 합니다. 매개 변수 배열의 각 요소는 `parameter` 의 다음 특성에 해당 하는 속성이 있는 개체를 [ \<매개 변수 >](../ide/param-javascript.md) 요소:  

    - `name`. 읽기/쓰기입니다. 매개 변수 이름을 나타내는 문자열을 반환 합니다.  

    - `type`. 읽기/쓰기입니다. 매개 변수 형식을 나타내는 문자열을 반환 합니다.  

    - `elementType`. 읽기/쓰기입니다. 형식이 `Array`, 배열에 있는 요소의 형식을 나타내는 문자열을 반환 합니다.  

    - `description`. 읽기/쓰기입니다. 매개 변수를 설명 하는 문자열을 반환 합니다.  

    - `locid`. 읽기/쓰기입니다. 함수에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.  

    - `optional`. 읽기/쓰기입니다. 매개 변수가 선택 사항 인지 여부를 나타내는 문자열을 반환 합니다. `true` 매개 변수가 선택 사항입니다; 임을 나타냅니다. `false` 임을 나타냅니다.  

  - `returnValue`. 읽기/쓰기입니다. 다음 특성에 해당 하는 속성을 사용 하 여 반환 값 개체를 가져오거나 합니다 [ \<반환 >](../ide/returns-javascript.md) 요소:  

    - `type`. 읽기/쓰기입니다. 반환 형식을 나타내는 문자열을 반환 합니다.  

    - `elementType`. 읽기/쓰기입니다. 형식이 `Array`, 배열에 있는 요소의 형식을 나타내는 문자열을 반환 합니다.  

    - `description`. 읽기/쓰기입니다. 반환 값을 설명 하는 문자열을 반환 합니다.  

    - `locid`. 읽기/쓰기입니다. 함수에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.  

    - `helpKeyword`. 읽기/쓰기입니다. 도움말 키워드를 포함 하는 문자열을 반환 합니다.  

    - `externalFile`. 읽기/쓰기입니다. 멤버 ID를 포함 하는 파일을 나타내는 문자열을 반환 합니다.  

    - `externalid`. 읽기/쓰기입니다. 함수 멤버 ID를 나타내는 문자열을 반환 합니다.  
  
### <a name="ParentObject"></a> parentObject 속성  
 멤버 함수의 부모 개체를 반환합니다. 예를 들어 `document.getElementByID`, `parentObject` 반환을 `document` 개체입니다. 이 속성은 사용할 수는 `signaturehelp` 이벤트 개체입니다.  
  
 값을 반환 합니다: 개체  
  
### <a name="Target"></a> 대상 속성  
 트리거 문자에 마침표 (.)는 왼쪽 항목을 나타내는 개체를 반환 합니다. 함수에 대 한 `target` 매개 변수 정보를 요청한 대상 함수를 반환 합니다. 이 속성은 사용할 수는 `statementcompletion` 고 `signaturehelp` 이벤트 개체입니다.  
  
 값을 반환 합니다: 개체  
  
### <a name="TargetName"></a> targetName 속성  
 대상을 나타내는 문자열을 반환 합니다. "This.", 예를 들어 `targetName` "this"를 반환 합니다. "A.B" ("B" 뒤에 커서가) 하는 경우에 대 한 `targetName` "B"를 반환 합니다. 이 속성은 사용할 수는 `statementcompletion` 이벤트 개체입니다.  
  
 반환 값: 문자열  
  
### <a name="SymbolHelp"></a> symbolHelp 속성  
 요약 정보 팝업 상자가 요청 되는 완성 항목을 반환 합니다. 이 속성은 사용할 수는 `statementcompletionhint` 이벤트 개체입니다.  
  
 반환 값: `symbolHelp` 개체입니다.  
  
 일부 속성을 `symbolHelp` 개체와 같은 `locid`를 공용으로 해당 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md) 특성.  
  
 다음은의 멤버는 `symbolHelp` 개체:  
  
- `name`. 읽기/쓰기입니다. 식별자 이름을 포함 하는 문자열을 반환 합니다.  
  
- `symbolType`. 읽기/쓰기입니다. 기호 유형을 나타내는 문자열을 반환 합니다. 가능한 값에는 알 수 없는, 부울, 숫자, 문자열, 개체, 함수, 배열, 날짜 및 Regex 포함 됩니다.  
  
- `symbolDisplayType`. 읽기/쓰기입니다. 표시할 유형 이름을 포함 하는 문자열을 반환 합니다. 하는 경우 `symbolDisplayType` 을 설정 하지 않으면 `symbolType` 사용 됩니다.  
  
- `elementType`. 읽기/쓰기입니다. 경우는 `symbolType` 는 `Array`, 배열에 있는 요소의 형식을 나타내는 문자열을 반환 합니다.  
  
- `scope`. 읽기/쓰기입니다. 기호의 범위를 나타내는 문자열을 반환 합니다. 가능한 값 전역, 지역 매개 변수 및 멤버를 포함합니다.  
  
- `description`. 읽기/쓰기입니다. 기호에 대 한 설명을 포함 하는 문자열을 반환 합니다.  
  
- `locid`. 읽기/쓰기입니다. 기호에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.  
  
- `helpKeyword`. 읽기/쓰기입니다. 도움말 키워드를 포함 하는 문자열을 반환 합니다.  
  
- `externalFile`. 읽기/쓰기입니다. 멤버 ID를 포함 하는 파일을 나타내는 문자열을 반환 합니다.  
  
- `externalid`. 읽기/쓰기입니다. 기호의 멤버 ID를 나타내는 문자열을 반환 합니다.  
  
- `functionHelp`. 읽기/쓰기입니다. 반환을 [functionHelp 속성](#FunctionHelp), 정보가 포함 될 수 있는 경우는 `symbolType` 함수입니다.  
  
### <a name="Scope"></a> 속성 범위  
 이벤트의 완료 범위를 반환합니다. 완료에 대 한 가능한 값은 전역 및 멤버의 범위. 이 속성은 사용할 수는 `statementcompletion` 이벤트 개체입니다.  
  
 반환 값: 문자열  
  
## <a name="debugging-intellisense-extensions"></a>IntelliSense 확장명 디버깅  
 확장 프로그램을 디버깅할 수 없습니다 하지만 사용할 수 있습니다 합니다 [intellisense 개체](#intellisenseObject) Visual Studio 출력 창에 정보를 보내는 함수입니다. 이 함수를 사용 하는 방법을 보여 주는 예제를 보려면 [출력 창에 메시지 보내기](#Logging) 이 항목의에서 뒷부분에 있습니다. 에 대 한 `logMessage` 하려면 하나 이상의 이벤트 처리기 확장에 등록 해야 합니다.  
  
## <a name="CodeExamples"></a> 코드 예제  
 이 섹션에는 IntelliSense 확장성 Api를 사용 하는 방법을 보여 주는 코드 예제가 포함 됩니다. 이러한 Api를 사용 하는 다른 방법 있습니다. 추가 예제를 보려면에서 다음 파일을 \\ \\ *Visual Studio 설치 경로*\JavaScript\References 폴더입니다. 이 JavaScript language service를 사용 하는 예제 작업 합니다.  
  
- underscoreFilter.js. 이 코드는 IntelliSense에서 전용 멤버를 숨깁니다. 여기에 대 한 이벤트 처리기는 `statementcompletion` 이벤트입니다.  
  
- showPlainComments.js. 이 코드는 표준 주석에 대 한 IntelliSense 지원을 제공합니다. 여기에 대 한 이벤트 처리기를 `signaturehelp` 고 `statementcompletionhint` 이벤트입니다.  
  
### <a name="Annotations"></a> IntelliSense 주석 추가  
 다음 절차에는 라이브러리를 직접 수정 하지 않고 타사 라이브러리에 대 한 IntelliSense 설명서 지원을 제공 하는 방법을 보여 줍니다. 이 위해 사용할 수 있습니다 `intellisense.annotate` 를 확장 합니다.  
  
 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.  
  
- demoLib.js 타사 라이브러리를 나타내는 프로젝트 파일입니다.  
  
- demoLib.intellisense.js IntelliSense 확장명입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.  
  
- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.  
  
##### <a name="to-add-an-intellisense-annotation"></a>IntelliSense 주석을 추가 하려면  
  
1. DemoLib.js에 다음 코드를 추가 합니다.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2. DemoLib.intellisense.js에 다음 코드를 추가 합니다.  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4. appCode.js에 다음 코드를 입력합니다. IntelliSense 매개 변수 정보를 표시 하는 확장에서 XML 문서 주석을 볼 수 있습니다.  
  
     ![Intellisense.annotate의 사용을 보여 주는](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5. appCode.js에 다음 코드를 입력합니다. 입력 하는 동안 IntelliSense 요약 정보를 표시 하는 확장의 표준 주석을 볼 수 있습니다.  
  
     ![Intellisense.annotate의 사용을 보여 주는](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
### <a name="Logging"></a> 출력 창에 메시지 보내기  
 다음 절차에는 출력 창에 메시지를 보내는 방법을 보여 줍니다. IntelliSense 확장 프로그램을 디버깅 하는 데는 메시지를 보낼 수 있습니다.  
  
 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.  
  
- examplelib.js와, 타사 라이브러리를 나타내는 프로젝트 파일입니다.  
  
- exampleLib.intellisense.js IntelliSense 확장명입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.  
  
- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>출력 창에 메시지를 보내려고  
  
1. Examplelib.js와에 다음 코드를 추가 합니다.  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2. ExampleLib.intellisense.js에 다음 코드를 추가 합니다.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. 출력 창에서 선택 **JavaScript Language Service** 에 **에서 출력 보기** 목록입니다. ([출력] 창을 보려면 **출력** 보기 메뉴에서.)  
  
5. appCode.js에 다음 코드를 입력합니다. 입력 하는 동안 출력 창 언어 서비스에서 메시지를 표시 합니다. 출력 창에서 첫 번째 메시지는 현재 범위에 대 한 문 완성 요청 되었는지 나타냅니다.  
  
    ```javascript  
    some  
    ```  
  
     다음에 표시 되어야 하는 출력의 부분 뷰입니다.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6. 선택 된 **모두 지우기** 출력 창에는 단추입니다.  
  
7. 다음 코드를 입력합니다. 첫 번째 메시지가 출력 창에 멤버 목록을 요청 되었는지 나타냅니다.  
  
    ```javascript  
    someVar.  
    ```  
  
     다음 표시 되어야 하는 출력의 부분 뷰입니다.  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
### <a name="Icons"></a> IntelliSense 아이콘 변경  
 다음 절차에는 기본적으로 IntelliSense에서 표시 되는 아이콘을 변경 하는 방법을 보여 줍니다. 네임 스페이스, 클래스, 인터페이스 및 열거형 등의 라이브러리 관련 개념에 대 한 IntelliSense 정보를 제공 하는 경우에 유용할 수 있습니다.  
  
 사용 가능한 아이콘 값을 참조 하세요. <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>합니다.  
  
 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.  
  
- 프로젝트는 examplelib.js와 해당 represens 타사 라이브러리를 파일입니다.  
  
- exampleLib.intellisense.js IntelliSense 확장명입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.  
  
- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.  
  
##### <a name="to-change-the-icons"></a>아이콘을 변경 하려면  
  
1. Examplelib.js와에 다음 코드를 추가 합니다.  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2. ExampleLib.intellisense.js에 다음 코드를 추가 합니다.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. appCode.js에 다음 코드를 입력합니다. 네임 스페이스에 대 한 아이콘이 변경 되어 있는지 참조를 입력 하는 동안 "{}" 처럼 C#에서 사용 됩니다.  
  
     ![문자 모양 속성의 사용을 보여 주는](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5. appCode.js에 다음 코드를 입력합니다. 입력 하는 동안 Enum1 멤버에 대 한 새 열거형 아이콘 및 SomeClass1 멤버에 대 한 새 클래스 아이콘이 표시 됩니다.  
  
     ![문자 모양 속성의 사용을 보여 주는 예제](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
### <a name="Overriding"></a> 런타임 미치는 IntelliSense 결과 방지합니다.  
 JavaScript language service를 동적으로 IntelliSense 정보를 제공 하는 코드를 실행 합니다. 결과적으로 런타임 동작 원하는 결과 방해할 경우에 따라 수 있습니다. 다음 절차에는 런타임 동작으로 인해 잘못 된 IntelliSense 때 IntelliSense 결과 재정의 하는 방법을 보여 줍니다.  
  
 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.  
  
- examplelib.js와, 타사 라이브러리를 나타내는 프로젝트 파일입니다.  
  
- exampleLib.intellisense.js IntelliSense 확장명입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.  
  
- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>런타임 미치는 IntelliSense 결과 방지 하려면  
  
1. Examplelib.js와에 다음 코드를 추가 합니다.  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     위의 코드에 래핑된 함수의 무시의 값을 기반으로 하는 초기 호출 `count`, 결과 반환 하지 않습니다.  
  
2. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3. appCode.js에 다음 코드를 입력합니다. 래핑된 함수의 호출 되지 않음을 의미 하는 때문에 IntelliSense 대신 식별자 목록 표시 되는 `throttled` 함수 결과 반환 하지 않습니다.  
  
     ![Intellisense 결과 재정의 하는 예가](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4. ExampleLib.intellisense.js에 다음 코드를 추가 합니다. 이 동작이 변경 됩니다 디자인 타임 IntelliSense는 래핑된 함수에 대 한 표시 되도록 예상 대로입니다.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5. AppCode.js에 이전에 입력 한 동일한 코드를 입력 하 여 결과 테스트 합니다. 이 경우 IntelliSense는 원하는 정보를 제공합니다.  
  
     ![IntelliSense 결과 재정의 하는 예가](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>참고 항목  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [식별자 문 완성](../ide/statement-completion-for-identifiers.md)
