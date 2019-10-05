---
title: 검색 식의 고급 검색 연산자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6befa20bcda7f30896fb2b04fadefb0eb5f21f8d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408401"
---
# <a name="advanced-search-operators-in-search-expressions"></a>검색 식의 고급 검색 연산자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

고급 검색 연산자를 사용 하 여 간단한에서 더 복잡 한 검색 식을 만들어 콘텐츠 검색을 구체화할 수 있습니다. 다음 표와 같이 이러한 연산자는 쿼리가 실행되는 컨텍스트를 제한합니다.  
  
> [!WARNING]
> 검색 엔진이 이러한 연산자를 인식하려면 고급 검색 연산자 뒤에 불필요한 공백 없이 마지막으로 콜론을 입력해야 합니다.  
  
|검색 대상|사용|예제|결과|  
|-------------------|---------|-------------|------------|  
|항목 제목의 용어|title:|title:binaryreader|제목에 “binaryreader”가 포함된 항목입니다.|  
|코드 예제의 용어|code:|code:readdouble|코드 예제에 “readdouble”이 포함된 항목입니다.|  
|특정 프로그래밍 언어 예제의 용어|code:vb:|code:vb:string|Visual Basic 예제에 “string”이 포함된 항목입니다.|  
|특정 인덱스 키워드와 연결된 항목|keyword:|keyword:readbyte|“readbyte” 인덱스 키워드와 연결된 항목입니다.|  
  
 code: 연산자를 사용하여 다양한 프로그래밍 언어에 대한 콘텐츠를 찾을 수 있지만, 이 연산자는 특정 프로그래밍 언어로 표시된 콘텐츠에 대한 결과만 반환합니다. 다음 표에는 이 연산자가 지원하는 프로그래밍 언어가 나와 있습니다.  
  
|프로그래밍 언어|사용|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> 또는<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> 또는<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> 또는<br /><br /> code:c++<br /><br /> 또는<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> 또는<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> 또는<br /><br /> code:js|  
|XAML|code:xaml|  
  
## <a name="see-also"></a>참고 항목  
 [검색 식의 논리 연산자](../ide/logical-operators-in-search-expressions.md)   
 [전체 텍스트 검색 팁](../ide/full-text-search-tips.md)
