---
title: 할당 후크 함수 | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 406647ae086285df8dfdfc00daf4b62be66e74a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402687"
---
# <a name="allocation-hook-functions"></a>할당 후크 함수
할당 후크 함수를 사용 하 여 설치할 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), 메모리 할당을 다시 할당 하거나 해제할 때마다 호출 됩니다. 이러한 후크 형식은 여러 다양 한 용도로 사용할 수 있습니다. 처리 하는 방법을 응용 프로그램 메모리 부족 상황 같은 할당 패턴을 검사할 테스트를 사용 하거나 이후 분석을 위해 할당 정보를 기록 합니다.

> [!NOTE]
> [할당 후크 및 C 런타임 메모리 할당](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)을 참조하여 할당 후크 함수에서 C 런타임 라이브러리 함수를 사용하는 방법에 대한 제한 사항에 대해 잘 알아두세요.

 할당 후크 함수에는 다음과 같이 프로토타입이 있어야 합니다.

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)에 전달한 포인터는 CRTDBG.H에 정의된 대로 **_CRT_ALLOC_HOOK** 형식입니다.

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 런타임 라이브러리가 후크를 호출 하는 경우는 *nAllocType* 인수 나타냅니다 할당 작업 제작 됩니다 (**_HOOK_ALLOC**, **_HOOK_REALLOC**, 또는 **_HOOK_FREE**). 무료 또는 다시 `pvData` 는 해제할 블록의 사용자 문서에 대 한 포인터입니다. 그러나는 할당에 대 한 할당 되지 않은 발생 했기 때문에이 포인터가 null입니다. 나머지 인수는 할당의 크기, 블록 형식 및 파일 이름에 대 한 포인터와 관련 된 다음 요청 번호를 포함 합니다. 사용 가능한 경우 인수 할당이 이루어진 줄 번호를 포함 합니다. 후크 함수는 지정된 모든 분석과 작업을 수행한 다음, 할당 작업을 계속할 수 있음을 나타내는 **TRUE** 또는 작업을 중지해야 함을 나타내는 **FALSE**를 반환해야 합니다. 이 간단한 형식의 후크가 이제까지 할당된 메모리 양을 확인하고, 그 양이 한계를 약간이라도 초과하는 경우에는 **FALSE**를 반환할 수 있습니다. 그러면 사용할 수 있는 메모리가 부족한 경우에만 주로 발생하는 할당 오류가 응용 프로그램에 발생합니다. 좀 더 복잡한 후크는 할당 패턴을 추적하거나 메모리 사용을 분석하거나 특정 상황이 발생하는 때를 보고할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [할당 후크 및 C 런타임 메모리 할당](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [디버그 후크 함수 작성](../debugger/debug-hook-function-writing.md)