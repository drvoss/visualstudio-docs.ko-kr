---
title: 디버깅 하는 동안 XPath 식 계산
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002078"
---
# <a name="evaluate-xpath-expressions"></a>XPath 식 계산

사용 하 여 XPath 식을 계산할 수 있습니다 합니다 **간략 한 조사식** 디버깅 하는 동안 창입니다. XPath 식은 W3C XPath 1.0 권장 사항에 따라 유효한 식이어야 합니다. 현재 XSLT 컨텍스트 (즉, 합니다 `self::node()` 에서 노드를 **지역** 창) XPath 식에 대 한 계산 컨텍스트를 제공 합니다.

XPath 식을 평가할 때:

- 기본 제공 XPath 함수가 지원됩니다.

- 기본 제공 XSLT 함수 및 사용자 정의 함수는 지원 되지 않습니다.

> [!NOTE]
> 만 XSLT 디버깅 Visual Studio의 Enterprise edition에서 제공 됩니다.

## <a name="evaluate-an-xpath-expression"></a>XPath 식 계산

다음 절차에서는 합니다 *average.xsl 아래* 하 고 *books.xml* 에서 파일을 [연습: XSLT 스타일 시트 디버깅](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) 페이지입니다.

1. `xsl:if` 시작 태그에 중단점을 삽입합니다.

2. 디버깅을 시작 하려면 선택 **XML** > **XSLT 디버깅 시작** 메뉴 모음에서 (또는 키를 누릅니다 **Alt**+**F5** ).

   디버거가 시작되고 `xsl:if` 태그에서 중단됩니다.

3. 마우스 오른쪽 단추로 클릭 **간략 한 조사식**합니다.

   합니다 **간략 한 조사식** 창이 열립니다.

4. 입력 `./price/text()` 에 **식** 필드를 **간략 한 조사식** 대화 상자를 선택한 후 **평가**합니다.

   현재 book 노드의 가격이 나타나는 합니다 **값** 상자입니다.

   ![간략 한 조사식 창에서 XPath 식 계산](media/quickwatch-price.png)

5. XPath 식을 변경 `./price/text() < $bookAverage` 을 클릭 **재평가**합니다.

   합니다 **값** 상자에 표시 하는 XPath 식이 `true`합니다.

## <a name="see-also"></a>참고자료

- [XSLT 디버그](../xml-tools/debugging-xslt.md)