---
title: JavaScript IntelliSense에 대 한 JSDoc 주석 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4d300651731b38b9b86421d36d9de169dc6464d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188782"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>JavaScript IntelliSense에 대한 JSDoc 주석 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 IntelliSense는 표준 JSDoc 주석을 사용하여 스크립트에 추가하는 정보를 표시합니다. JSDoc 주석을 사용하여 함수, 필드 및 변수와 같은 코드 요소에 대한 정보를 제공할 수 있습니다.  

## <a name="jsdoc-comment-tags"></a>JSDoc 주석 태그  
 다음과 같은 표준 JSDoc 주석 태그는 IntelliSense에서 코드에 대한 정보를 표시하는 데 사용됩니다.  

|  JSDoc 태그   |                       구문                        |                                                     참고                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *설명*              |                                   사용되지 않는 함수 또는 메서드를 지정합니다.                                   |
| @description |             @description *설명*              |                              함수 또는 메서드에 대한 설명을 지정합니다.                               |
|    @param    | @param {*type*} *parameterName*<em>description</em> | 함수 또는 메서드의 매개 변수에 대한 정보를 지정합니다.<br /><br /> TypeScript 지원 @paramTag합니다. |
|  @property   |          @property {*type*} *propertyName*          |   설명을 포함하여 개체에 정의된 필드 또는 멤버에 대한 정보를 지정합니다.    |
|   @returns   |                  @returns {*type*}                  |           반환 값을 지정합니다.<br /><br /> TypeScript를 사용 하 여 @returnType 대신 @returns합니다.           |
|   @summary   |               @summary *설명*                |                   함수 또는 메서드에 대 한 설명을 지정 합니다 (동일 @description).                   |
|    @type     |                   @type {*type*}                    |                                상수 또는 변수의 형식을 지정합니다.                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            사용자 지정 형식을 지정합니다.                                            |

### <a name="examples"></a>예  
 다음 예제에서는 사용 합니다 @description, @param, 및 @return 라는 함수에 대 한 JSDoc 태그 `getArea`합니다.  

```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  

 앞의 예제에서 IntelliSense는 `getArea`에 대한 여는 괄호를 입력할 때 설명, 매개 변수 및 반환 정보를 표시합니다.  

 ![함수에 대 한 IntelliSense 정보](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  

 다음 예제에서는 사용 하는 방법을 보여 줍니다 합니다 @typedef 사용 하 여 태그를 @property 태그입니다.  

```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  

var w = new Weather();  
```  

 다음 예제에서는 사용 된 @type JSDoc 태그입니다. 이 예제와 같이 초기 별표 쌍(\*\*) 뒤에 오는 단일 별표(*)는 필요하지 않습니다.  

```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  

```  

 다음 예제에서는 사용 하는 방법의 @deprecated JSDoc 태그입니다.  

```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```
