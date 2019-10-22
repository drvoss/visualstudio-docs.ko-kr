---
title: '방법: XPath 식 계산 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670871"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>방법: XPath 식 계산
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**간략 한 조사식** 대화 상자를 사용 하 여 XPath 식을 평가할 수 있습니다. XPath 식은 W3C XPath 1.0 권장 사항에 따라 유효한 식이어야 합니다. 현재 XSLT 컨텍스트, 즉 **지역** 창의 `self::node()` 노드인는 XPath 식에 대 한 평가 컨텍스트를 제공 합니다.

 다음 목록에서는 XPath 식을 계산할 때 지원되는 함수를 설명합니다.

- 기본 제공 XPath 함수가 지원됩니다.

- 기본 제공 XSLT 함수는 지원되지 않습니다.

- 사용자 정의 함수는 지원되지 않습니다.

> [!NOTE]
> 다음 절차에서는 [연습: XSLT 스타일 시트 디버그](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) 항목의 belowavg.xsl 및 books.xml 파일을 사용 합니다.

### <a name="to-evaluate-an-xpath-expression"></a>XPath 식을 계산하려면

1. `xsl:if` 시작 태그에 중단점을 삽입합니다.

2. XML 편집기 도구 모음에서 **XSL 디버깅** 단추를 클릭 합니다.

     디버거가 시작되고 `xsl:if` 태그에서 중단됩니다.

3. 마우스 오른쪽 단추를 클릭 하 고 **간략 한 조사식**을 선택 합니다.

     **간략 한 조사식** 대화 상자가 표시 됩니다.

4. **간략 한 조사식** 대화 상자의 **식** 필드에 `./price/text()`를 입력 하 고 다시 **계산**을 클릭 합니다.

     현재 책 노드의 가격은 **값** 상자에 나타납니다.

5. XPath 식을 `./price/text() < $bookAverage` 변경 하 고 다시 **계산**을 클릭 합니다.

     **값** 상자는 XPath 식이 `true`로 평가 됨을 보여 줍니다.

## <a name="see-also"></a>관련 항목:
 [XSLT 디버그](../xml-tools/debugging-xslt.md)
