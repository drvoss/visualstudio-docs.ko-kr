---
title: XML 편집기 IntelliSense 기능
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 312c304855a450a648b000b8306b80ade969c785
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807980"
---
# <a name="xml-editor-intellisense-features"></a>XML 편집기 IntelliSense 기능

XML 편집기에서는 Visual Studio에서 제공하는 다른 언어 편집기와 비교할 수 있는 완전한 IntelliSense 기능을 제공합니다. 이 단원에서는 XSD(XML 스키마 정의 언어) 및 XSLT 문서와 함께 IntelliSense를 사용하는 방법에 대해 설명합니다.

## <a name="intellisense-in-an-xsd-document"></a>XSD 문서의 IntelliSense

스키마 문서와 연결 되 면 얻게 예상 되는 요소의 드롭다운 목록을 입력 하면 언제 든 지 `"<"` 클릭 또는 합니다 **개체 멤버 목록 표시** XML 편집기 도구 모음 단추입니다.

![표시 개체 멤버 목록 단추](media/display-object-member-list-xml.png)

XML 문서를 사용 하 여 스키마를 연결 하는 방법에 대 한 정보를 참조 하세요 [XML 문서 유효성 검사](../xml-tools/xml-document-validation.md)합니다.

시작 태그 안에서 SPACE를 입력할 때도 현재 요소에 추가할 수 있는 모든 특성을 표시하는 드롭다운 목록이 나타납니다.

특성 값으로 `"="` 또는 값으로 여는 따옴표를 입력할 경우에도 해당 특성에 사용할 수 있는 값 목록이 표시됩니다. 스키마에서 `xsd:enumeration` 패싯을 통해 열거형 값을 제공하거나 특성이 `Boolean` 형식인 경우에만 값이 제공됩니다. `xml:lang`에서 파생되는 모든 `simpleType` 또는 `xsd:language`에 대해서도 알려진 언어 코드의 IntelliSense 목록이 제공됩니다. 네임스페이스 선언에 대해 알려진 `targetNamespace` 값의 IntelliSense 목록이 제공됩니다.

요소가 `">"`인 경우 `simpleType`를 입력하여 시작 태그를 닫을 때도 가능한 값의 IntelliSense 목록이 제공됩니다. 요소의 동작은 이전 단락에서 설명한 특성의 동작과 유사합니다.

이 IntelliSense 목록에는 연결된 스키마에 있는 `xsd:annotation` 및 `xsd:documentation` 정보를 기반으로 도구 설명이 나타납니다.

## <a name="intellisense-in-an-xslt-document"></a>XSLT 문서의 IntelliSense

명명된 템플릿 또는 특성을 XSLT 문서에 추가한 후 IntelliSense를 사용하여 다음을 삽입할 수 있습니다.

- 특성 집합 이름

- 템플릿 노드

- 템플릿 이름

- 제공된 노드의 매개 변수 이름

- 제공된 명명된 템플릿의 매개 변수 이름

자세한 내용은 [연습: XSLT IntelliSense를 사용 하 여](../xml-tools/walkthrough-using-xslt-intellisense.md) 항목입니다.

## <a name="auto-completion"></a>자동 완성

XML 편집기에서는 필수 XML 구문이 자동으로 입력되므로 XML을 쉽게 편집할 수 있습니다. 예를 들어, 다음 시작 태그를 입력하면

`<book>`

끝 태그가 입력되고 커서가 시작 태그 뒤에 놓입니다. 다음은이 예제 (의 "&#124;"은 커서 위치 정보):

`<book>`&#124;`</book>`

특성 값은 항상 따옴표로 묶어야 하기 때문에 XML 편집기에서는 따옴표가 자동으로 입력됩니다. 예를 들어, 다음을 입력하면

`<book title=`

따옴표가 추가되고 따옴표 사이에 커서가 놓입니다.

`<book title="`&#124;`"`

이와 마찬가지로 XML 편집기에서는 다음 XML 구문이 자동으로 삽입됩니다.

- 처리 명령 종료: `?>`

- CDATA 블록 종료: `]]>`

- 주석 종료: `-->`

- DTD 선언 종료: `>`

XML 편집기는 네임 스페이스를 삽입할 수 있습니다 또는 네임 스페이스 정규화 된 요소를 선택 하면 IntelliSense 목록 및 해당 요소 또는 특성에 대 한 네임 스페이스의 특성은 아직 범위 내에 선언 합니다.

예를 들어, 문서에서 선언하지 않은 `e:Book` 네임스페이스에 접두사가 바인딩된 IntelliSense 목록에서 `http://books` 요소를 선택한 경우 XML 편집기에서 필수 네임스페이스 선언이 자동으로 삽입됩니다. 다음은 결과 XML 텍스트입니다.

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>중괄호 일치

XML 편집기에서는 중괄호 강조 기능을 제공하므로 방금 닫은 요소에 대한 피드백을 즉시 얻을 수 있습니다. 바로 가기 키를 사용할 수도 있습니다 (**Ctrl**+**]**) 한 중괄호에서 짝을 이루는 중괄호로 이동할 수 있습니다.

XML 편집기에서는 다음 항목에 대해 이 작업을 수행합니다.

- 일치하는 시작 태그와 끝 태그

- 쌍 "\<" 또는 ">" 꺾쇠 괄호입니다.

- 주석의 시작과 끝

- 처리 명령의 시작과 끝

- CDATA 블록의 시작과 끝

- DTD 선언의 시작과 끝

- 특성의 여는 따옴표와 닫는 따옴표

## <a name="modify-the-intellisense-options"></a>IntelliSense 옵션 수정

IntelliSense 및 자동 완성 기능은 기본적으로 활성화되어 있습니다. 수정 하 여이 변경할 수는 있지만 하 **도구** > **옵션** 설정 합니다.

합니다 **자동 삽입** 섹션을 **기타** 다음 동작을 제어 하는 페이지:

|이름|설명|
|-|-----------------|
|닫기 태그|새 요소에 대해 닫기 태그를 삽입합니다.|
|특성 따옴표|새 특성 이름을 입력할 때 특성 값 따옴표를 삽입합니다.|
|기타 태그|주석, CDATA, DOCTYPE, 처리 명령 및 기타 태그 선언을 완성합니다.|

### <a name="to-change-the-auto-completion-behavior"></a>자동 완성 동작을 변경하려면

1. **도구** 메뉴에서 **옵션**을 선택합니다.

2. 확장 **텍스트 편집기**를 확장 하 고 **XML**를 선택 하 고 **기타**.

3. 아무 것도 변경 합니다 **자동 삽입** 섹션을 클릭 **확인**합니다.

## <a name="see-also"></a>참고자료

- [XML 편집기](../xml-tools/xml-editor.md)
- [IntelliSense 사용](../ide/using-intellisense.md)
- [연습: XSLT IntelliSense 사용](../xml-tools/walkthrough-using-xslt-intellisense.md)