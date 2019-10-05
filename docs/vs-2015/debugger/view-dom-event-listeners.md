---
title: DOM 이벤트 수신기 보기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693582"
---
# <a name="view-dom-event-listeners"></a>DOM 이벤트 수신기 보기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 및 Windows Phone 적용 됩니다] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 합니다 **이벤트** DOM 탐색기의 탭에는 DOM 요소와 연결 된 이벤트를 표시 합니다. 각각의 최상위 노드를 **이벤트** 탭 활성 구독자가 있는 이벤트를 나타냅니다. 최상위 노드에는 특정 이벤트에 대해 등록된 이벤트 수신기를 나타내는 하위 노드가 포함되어 있습니다. 이벤트를 수신기를 볼 수 있을뿐 아니라 이 탭을 사용하여 JavaScript 코드에서 이벤트 수신기 위치를 탐색할 수도 있습니다. 이 항목의 내용은 HTML 및 JavaScript로 작성된 스토어 앱에 적용됩니다.

 목록에는 **이벤트** 탭은 동적입니다. 앱 실행 중에 이벤트 수신기를 추가하면 목록에 새 이벤트 수신기가 나타납니다. 이벤트 수신기 추가 및 제거에 대 한 정보를 참조 하세요 [이벤트 수신기를 사용 하 여 문제를 해결 하기 위한 팁](#Tips) 이 항목의 합니다.

> [!NOTE]
> DOM 요소를 같은 하지 않은 코드 요소에 대 한 이벤트 수신기 `xhr`에 표시 되지 않습니다 합니다 **이벤트** 탭 합니다.

## <a name="view-event-listeners-for-dom-elements"></a>DOM 요소의 이벤트 수신기 보기
 이 예에는 Windows Phone 스토어 앱이 나와 있습니다. 여기서 설명하는 DOM 탐색기 기능은 Windows 스토어 앱에서도 지원됩니다.

#### <a name="to-view-event-listeners"></a>이벤트 수신기를 보려면

1. Visual Studio에서 Windows Phone 피벗 애플리케이션 프로젝트 템플릿을 사용하는 JavaScript 앱을 만듭니다.

2. Visual Studio에서 열기 템플릿으로 선택 **에뮬레이터 8.1 WVGA 4 인치 512MB** 디버거의 디버그 도구 모음의 드롭다운 목록에서:

     ![디버그 대상 선택](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. F5 키를 눌러 디버그 모드에서 응용 프로그램을 실행합니다.

4. 실행 중인 앱으로 이동 합니다 **섹션 3** 피벗 항목입니다.

5. Visual Studio로 전환합니다(Alt+Tab 또는 F12).

6. DOM 탐색기의 오른쪽 상단에 있는 `Find`를 선택합니다.

7. `ListView`를 입력한 후 Enter 키를 누릅니다.

8. 필요한 경우 선택 합니다 **다음** 단추를를 `DIV` 나타내는 요소는 `ListView` 컨트롤 (이 요소에는 `data-win-control` 값 `WinJS.UI.ListView`).

     이제 DOM 탐색기에서 `DIV` 요소를 선택할 수 있습니다.

9. 선택 된 **이벤트** DOM 탐색기의 오른쪽 창에서 탭 합니다.

     이제 다음과 같이 `DIV` 요소에 대한 활성 구독자가 있는 이벤트를 볼 수 있습니다.

     ![DOM 탐색기의 이벤트 탭](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. 이러한 이벤트에 대한 이벤트 수신기를 찾으려면 연결된 JavaScript 파일 링크를 선택합니다.

11. DOM 계층 구조에서 부모 요소에 대한 이벤트 수신기를 신속하게 식별하려면 DOM 탐색기의 맨 아래 있는 계층 구조 목록에서 부모 요소를 선택합니다.

     ![DOM 계층에서 부모 요소 선택](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     합니다 **이벤트** 탭 계층 목록에서 선택 하는 모든 요소에 대 한 이벤트 수신기가 표시 됩니다.

### <a name="Tips"></a> 이벤트 수신기를 사용 하 여 문제를 해결 하기 위한 팁
 일부 앱 시나리오에서는 이벤트 수신기 제거 해야 합니다 명시적으로 사용 하 여 [removeEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)합니다. 사용 된 **이벤트** 코드를 실행 하는 동안 DOM 요소에서 이벤트 수신기가 제거 되었는지 여부를 테스트 하려면 DOM 탐색기에서 탭 합니다. 아래 이러한 유형의 문제를 해결할 수 있는 팁이 몇 가지 나와 있습니다.

- Visual Studio에서 구현 되는 단일 페이지 탐색 모델을 사용 하는 앱에 대 한 [프로젝트 템플릿](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx), 일반적으로 페이지의 일부인 DOM 요소 등의 개체에 대 한 등록 된 이벤트 수신기를 제거할 필요는 없습니다. 이 시나리오에서 DOM 요소 및 연결된 이벤트 수신기는 수명이 동일하고 가비지 수집될 수 있습니다.

- DOM 요소 또는 개체의 수명이 연결된 수신기와 다르면 `removeEventListener` 메서드를 호출해야 할 수 있습니다. 예를 들어 `window.onresize` 이벤트를 사용하는 경우 이벤트를 처리하는 페이지를 벗어나 탐색하면 이벤트 수신기를 제거해야 할 수 있습니다.

- `removeEventListener`가 지정된 수신기를 제거하지 못할 경우 개체의 다른 인스턴스에서 호출되고 있는 중일 수 있습니다. 사용할 수는 [bind 메서드 (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) 수신기를 추가 하면이 문제를 해결 하는 방법입니다.

- 사용 하 여 추가 된 이벤트 수신기를 제거 하려면 [bind 메서드 (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) 또는 수신기를 추가 하면 익명 함수를 사용 하 여 함수의 인스턴스를 저장 합니다. 아래 이러한 패턴을 안전하게 사용하는 방법이 한 가지 나와 있습니다.

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     바인딩된 함수에 참조를 저장하는 대신 다음 코드를 사용할 경우 이벤트 수신기를 명시적으로 제거하지 못할 수 있습니다.

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- `removeEventListener` 특성(예: `obj.on<eventname>`)을 사용하여 이벤트 수신기를 추가한 경우에는 `window.onresize = handlerFunc`를 사용하여 제거할 수 없습니다.

- JavaScript 메모리 분석기를 사용 하 여 [JavaScript 메모리](../profiling/javascript-memory.md) 앱에서. 명시적으로 제거해야 하는 이벤트 수신기는 메모리 누수로 나타날 수 있습니다.

## <a name="see-also"></a>참고 항목

- [빠른 시작: HTML 및 CSS 디버그](../debugger/quickstart-debug-html-and-css.md)
- [DOM 탐색기를 사용하여 CSS 스타일 디버그](../debugger/debug-css-styles-using-dom-explorer.md)
- [DOM 탐색기를 사용하여 레이아웃 디버그](../debugger/debug-layout-using-dom-explorer.md)