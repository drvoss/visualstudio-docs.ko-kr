---
title: JavaScript IntelliSense에 대 한 XML 문서 주석 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619542"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>JavaScript IntelliSense에 대한 XML 문서 주석 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML 문서 주석은* 함수, 필드 및 변수와 같은 코드 요소에 대 한 정보를 제공 하기 위해 스크립트에 추가 하는 JavaScript 주석입니다. Visual Studio에서는 스크립트 함수를 참조할 때 이러한 텍스트 설명이 IntelliSense를 사용 하 여 표시 됩니다.

 이 항목에서는 XML 문서 주석을 사용 하는 방법에 대 한 기본 자습서를 제공 합니다. [@No__t_1var >](../ide/var-javascript.md) 및 [\<value >](../ide/value-javascript.md)와 같은 다른 요소를 사용 하는 방법에 대 한 자세한 내용은 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)을 참조 하세요. @No__t_0와 같은 비동기 콜백에 대 한 IntelliSense 정보를 제공 하는 방법에 대 한 자세한 내용은 [\<returns >](../ide/returns-javascript.md)를 참조 하세요.

> [!NOTE]
> 참조된 파일, 어셈블리 및 서비스에서만 XML 문서 주석을 사용할 수 있습니다.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>JavaScript 함수에 대 한 XML 문서 주석을 만들려면

- 함수에서 [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)및 [\<returns](../ide/returns-javascript.md) 요소를 추가 하 고 각 요소 앞에 세 개의 슬래시 표시 (///)를 추가 합니다.

    > [!NOTE]
    > 각 요소는 한 줄에 있어야 합니다.

     다음 예제에서는 JavaScript 함수를 보여 줍니다.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- XML 문서 주석을 보려면 다음 예제와 같이 XML 문서 주석으로 표시 된 함수의 이름 및 여는 괄호를 입력 합니다.

    ```javascript
    var areaVal = getArea(
    ```

     XML 문서 주석을 포함 하는 함수의 여는 괄호를 입력 하면 코드 편집기에서 IntelliSense를 사용 하 여 XML 문서 주석에 정의 된 정보를 표시 합니다.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>JavaScript 필드에 대 한 XML 문서 주석을 만들려면

- 생성자 함수 또는 개체 정의에서 앞에 세 개의 슬래시 기호 (///)가 있는 [\<field >](../ide/field-javascript.md) 요소를 추가 합니다.

     다음 예제에서는 생성자 함수에서 `<field>` 요소를 사용 하는 방법을 보여 줍니다. 추가 예제는 [\<field >](../ide/field-javascript.md)를 참조 하세요.

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- XML 문서 주석을 보려면 다음 예제와 같이 XML 문서 주석으로 표시 된 함수 생성자를 사용 하 여 개체를 만듭니다.

    ```javascript
    var eng = new Engine();
    ```

- 다음 줄에서 개체 이름 및 필드에 대 한 IntelliSense 정보를 표시 하는 마침표를 입력 합니다.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>오버 로드 된 함수에 대 한 XML 문서 주석을 만들려면

1. 함수에서 각 오버 로드에 대 한 [\<signature >](../ide/signature-javascript.md) 요소를 추가 합니다. 이러한 요소에는 `<summary>`, `<param>` 및 `<returns>`와 같은 다른 요소를 추가 합니다. 각 요소 앞에는 세 개의 슬래시 기호 (///)가 있습니다.

     다음 예제에서는 오버 로드 된 JavaScript 함수를 보여 줍니다. 이 예제에서 오버 로드는 매개 변수 형식에 따라 다릅니다.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. XML 문서 주석을 보려면 다음 예제와 같이 XML 문서 주석으로 표시 된 함수의 이름과 여는 괄호를 입력 합니다.

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>지역화 된 IntelliSense를 만들려면

1. OpenAjax MessageBundle 형식의 문서 주석을 포함 하는 XML 파일을 만듭니다.

    > [!IMPORTANT]
    > MessageBundle은 권장 되는 형식입니다. 이 형식은 Microsoft Ajax 나 winmd 파일에서 지원 되지 않습니다. 대체 `VSDoc` 형식을 사용 하는 방법에 대 한 자세한 내용은 [\<loc >](../ide/loc-javascript.md)를 참조 하세요.

     다음 예제에서는 지역화 된 IntelliSense 정보를 포함 하는 사이드카 파일의 내용을 보여 줍니다. 이 파일은 JA-JP와 같은 문화권별 폴더에 있는 XML 파일입니다. 폴더는 `<loc>` 요소를 포함 하는 .js 파일과 동일한 위치에 있어야 합니다. XML 파일의 파일 이름은 `<loc>` 요소에 지정 된 `filename` 매개 변수와 일치 해야 합니다.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. .Js 파일에서 다음 코드를 추가 합니다. @No__t_0 요소는 스크립트 보다 먼저 선언 해야 하며, `<reference>` 요소와 같은 사용 규칙을 따라야 합니다. 자세한 내용은 [JavaScript IntelliSense](../ide/javascript-intellisense.md) 및 [\<loc >](../ide/loc-javascript.md)를 참조 하세요.

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. .Js 파일에 XML 문서 요소와 기본 설명을 추가 합니다. 사이드카 파일에서 해당 `name` 특성 값과 일치 하도록 `locid` 특성 값을 설정 합니다. 기본 설명은 지역화 된 IntelliSense 정보로 대체 됩니다 (사용 가능한 경우).

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. XML 문서 주석을 보려면 다음 예제와 같이 함수의 이름과 여는 괄호를 입력 합니다.

    ```javascript
    add(
    ```

## <a name="see-also"></a>관련 항목:
 [Javascript intellisense](../ide/javascript-intellisense.md) [XML 문서 주석](../ide/xml-documentation-comments-javascript.md) [NIB: 연습: ASP.NET의 javascript IntelliSense](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
