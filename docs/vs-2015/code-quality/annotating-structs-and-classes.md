---
title: 구조체 및 클래스에 주석 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: df2e75bb3dd01d051d8fed29748e499f8f620128
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157071"
---
# <a name="annotating-structs-and-classes"></a>구조체 및 클래스에 주석 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

고정 처럼 작동 하는 주석을 사용 하 여 구조체와 클래스 멤버에 주석을 달 수 있습니다-함수 진입/종료 바깥쪽 구조를 매개 변수나 결과 값을 포함 하는 또는 함수 호출에서 true가 될 것으로 가정 됩니다.  
  
## <a name="struct-and-class-annotations"></a>구조체 및 클래스 주석  
  
- `_Field_range_(low, high)`  
  
     (포함)에서 범위에 필드가 있는지 `low` 에 `high`입니다.  같음 `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` 적절 한 사전 또는 사후 조건을 사용 하 여 주석이 추가 된 개체에 적용 합니다.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     요소 (바이트)으로 지정 된 쓰기 가능한 크기를 지정 된 필드 `size`합니다.  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     요소 (바이트)으로 지정 된 쓰기 가능한 크기를 지정 된 필드 `size`, 및 `count` 읽을 수 있는 해당 요소 (바이트)입니다.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     요소 (바이트)으로 지정 된 읽기 및 쓰기 가능한 크기 지정 된 필드 `size`합니다.  
  
- `_Struct_size_bytes_(size)`  
  
     요소 (바이트)으로 지정 된 읽기 및 쓰기 가능한 크기 지정 된 필드 `size`합니다.  
  
     구조체 또는 클래스 선언에 적용 됩니다.  가 지정한 바이트 수를 사용 하 여 해당 형식의 유효한 개체를 선언된 된 형식 보다 클 수 있습니다 나타냅니다 `size`합니다.  예:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     버퍼 크기 매개 변수는 바이트 `pM` 형식의 `MyStruct *` 되도록 이동 됩니다.  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [SAL 주석은 C를 줄이기 위해 사용 하 여 /C++ 오류 코드](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 이해](../code-quality/understanding-sal.md)   
 [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)   
 [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)   
 [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)   
 [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [내장 함수](../code-quality/intrinsic-functions.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
