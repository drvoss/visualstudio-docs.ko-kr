---
title: '&lt;loc &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651473"
---
# <a name="ltlocgt-javascript"></a>&lt;loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지역화 된 IntelliSense 정보를 제공 하는 사이드카 파일의 위치 및 유형을 지정 합니다.

## <a name="syntax"></a>구문

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>매개 변수
 `filename` 선택 사항입니다. 중립 문화권에 대 한 지역화 정보를 포함 하는 사이드카 파일의 루트 이름입니다. Visual Studio에서 지역화 정보를 검색 하는 경우이 파일의 문화권별 버전을 찾으려고 시도 합니다. 예를 들어 `filename`가 jquery .xml 인 경우 Visual Studio는 `<loc>` 요소를 포함 하는 .js 파일과 동일한 위치에 있는 올바른 문화권별 폴더 (예: JA-JP)를 검색 합니다. 문화권별 폴더를 찾으면 jquery 파일이 있는지 여부를 확인 합니다. 올바른 파일을 찾을 수 없는 경우 대신 관리 되는 리소스 위치 규칙을 사용 합니다. @No__t_0의 기본값은 현재 파일의 이름이 며 .js 대신 확장명이 .xml입니다.

 `format` 선택 사항입니다. 지역화에 사용 되는 사이드카 파일의 형식입니다. Open Ajax 메타 데이터로 정의 된 메시지 번들의 사용을 지정 하려면 `messagebundle`을 사용 합니다. `messagebundle`은 권장 되는 형식입니다. 그러나이 형식은 Microsoft Ajax 나 winmd 파일에서 지원 되지 않습니다. @No__t_0를 사용 하 여 Microsoft Ajax 및 Windows 런타임에서 사용 하는 표준 .NET Framework 지역화 형식을 지정할 수 있습니다. 이 특성은 선택적 요소입니다. `vsdoc` 기본 형식입니다.

## <a name="remarks"></a>설명
 @No__t_0 요소는 파일의 맨 위에 `<reference>` 요소와 같은 섹션에 표시 되어야 합니다. @No__t_0 요소에 대 한 사용 규칙은 `<reference>` 요소와 동일 합니다. 자세한 내용은 [JavaScript IntelliSense](../ide/javascript-intellisense.md)의 "참조 지시문" 섹션을 참조 하세요.

 Visual Studio는 각 .js 파일에 대해 단일 `<loc>` 요소를 처리 합니다. 여러 `<loc>` 요소가 있으면 단일 `<loc>` 요소만 사용 됩니다. 사용할 `<loc>` 요소를 결정 하는 동작은 정의 되지 않습니다.

 메시지 번들 형식을 사용 하는 경우 XML 문서 주석의 `locid` 특성을 사용 하 여 `name` 특성 값을 지정 합니다.

## <a name="example"></a>예
 다음 예제에서는 messagebundle 형식으로 `<loc>` 요소를 사용 하는 방법을 보여 줍니다. MessageFilename .xml 이라는 파일에 다음 XML을 추가 하 고 `filename` 매개 변수 설명에 지정 된 대로 올바른 문화권별 폴더에 파일을 저장 합니다.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Messagebundle 예제의 경우 프로젝트의 JavaScript 파일에 다음 코드를 추가 합니다. @No__t_0 요소는 JavaScript 파일의 첫 번째 줄로 표시 되어야 합니다. 이 코드의 설명은 지역화 된 설명으로 대체 됩니다 (사용 가능한 경우).

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 다음 예에서는 VSDoc 형식을 사용 합니다. ScriptFilename .xml 이라는 파일에 다음 XML을 추가 하 고 올바른 문화권별 폴더에 파일을 저장 합니다.

```
<?xml version="1.0" encoding="utf-8" ?>
<doc>
  <assembly>
    <name>Lights</name>
  </assembly>
  <members>
    <member name="M:illuminate">
      <summary>Activates a light. </summary>
      <param name='a'>The light to activate. </param>
    </member>
  </members>
</doc>

```

 VSDoc 예제의 경우 프로젝트의 JavaScript 파일에 다음 코드를 추가 합니다. 이 코드의 설명은 지역화 된 설명으로 대체 됩니다 (사용 가능한 경우).

```javascript
/// <loc filename="scriptFilename.xml" format="vsdoc" />

function illuminate(a)
{
    /// <summary locid='M:illuminate'>description</summary>
    /// <param name='a' type='Number'>parameter a description</param>
}

```

## <a name="see-also"></a>참고 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
