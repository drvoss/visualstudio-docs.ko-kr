---
title: '방법: 생성 된 코드에 대 한 코드 분석 경고 표시 안 함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9949a72abc46f2212fe448e193a06cce90b6df7c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438983"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>방법: 생성된 코드에 대한 코드 분석 경고 표시 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관리 되는 코드 컴파일러는 종종 코드를 빠르게 개발할 수 있도록 프로젝트에 추가 되는 코드를 생성 합니다. 또한 개발자는 종종 응용 프로그램을 신속 하 게 개발 하는 데 타사 도구를 사용 합니다. 이러한 도구는 또한 프로젝트에 추가 되는 코드를 생성 합니다.  
  
 생성 된 코드에서 코드 분석을 검색 하는 규칙 위반을 확인 하려는 합니다. 그러나 볼 수 없으며 위반을 포함 하는 코드를 유지 관리 하는 경우이 참조 하지 않을 수 있습니다.  
  
 합니다 **생성 된 코드 결과 표시 안 함** 프로젝트의 코드 분석 속성 페이지에서 확인란을 사용 하면 타사 도구에서 생성 된 코드에서 코드 분석 경고를 표시 하려는 지 여부를 선택할 수 있습니다.  
  
> [!NOTE]
> 이 옵션 폼 및 템플릿에 오류 및 경고를 표시 하는 경우 생성 된 코드에서 코드 분석 오류 및 경고를 억제 하지 않습니다. 폼이나 템플릿의 소스 코드를 볼 수도 있고 유지 관리할 수도 있습니다.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>프로젝트에서 생성 된 코드에 대 한 경고를 표시 하지 않으려면  
  
1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 누른 **속성**합니다.  
  
2. 클릭 **코드 분석**합니다.  
  
3. 선택 된 **생성 된 코드 결과 표시 안 함** 확인란 합니다.
