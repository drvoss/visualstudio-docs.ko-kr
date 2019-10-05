---
title: 내장 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e5284ae41f961d8e027590b4296037236e7108f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699432"
---
# <a name="intrinsic-functions"></a>내장 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SAL의 식을 C 수 /C++ 의도 하지 않은 식에는 식 제공-예를 들어, + +,--, 및이 컨텍스트에서 의도 하지 않은 모든 함수 호출 합니다.  그러나 SAL는 일부 함수와 비슷한 개체 및 SAL 식에서 사용할 수 있는 일부 예약 된 기호를 제공 합니다. 이러한 이라고 *내장 함수*합니다.  
  
## <a name="general-purpose"></a>일반 용도  
 다음 내장 함수 주석에 sal 일반 유틸리티를 제공합니다.  
  
|주석|설명|  
|----------------|-----------------|  
|`_Curr_`|현재 주석이 추가 되는 개체에 대 한 동의어입니다.  경우는 `_At_` 주석 사용 중인 `_Curr_` 첫 번째 매개 변수로 동일 `_At_`합니다.  그러지 매개 변수 또는 주석이 어휘 적으로 연결 되는 전체 함수/반환 값은입니다.|  
|`_Inexpressible_(expr)`|버퍼의 크기는 너무 복잡해 서 주석 식을 사용 하 여 표시할 수 있는 상황을 표현 합니다.-예를 들어, 멤버를 선택한 경우 입력된 데이터 집합을 검색 하 고 다음 계산 하 여 계산 됩니다.|  
|`_Nullterm_length_(param)`|`param` null 종결자를 포함 하지 않습니다 하지만 최대 버퍼의 요소 수가입니다. 비 집계, void가 아닌 형식의 모든 버퍼를 적용할 수 있습니다.|  
|`_Old_(expr)`|전제 조건에서 계산 될 때 `_Old_` 입력된 값을 반환 합니다 `expr`합니다.  값을 반환 한다는 사후 조건에서 계산할 때 `expr` 사전 조건에서 계산한 되는 것입니다.|  
|`_Param_(n)`|합니다 `n`번째 매개 변수가 1부터 계산 함수에 대 `n`, 및 `n` 리터럴 정수 계열 상수입니다. 매개 변수 이름이 인 경우이 주석은 매개 변수 이름으로 액세스할 수 있도록 동일 합니다. **참고:** `n` 줄임표에 의해 정의 됩니다 또는 이름이 사용 되지 않습니다 함수 프로토타입의 사용할 수 있습니다 하는 위치 매개 변수를 참조할 수 있습니다.|  
|`return`|C /C++ 예약된 키워드 `return` 함수의 반환 값을 나타내는 SAL 식에 사용할 수 있습니다.  값은 post 상태에만 사용할 수 이 사전 상태에서 사용 하려면 구문 오류입니다.|  
  
## <a name="string-specific"></a>특정 문자열  
 다음 내장 함수를 주석에 문자열을 조작할을 수 있습니다. 동일한 목적을 수행 하는 이러한 함수의 모든 4: null 종료 되기 전에 발견 되는 형식의 요소 수를 반환 합니다. 차이점은 참조 하는 요소에는 데이터의 종류입니다. 사용 하 여, null로 끝나는 길이 지정 하려는 경우에 버퍼는 문자로 구성 되어 있지는 `_Nullterm_length_(param)` 이전 섹션의 주석입니다.  
  
|주석|설명|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` null 종결자를 포함 하지 않습니다 하지만 최대 문자열의 요소 수가입니다. 이 주석의 문자열의 문자 형식에 대 한 예약 되어 있습니다.|  
|`strlen(param)`|`param` null 종결자를 포함 하지 않습니다 하지만 최대 문자열의 요소 수가입니다. 이 주석 문자에 사용 하 여 배열 및 C 런타임 함수가 유사에 대해 예약 [strlen()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)합니다.|  
|`wcslen(param)`|`param` 최대 (포함 되지 않음) 문자열의 요소 수는 null 종결자입니다. 이 주석은 와이드 문자에 사용 하 여 배열 및 유사한 C 런타임 함수에 대해 예약 [wcslen()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [SAL 주석은 C를 줄이기 위해 사용 하 여 /C++ 오류 코드](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 이해](../code-quality/understanding-sal.md)   
 [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)   
 [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)   
 [구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)   
 [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)   
 [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
