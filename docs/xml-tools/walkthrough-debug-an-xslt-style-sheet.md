---
title: XSLT 스타일 시트 디버깅
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808482"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>연습: XSLT 스타일시트 디버그

이 연습 단계에서는 XSLT 디버거를 사용하는 방법을 보여 줍니다. 이 단계에는 변수 보기, 중단점 설정 및 단계별로 코드 실행이 포함됩니다. 디버거를 사용 하면 한 번에 한 줄씩 코드를 실행할 수 있습니다.

이 연습을 준비 하려면 먼저 두 복사 [샘플 파일](#sample-files) 로컬 컴퓨터에 있습니다. 스타일 시트 하나 이며 하나는 XML 파일 스타일 시트에 대 한 입력으로 사용 됩니다. 이 연습에서는 스타일 시트를 사용 하 여 가격이 평균도 서 가격 보다는 모든 온라인 설명서를 찾습니다.

> [!NOTE]
> XSLT 디버거만 Visual Studio의 Enterprise edition에서 제공 됩니다.

## <a name="start-debugging"></a>디버깅 시작

1. **파일** 메뉴 선택 **열려** > **파일**합니다.

2. 찾을 합니다 *average.xsl 아래* 파일을 선택 **오픈**합니다.

   스타일 시트를 XML 편집기에서 열립니다.

3. 찾아보기 단추를 클릭 (**...** )에 **입력** 문서 속성 창의 필드입니다. (경우 합니다 **속성** 창이 표시 되지 않으면 편집기에서 열려 있는 파일에서 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 선택한 **속성**.)

4. 찾을 합니다 *books.xml* 파일을 선택한 후 **오픈**합니다.

   XSLT 변형에 사용 되는 소스 문서 파일이 설정 합니다.

5. 설정을 [중단점](../debugger/using-breakpoints.md) 에 줄의 12 *average.xsl 아래*합니다. 여러 가지 방법 중 하나에서이 수행할 수 있습니다.

   - 줄 12에 대 한 편집기의 여백에 여기를 클릭 합니다.

   - 12 줄의 아무 곳 이나 클릭 한 다음 **F9**합니다.

   - 마우스 오른쪽 단추로 클릭 합니다 `xsl:if` 태그를 시작 하 고 선택한 **중단점** > **중단점 삽입**합니다.

      ![Visual Studio에서 XSL 파일에서 중단점을 삽입 합니다.](media/insert-breakpoint.PNG)

6. 메뉴 모음에서 선택 **XML** > **XSLT 디버깅 시작** (또는 키를 누릅니다 **Alt**+**F5**).

   디버깅 프로세스를 시작 합니다.

   편집기에서 디버거에 배치 되는 `xsl:if` 스타일 시트의 요소입니다. 라는 다른 파일 *average.xml 아래* ; 편집기에서 열립니다는 출력 파일은 입력된 파일의 각 노드로 채워집니다입니다 *books.xml* 처리 됩니다.

   합니다 **자동**를 **지역**, 및 **조사식 1** 창이 Visual Studio 창의 맨 아래에 표시 합니다. 합니다 **지역** 는 모든 지역 변수와 해당 현재 값 창에 표시 됩니다. 여기에는 스타일시트에 정의된 변수가 포함되며 디버거에서 현재 컨텍스트에 있는 노드를 추적하는 데 사용하는 변수도 포함됩니다.

## <a name="watch-window"></a>조사식 창

두 개의 변수를 추가 합니다 **조사식 1** 창이 입력된 파일을 처리 하는 해당 값 검사할 수 있습니다. (사용할 수도 있습니다는 **지역** 창 조사 하려는 변수는 이미 있는 경우 값을 검토 합니다.)

1. **디버그** 메뉴 선택 **Windows** > **조사식** > **조사식 1**합니다.

   합니다 **조사식 1** 창이 표시 됩니다.

2. 형식 `$bookAverage` 에 **이름** 필드를 누릅니다 **Enter**합니다.

   값을 `$bookAverage` 에 변수 표시 합니다 **값** 필드.

3. 다음 줄에서 입력 `self::node()` 에 **이름** 필드를 누릅니다 **Enter**합니다.

   `self::node()`는 현재 컨텍스트 노드로 계산되는 XPath 식입니다. `self::node()` XPath 식의 값은 첫 번째 book 노드입니다. 이 값은 변환을 진행하면서 변경됩니다.

4. 확장을 `self::node()` 노드를 다음 노드를 확장 하 고 있는 값이 `price`합니다.

   ![Visual Studio에서 XSLT를 디버깅 하는 동안 조사식 창](media/xslt-debugging-watch-window.png)

   현재 book 노드에 대 한 책 가격 값을 보고 비교 수는 `$bookAverage` 값입니다. 책 가격은 평균 아래 이므로 `xsl:if` 디버깅 프로세스를 계속 하면 조건은 성공 해야 합니다.

## <a name="step-through-the-code"></a>코드를 단계별로 실행

1. **F5**를 눌러 계속합니다.

   만족 하는 첫 번째 book 노드가 때문 합니다 `xsl:if` 조건이 book 노드가 추가 됩니다는 *average.xml 아래* 출력 파일입니다. 디버거는 스타일시트의 `xsl:if` 요소에 다시 배치될 때까지 계속 실행됩니다. 디버거는 이제의 두 번째 book 노드에 배치 합니다 *books.xml* 파일입니다.

   에 **조사식 1** 창은 `self::node()` 값이 두 번째 book 노드로 변경 합니다. 가격 요소 값을 검사하여 가격이 평균을 초과하는 것을 확인할 수 있으므로 `xsl:if` 조건은 실패해야 합니다.

2. **F5**를 눌러 계속합니다.

   두 번째 book 노드가 충족 하지 않으므로 합니다 `xsl:if` 조건에 book 노드가 추가 되지 않습니다 합니다 *average.xml 아래* 출력 파일입니다. 디버거가 계속에 다시 배치 될 때까지 실행을 `xsl:if` 스타일 시트에는 요소입니다. 디버거는 이제 세 번째 배치할 `book` 에서 노드를 *books.xml* 파일입니다.

   에 **조사식 1** 창은 `self::node()` 값이 세 번째 book 노드로 변경 합니다. 값을 검사 하 여는 `price` 요소 평균 가격이 것을 확인할 수 있습니다. `xsl:if` 조건은 성공 해야 합니다.

3. **F5**를 눌러 계속합니다.

   때문에 `xsl:if` 조건을 만족 했기 세 번째 book에 추가 되는 *average.xml 아래* 출력 파일입니다. XML 문서에 있는 모든 book이 처리되었으므로 디버거가 중지됩니다.

## <a name="sample-files"></a>샘플 파일

다음 두 파일은 연습에 사용됩니다.

### <a name="below-averagexsl"></a>below-average.xsl

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

## <a name="see-also"></a>참고자료

- [XSLT 디버그](../xml-tools/debugging-xslt.md)