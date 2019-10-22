---
title: XSLT 스타일 시트 디버그
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c1f774757acc293091f19a783ed93f34647d494
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604606"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>연습: XSLT 스타일 시트 디버깅

이 연습 단계에서는 XSLT 디버거를 사용하는 방법을 보여 줍니다. 이 단계에는 변수 보기, 중단점 설정 및 단계별로 코드 실행이 포함됩니다. 디버거를 사용 하면 한 번에 한 줄씩 코드를 실행할 수 있습니다.

이 연습을 준비 하려면 먼저 두 [샘플 파일](#sample-files) 을 로컬 컴퓨터에 복사 합니다. 하나는 스타일 시트이 고 하나는 스타일 시트에 대 한 입력으로 사용할 XML 파일입니다. 이 연습에서 사용 하는 스타일 시트는 비용이 평균 책 가격 미만인 모든 책을 찾습니다.

> [!NOTE]
> XSLT 디버거는 Visual Studio의 Enterprise edition 에서만 사용할 수 있습니다.

## <a name="start-debugging"></a>디버깅 시작

1. **파일** 메뉴에서  > **파일** **열기** 를 선택 합니다.

2. *Below-average* 파일을 찾아 **열기**를 선택 합니다.

   XML 편집기에서 스타일 시트가 열립니다.

3. 문서 속성 창의 **입력** 필드에서 찾아보기 단추 ( **...** )를 클릭 합니다. ( **속성** 창이 표시 되지 않으면 편집기에서 열린 파일의 아무 곳 이나 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.)

4. *Books.xml* 파일을 찾은 다음 **열기**를 선택 합니다.

   이렇게 하면 XSLT 변환에 사용 되는 소스 문서 파일이 설정 됩니다.

5. *Below-average*의 12 줄에 [중단점](../debugger/using-breakpoints.md) 을 설정 합니다. 여러 가지 방법 중 하나로이 작업을 수행할 수 있습니다.

   - 12 줄에서 편집기의 여백을 클릭 합니다.

   - 12 줄에서 아무 곳 이나 클릭 한 다음 **F9**키를 누릅니다.

   - @No__t_0 시작 태그를 마우스 오른쪽 단추로 클릭 한 다음 중단점 ** > ** 중단점**삽입**을 선택 합니다.

      ![Visual Studio에서 XSL 파일에 중단점 삽입](media/insert-breakpoint.PNG)

6. 메뉴 모음에서 **XML**  > **XSLT 디버깅 시작** 을 선택 하거나 **Alt** +**f5**키를 누릅니다.

   디버깅 프로세스가 시작 됩니다.

   편집기에서 디버거는 스타일 시트의 `xsl:if` 요소에 배치 됩니다. *Below-average* 라는 다른 파일이 편집기에서 열립니다. 이 파일은 입력 파일 *books.xml* 의 각 노드가 처리 될 때 채워질 출력 파일입니다.

   **자동**, **지역**및 **조사식 1** 창이 Visual Studio 창의 아래쪽에 나타납니다. **지역** 창에 모든 지역 변수 및 현재 값이 표시 됩니다. 여기에는 스타일시트에 정의된 변수가 포함되며 디버거에서 현재 컨텍스트에 있는 노드를 추적하는 데 사용하는 변수도 포함됩니다.

## <a name="watch-window"></a>조사식 창

입력 파일이 처리 될 때 값을 검사할 수 있도록 **조사식 1** 창에 두 개의 변수를 추가 합니다. 보려는 변수가 이미 있는 경우 **지역** 창을 사용 하 여 값을 검사할 수도 있습니다.

1. **디버그** 메뉴에서 **Windows**  > **조사식**  > **조사식 1**을 선택 합니다.

   **조사식 1** 창이 표시 됩니다.

2. **이름** 필드에 `$bookAverage`를 입력 하 고 **enter**키를 누릅니다.

   @No__t_0 변수의 값은 **값** 필드에 표시 됩니다.

3. 다음 줄에서 **이름** 필드에 `self::node()`를 입력 하 고 **enter**키를 누릅니다.

   `self::node()`는 현재 컨텍스트 노드로 계산되는 XPath 식입니다. `self::node()` XPath 식의 값은 첫 번째 book 노드입니다. 이 값은 변환을 진행하면서 변경됩니다.

4. @No__t_0 노드를 확장 한 다음 값이 `price` 인 노드를 확장 합니다.

   ![Visual Studio에서 XSLT 디버깅 중 조사식 창](media/xslt-debugging-watch-window.png)

   현재 책 노드의 책 가격 값을 확인 하 여 `$bookAverage` 값과 비교할 수 있습니다. 책 가격은 평균 미만이 기 때문에 디버깅 프로세스를 계속할 때 `xsl:if` 조건이 성공 해야 합니다.

## <a name="step-through-the-code"></a>코드를 단계별로 실행 합니다.

1. **F5**를 눌러 계속합니다.

   첫 번째 책 노드가 `xsl:if` 조건을 충족 하기 때문에 book 노드가 *below-average* 출력 파일에 추가 됩니다. 디버거는 스타일시트의 `xsl:if` 요소에 다시 배치될 때까지 계속 실행됩니다. 이제 디버거가 *books.xml* 파일의 두 번째 book 노드에 배치 됩니다.

   **조사식 1** 창에서 `self::node()` 값이 두 번째 book 노드로 변경 됩니다. 가격 요소 값을 검사하여 가격이 평균을 초과하는 것을 확인할 수 있으므로 `xsl:if` 조건은 실패해야 합니다.

2. **F5**를 눌러 계속합니다.

   두 번째 book 노드가 `xsl:if` 조건을 충족 하지 않으므로 book 노드가 *below-average* 출력 파일에 추가 되지 않습니다. 디버거는 스타일 시트의 `xsl:if` 요소에 다시 배치 될 때까지 계속 실행 됩니다. 이제 디버거가 *books.xml* 파일의 세 번째 `book` 노드에 배치 됩니다.

   **조사식 1** 창에서 `self::node()` 값이 세 번째 book 노드로 변경 됩니다. @No__t_0 요소의 값을 검사 하 여 가격이 평균 미만인 지 확인할 수 있습니다. @No__t_0 조건이 성공 합니다.

3. **F5**를 눌러 계속합니다.

   @No__t_0 조건이 충족 되었으므로 세 번째 책이 *below-average* 출력 파일에 추가 됩니다. XML 문서에 있는 모든 book이 처리되었으므로 디버거가 중지됩니다.

## <a name="sample-files"></a>샘플 파일

다음 두 파일은 연습에 사용됩니다.

### <a name="below-averagexsl"></a>below-average

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>참조

- [XSLT 디버그](../xml-tools/debugging-xslt.md)