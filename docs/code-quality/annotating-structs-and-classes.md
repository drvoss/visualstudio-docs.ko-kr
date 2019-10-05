---
title: 구조체 및 클래스에 주석 지정
ms.date: 06/28/2019
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
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 35be465064c9524eb0e1339794b6a19b7a595da1
ms.sourcegitcommit: d2b234e0a4a875c3cba09321cdf246842670d872
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493630"
---
# <a name="annotating-structs-and-classes"></a>구조체 및 클래스에 주석 지정

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

- `_Field_z_`

     필드에는 null로 끝나는 문자열입니다.

- `_Struct_size_bytes_(size)`

     구조체 또는 클래스 선언에 적용 됩니다.  가 지정한 바이트 수를 사용 하 여 해당 형식의 유효한 개체를 선언된 된 형식 보다 클 수 있습니다 나타냅니다 `size`합니다.  예를 들어:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     버퍼 크기 매개 변수는 바이트 `pM` 형식의 `MyStruct *` 되도록 이동 됩니다.

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>예제

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[0];
};
```

이 예제에 대 한 참고 사항:

- `_Field_z_`는 `_Null_terminated_`와 같습니다.  `_Field_z_` 이름에 대 한 필드 이름 필드는 null로 끝나는 문자열 임을 지정 합니다.
- `_Field_range_` 에 대 한 `bufferSize` 지정 변수의 `bufferSize` 1 내에 있어야 하 고 `MaxBufferSize` (모두 포함).
- 최종 결과 `_Struct_size_bytes_` 고 `_Field_size_` 주석은 해당 합니다. 와 비슷한 레이아웃이 있는 클래스나 구조체에 대 한 `_Field_size_` 참조 및 계산에 해당 하는 보다 적은 수 있기 때문에 보다 쉽게 읽고 유지 관리는 `_Struct_size_bytes_` 주석입니다. `_Field_size_` 변환할 바이트 크기를 필요 하지 않습니다. 바이트 크기가 옵션을 예를 들어, void 포인터 필드에 대해 `_Field_size_bytes_` 사용할 수 있습니다. 둘 다 `_Struct_size_bytes_` 고 `_Field_size_` 존재, 모두 도구에 제공 됩니다. 것은 도구 두 주석은 동의 하는 경우 수행할 작업입니다.

## <a name="see-also"></a>참고 항목

- [C/C++ 코드 오류를 줄이기 위한 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL 이해](../code-quality/understanding-sal.md)
- [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)
- [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)
- [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)
- [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [내장 함수](../code-quality/intrinsic-functions.md)
- [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)