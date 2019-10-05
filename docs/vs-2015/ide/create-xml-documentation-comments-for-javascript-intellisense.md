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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9fba6ff1b4c56243a47c8b136a25d6f9d593d8e3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701253"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>JavaScript IntelliSense에 대한 XML 문서 주석 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML 문서 주석* JavaScript 함수, 필드 및 변수와 같은 코드 요소에 대 한 정보를 제공 하는 스크립트를 추가 하는 주석이 됩니다. Visual Studio에서 이러한 텍스트 설명은 스크립트 함수를 참조 하는 경우에 IntelliSense를 사용 하 여 표시 됩니다.  
  
 이 항목에서는 XML 문서 주석을 사용 하 여 기본 자습서를 제공 합니다. 와 같은 다른 요소를 사용 하는 방법은 [ \<var >](../ide/var-javascript.md) 하 고 [ \<값 >](../ide/value-javascript.md), 추가 코드 예제에 대 한 참조 및 [XML 문서 주석 ](../ide/xml-documentation-comments-javascript.md). 와 같은 비동기 콜백이 대 한 IntelliSense 정보를 제공 하는 것에 대 한 자세한를 `Promise`를 참조 하세요 [ \<반환 >](../ide/returns-javascript.md)합니다.  
  
> [!NOTE]
> 참조된 파일, 어셈블리 및 서비스에서만 XML 문서 주석을 사용할 수 있습니다.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>에 JavaScript 함수에 대 한 XML 문서 주석 만들기  
  
- 함수에서 추가 [ \<요약 >](../ide/summary-javascript.md)를 [ \<param >](../ide/param-javascript.md), 및 [ \<반환 >](../ide/returns-javascript.md) 요소를 사용 하 여 각 요소 앞에 야 하 고 3 개의 슬래시 (/ / /) 표시 합니다.  
  
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
  
- XML 문서 주석이 보려면 이름과 다음 예제와 같이 XML 문서 주석으로 표시 된 함수의 여는 괄호를 입력 합니다.  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     XML 문서 주석이 포함 된 함수의 여는 괄호를 입력 하면 코드 편집기 IntelliSense를 사용 하 여 XML 문서 주석에서 정의한 정보를 표시 합니다.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>JavaScript 필드에 대 한 XML 문서 주석을 만들려면  
  
- 생성자 함수 또는 개체 정의에 추가 된 [ \<필드 >](../ide/field-javascript.md) 요소 앞에 세 개의 슬래시 기호 (/ / /).  
  
     다음 예제에서는 사용을 보여 줍니다.는 `<field>` 생성자 함수에는 요소입니다. 추가 예제를 보려면 [ \<필드 >](../ide/field-javascript.md)합니다.  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
- XML 문서 주석이 보려면 다음 예제와 같이 XML 문서 주석으로 표시 되는 function 생성자를 사용 하 여 개체를 만듭니다.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
- 다음 줄에 개체 이름과 필드에 대 한 IntelliSense 정보를 표시할 기간을 입력 합니다.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>에 오버 로드 된 함수에 대 한 XML 문서 주석 만들기  
  
1. 함수에서 추가 된 [ \<서명 >](../ide/signature-javascript.md) 각 오버 로드에 대 한 요소입니다. 이러한 요소를 다른 요소를 추가 같은 `<summary>`, `<param>`, 및 `<returns>`, 3 개의 슬래시 기호 (/ / /)를 사용 하 여 각 요소 앞입니다.  
  
     다음 예제에서는 오버 로드 된 JavaScript 함수를 보여 줍니다. 이 예제에서는 오버 로드 매개 변수 형식에서 다릅니다.  
  
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
  
2. XML 문서 주석이 보려면 이름과 다음 예제와 같이 XML 문서 주석으로 표시 된 함수의 여는 괄호를 입력 합니다.  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>지역화 된 IntelliSense를 만들려면  
  
1. OpenAjax MessageBundle 형식으로 문서 주석이 포함 된 XML 파일을 만듭니다.  
  
    > [!IMPORTANT]
    > MessageBundle 권장 되는 형식입니다. 이 형식은.winmd 파일 또는 Microsoft Ajax에서 지원 되지 않습니다. 대체를 사용 하 여에 대 한 자세한 `VSDoc` 형식을 참조 하십시오 [ \<loc >](../ide/loc-javascript.md)합니다.  
  
     다음 예제에서는 지역화 된 IntelliSense 정보를 포함 하는 사이드카 파일의 콘텐츠를 보여 줍니다. 이것이 일본 같은 문화권별 폴더에 있는 XML 파일입니다. 폴더는 포함 된.js 파일을 동일한 위치에 있어야 합니다 `<loc>` 요소입니다. XML 파일의 파일 이름은 일치 해야 합니다 `filename` 에 지정 된 매개 변수는 `<loc>` 요소입니다.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2. .Js 파일에 다음 코드를 추가 합니다. 합니다 `<loc>` 요소의 다른 스크립트 보다 먼저 선언 되어야 하며와 동일한 사용 규칙을 따릅니다는 `<reference>` 요소입니다. 자세한 내용은 [JavaScript IntelliSense](../ide/javascript-intellisense.md) 하 고 [ \<loc >](../ide/loc-javascript.md)합니다.  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3. .Js 파일에는 XML 문서 요소 및 기본 설명을 추가 합니다. 설정 된 `locid` 특성 값을 해당 일치 `name` 사이드카 파일에서 특성 값입니다. 사용 가능한 경우 기본 설명은 지역화 된 IntelliSense 정보로 바뀝니다.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4. XML 문서 주석이 보려면 이름과 다음 예제와 같이 함수의 여는 괄호를 입력 합니다.  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)   
 [NIB: 연습: ASP.NET의 JavaScript IntelliSense](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
