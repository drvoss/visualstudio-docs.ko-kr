---
title: 할당 후크 및 C 런타임 메모리 할당 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1840f6f5650b3491cf7898c1d8d6a6fcae19f906
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564976"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>할당 후크 및 C 런타임 메모리 할당
할당 후크 함수에 대 한 매우 중요 한 제한 명시적으로 무시 해야 한다는 점은 `_CRT_BLOCK` 블록입니다. 이러한 블록은 내부 메모리를 할당 하는 C 런타임 라이브러리 함수를 호출 하는 경우 C 런타임 라이브러리 함수에 의해 내부적으로 만든 메모리 할당입니다. 무시 해도 `_CRT_BLOCK` 할당 된 시작 부분에 다음 코드를 포함 하 여 블록 후크 함수:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

할당 후크 무시 하지 않습니다 `_CRT_BLOCK` 블록을 후크에서 호출한 모든 C 런타임 라이브러리 함수는 무한 루프에서 프로그램을 트래핑할 수 있습니다. 예를 들어, `printf`는 내부 할당을 만듭니다. 후크 코드가 `printf`를 호출하면 결과 할당으로 인해 후크가 다시 호출되어 **printf**를 다시 호출하고 스택에 오버플로가 발생할 때까지 이 과정이 계속됩니다. `_CRT_BLOCK` 할당 작업을 보고해야 할 경우, 이러한 제한을 피하려면 형식 지정과 출력에 C 런타임 함수 대신 Windows API 함수를 사용해야 합니다. Windows Api C 런타임 라이브러리 힙을 사용 하지 않는 않기 무한 루프에서 할당 후크를 트래핑 하지 않습니다.

런타임 라이브러리 소스 파일을 검사하면 기본 할당 후크 함수 **CrtDefaultAllocHook**(**TRUE**만 반환)가 자체 별도 파일인 DBGHOOK.C에 있음을 알 수 있습니다. 애플리케이션의 **main** 함수보다 먼저 실행되는 런타임 시작 코드가 만든 할당에 대해서도 할당 후크를 호출하려면 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)를 사용하지 말고 사용자의 함수로 이 기본 함수를 대체합니다.

## <a name="see-also"></a>참고 항목
- [디버그 후크 함수 작성](../debugger/debug-hook-function-writing.md)
