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
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 1cff36760a84821a33dcdb1ee4cc6842cd40aee0
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72015973"
---
# <a name="annotating-structs-and-classes"></a>구조체 및 클래스에 주석 지정

고정 처럼 동작 하는 주석을 사용 하 여 구조체 및 클래스 멤버에 주석을 추가할 수 있습니다 .이는 바깥쪽 구조체를 매개 변수 또는 결과 값으로 포함 하는 함수 호출 또는 함수 시작/종료에서 true로 간주 됩니다.

## <a name="struct-and-class-annotations"></a>구조체 및 클래스 주석

- `_Field_range_(low, high)`

     필드의 범위 (포함)는 `low`에서 `high` 까지입니다.  적절 한 사전 또는 사후 조건을 사용 하 여 주석이 달린 개체에 적용 되는 @no__t와 동일 합니다.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     @No__t-0으로 지정 된 요소 (또는 바이트)에 쓰기 가능한 크기가 있는 필드입니다.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     @No__t-0으로 지정 된 요소 (또는 바이트)에 쓰기 가능한 크기가 있는 필드 및 읽을 수 있는 해당 요소 (바이트)의 @no__t입니다.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     @No__t-0으로 지정 된 요소 (또는 바이트)에서 읽고 쓸 수 있는 크기를 모두 포함 하는 필드입니다.

- `_Field_z_`

     Null로 끝나는 문자열을 포함 하는 필드입니다.

- `_Struct_size_bytes_(size)`

     구조체 또는 클래스 선언에 적용 됩니다.  @No__t-0으로 지정 된 바이트 수를 사용 하 여 해당 형식의 유효한 개체가 선언 된 형식 보다 클 수 있음을 나타냅니다.  예를 들어 다음과 같은 가치를 제공해야 합니다.

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     매개 변수의 버퍼 크기 (바이트)는 `MyStruct *` 형식의 `pM`입니다.

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

이 예에 대 한 참고 사항:

- `_Field_z_`는 `_Null_terminated_`와 같습니다.  이름 필드에 `_Field_z_`은 이름 필드가 null로 끝나는 문자열 임을 지정 합니다.
- @no__t에 대 한 `bufferSize`은 `bufferSize`의 값이 1에서 `MaxBufferSize` (둘 다 포함) 임을 지정 합니다.
- @No__t-0 및 `_Field_size_` 주석의 최종 결과는 동일 합니다. 레이아웃이 비슷한 구조 나 클래스의 경우 `_Field_size_`은 해당 하는 `_Struct_size_bytes_` 주석 보다 더 많은 참조와 계산을 포함 하기 때문에 더 쉽게 읽고 유지 관리할 수 있습니다. `_Field_size_`은 바이트 크기로 변환할 필요가 없습니다. 예를 들어 void 포인터 필드의 경우에는 바이트 크기만 옵션을 사용할 수 있습니다. 예를 들어 `_Field_size_bytes_`을 사용할 수 있습니다. @No__t-0과 `_Field_size_`이 모두 있는 경우 도구에서 둘 다 사용할 수 있습니다. 두 주석이 동의 하지 않는 경우에는이 도구를 통해 수행할 작업을 결정 해야 합니다.

## <a name="see-also"></a>관련 항목

- [C/C++ 코드 오류를 줄이기 위한 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL 이해](../code-quality/understanding-sal.md)
- [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)
- [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)
- [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)
- [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [내장 함수](../code-quality/intrinsic-functions.md)
- [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)