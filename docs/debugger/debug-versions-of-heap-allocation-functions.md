---
title: 힙 할당 함수의 디버그 버전 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d00ea299ae7cebea5d6ad1a09837dc75e10568aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852793"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>힙 할당 함수의 디버그 버전
C 런타임 라이브러리에 힙 할당 함수의 특별한 디버그 버전이 있습니다. 이러한 함수는 _dbg가 추가된 릴리스 버전과 이름이 같습니다. 이 항목에서는 `malloc`과 `_malloc_dbg`를 예로 들어 CRT 함수의 릴리스 버전과 _dbg 버전의 차이를 설명합니다.

 때 [_DEBUG](/cpp/c-runtime-library/debug) 가 정의 CRT 모두 매핑합니다 [malloc](/cpp/c-runtime-library/reference/malloc) 호출 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)합니다. 따라서 디버깅하는 동안의 이점을 위해 `_malloc_dbg` 대신 `malloc`를 사용하여 코드를 다시 쓸 필요는 없습니다.

 그러나 `_malloc_dbg`를 명시적으로 호출할 수는 있습니다. `_malloc_dbg`를 명시적으로 호출하면 다음과 같은 이점이 있습니다.

- `_CLIENT_BLOCK` 형식 할당 추적

- 할당이 필요한 소스 파일과 줄 번호 저장

  변환 하지 않을 경우에 `malloc` 에 대 한 호출 `_malloc_dbg`를 정의 하 여 소스 파일 정보를 얻을 수 있습니다 [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), 전처리기에서 직접 지도에 대 한 모든 호출에 이르게 `malloc` 에`_malloc_dbg` 래퍼에 의존 하지 않고 `malloc`합니다.

  클라이언트 블록에서 별도의 할당 형식을 추적하려면 `_malloc_dbg`를 직접 호출하고 `blockType` 매개 변수를 `_CLIENT_BLOCK`에 설정해야 합니다.

  _DEBUG을 정의 하지 않은 경우 호출 `malloc` 방해 받지 않으며, 호출 하는 `_malloc_dbg` 로 확인 됩니다 `malloc`를 정의 [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) 무시 되 고 원본 파일에 대 한 정보는 할당 요청이 제공 되지 않습니다. `malloc`에 블록 형식 매개 변수가 없기 때문에 `_CLIENT_BLOCK` 형식 요청은 표준 할당으로 취급됩니다.

## <a name="see-also"></a>참고 항목

- [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)