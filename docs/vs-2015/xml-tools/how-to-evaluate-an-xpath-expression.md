---
title: '방법: XPath 식 계산 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03c43d272d3c740c55314db5d1b7b6c225b7e5c8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421771"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>방법: XPath 식 계산
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 하 여 XPath 식을 계산할 수 있습니다 합니다 **간략 한 조사식** 대화 상자. XPath 식은 W3C XPath 1.0 권장 사항에 따라 유효한 식이어야 합니다. 현재 XSLT 컨텍스트-즉, 합니다 `self::node()` 에서 노드를 **지역** 창-XPath 식에 대 한 계산 컨텍스트를 제공 합니다.  
  
 다음 목록에서는 XPath 식을 계산할 때 지원되는 함수를 설명합니다.  
  
- 기본 제공 XPath 함수가 지원됩니다.  
  
- 기본 제공 XSLT 함수는 지원되지 않습니다.  
  
- 사용자 정의 함수는 지원되지 않습니다.  
  
> [!NOTE]
> 다음 절차에서 belowAvg.xsl 및 books.xml 파일을 사용 하 여 [연습: XSLT 스타일 시트 디버깅](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) 항목입니다.  
  
### <a name="to-evaluate-an-xpath-expression"></a>XPath 식을 계산하려면  
  
1. `xsl:if` 시작 태그에 중단점을 삽입합니다.  
  
2. 클릭 합니다 **XSL 디버깅** XML 편집기 도구 모음 단추입니다.  
  
     디버거가 시작되고 `xsl:if` 태그에서 중단됩니다.  
  
3. 마우스 오른쪽 단추로 클릭 **간략 한 조사식**합니다.  
  
     합니다 **간략 한 조사식** 대화 상자가 표시 됩니다.  
  
4. 입력 `./price/text()` 에 **식** 필드를 **간략 한 조사식** 대화 상자를 클릭 **재평가**.  
  
     현재 book 노드의 가격이 나타나는 합니다 **값** 상자입니다.  
  
5. XPath 식을 변경 `./price/text() < $bookAverage` 을 클릭 **재평가**합니다.  
  
     합니다 **값** 상자에 표시 하는 XPath 식이 `true`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [XSLT 디버그](../xml-tools/debugging-xslt.md)
