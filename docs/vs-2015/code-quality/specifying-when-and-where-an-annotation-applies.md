---
title: 주석 적용 시기 및 위치 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ba14fdbc23968fcaf10355f73517ab6cd54f8797
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142181"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>주석 적용 시기 및 위치 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

주석의 조건부 경우 분석기를 지정 하려면 다른 주석이 필요할 수 있습니다.  예를 들어, 함수에 동기식 또는 비동기식 일 수 있는 변수, 함수를 다음과 같이 동작 합니다. 동기 경우에서이 항상 결국 성공 하지만, 비동기 작업의 경우에 오류를 보고 즉시 성공 수 없습니다. 함수를 동기적으로 호출 되 면 반환 있을 것 때문에 코드 분석기 값을 제공 결과 값을 확인 합니다.  그러나 함수를 비동기적으로 호출 하 고 함수 결과 확인 하지 않습니다, 심각한 오류가 발생할 수 있습니다. 이 예제에서는 사용할 수 있는 상황을 보여 줍니다.는 `_When_` 주석-이 문서의 뒷부분에서 설명-검사할 수 있도록 합니다.  
  
## <a name="structural-annotations"></a>구조적 주석  
 주석 적용 시기 및 위치를 제어 하려면 다음과 같은 구조적 주석을 사용 합니다.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` lvalue를 생성 하는 식이입니다. 에 대 한 주석 `anno-list` 로 명명 된 개체에 적용 됩니다 `expr`합니다. 각 주석에 `anno-list`, `expr` 사전 조건에서 주석이 해석 되 고 사후 조건에서 사후 조건 경우에는 주석이 해석 되는 경우 사전 조건으로 해석 됩니다.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` lvalue를 생성 하는 식이입니다. 에 대 한 주석 `anno-list` 로 명명 된 개체에 적용 됩니다 `expr`합니다. 각 주석에 `anno-list`, `expr` 전제 조건에서 주석이 해석 되 고 사후 조건에서 사후 조건 경우에는 주석이 해석 되는 경우 사전 조건으로 해석 됩니다.<br /><br /> `iter` 주석에 범위가 지정 된 변수의 이름입니다 (포함 `anno-list`). `iter` 암시적 형식이 `long`합니다. 바깥쪽 범위에서 동일 하 게 명명 된 변수는 평가에서 숨겨집니다.<br /><br /> `elem-count` 정수로 확인 되는 식이입니다.|  
|`_Group_(anno-list)`|에 대 한 주석 `anno-list` 모든 각 주석이 적용 되는 그룹 주석이 적용 되는 모든 한정자가으로 간주 됩니다.|  
|`_When_(expr, anno-list)`|`expr` 변환할 수 있는 식 `bool`합니다. 0이 아닌 경우 (`true`)를 지정 된 주석을 `anno-list` 적용 가능한 것으로 간주 됩니다.<br /><br /> 기본적으로의 각 주석이 `anno-list`, `expr` 주석이 전제 조건으로 이며 경우 출력 값을 사용 하 여 주석을 사후 조건 하는 경우 입력된 값을 사용 하 여 해석 됩니다. 기본값을 재정의 하려면 사용할 수 있습니다는 `_Old_` 입력된 값을 사용 해야 함을 나타내려면 사후 조건을 평가할 때 내장 함수입니다. **참고:**  다른 주석 사용의 결과로 사용할 수 있습니다 `_When_` 변경할 수 있는 값-예를 들어 `*pLength`-때문에 관련 된 계산된 된 결과 `expr` 사전 조건에서 계산된 결과를 사후 조건에서에서 달라질 수 있습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [SAL 주석은 C를 줄이기 위해 사용 하 여 /C++ 오류 코드](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 이해](../code-quality/understanding-sal.md)   
 [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)   
 [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)   
 [구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)   
 [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)   
 [내장 함수](../code-quality/intrinsic-functions.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
