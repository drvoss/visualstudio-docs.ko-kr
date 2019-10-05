---
title: CRT 라이브러리를 사용 하 여 메모리 누수를 찾을 | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7fdfedbb2f632bdb0fcaa05c7f0fb282a8fcd2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849975"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>CRT 라이브러리로 메모리 누수 찾기

메모리 누수는 C에서 가장 미묘 하 고 검색 하드 버그 /C++ 앱. 메모리 누수 올바르게 이전에 할당 된 메모리를 할당 해제 하는 데 실패의 결과입니다. 작은 메모리 누수를 처음에 발견 되지 않을 수 있지만 시간이 지남에 따라 앱 메모리 부족 시 충돌 까지의 성능이 떨어지는 증상 발생할 수 있습니다. 누수 앱을 모든 사용 가능한 메모리를 사용 하 여 다른 앱 충돌을 일으킬 수 있는 앱에 대 한 혼동을 만드는 책임이 있습니다. 사소한 메모리 누수를 해결 해야 하는 다른 문제를 나타낼 수 있습니다.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 디버거 및 C 런타임 라이브러리 (CRT) 도움이 될 수 있습니다 검색 하 고 메모리 누수를 식별 합니다.

## <a name="enable-memory-leak-detection"></a>메모리 누수 탐지를 사용 하도록 설정

메모리 누수를 탐지 하는 것에 대 한 기본 도구는 C /C++ 디버거 및 C 런타임 라이브러리 (CRT) 디버그 힙 함수입니다.

모든 디버그 힙 함수를 사용 하도록 설정 하려면에서 다음 문을 포함 하면 C++ 다음 순서로 프로그램:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define` 문은 CRT 힙 함수의 기본 버전을 해당 디버그 버전에 매핑합니다. 생략 하면 합니다 `#define` 문, 메모리 누수 덤프를 됩니다 [덜 자세한](#interpret-the-memory-leak-report)합니다.

포함 하 여 *crtdbg.h* 매핑하는 `malloc` 하 고 `free` 함수가 해당 디버그 버전인 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) 및 [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), 메모리를 추적 하는 할당 및 할당 취소 합니다. 이 매핑은 `_DEBUG`가 있는 디버그 빌드에서만 발생합니다. 릴리스 빌드에서는 일반적인 `malloc` 함수와 `free` 함수가 사용됩니다.

위의 문을 사용 하 여 디버그 힙 함수를 설정한 후 배치에 대 한 호출 [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) 앱이 종료 될 때 메모리 누수 보고서를 표시 하는 앱 종료 지점 앞입니다.

```cpp
_CrtDumpMemoryLeaks();
```

앱의 여러 종료 하는 경우 수동으로 추가할 필요가 없습니다 `_CrtDumpMemoryLeaks` 종료 지점 마다. 가 자동으로 호출 시킬 `_CrtDumpMemoryLeaks` 각 종료 지점에 대 한 호출을 배치 `_CrtSetDbgFlag` 여기에 표시 된 비트 필드를 사용 하 여 앱의 시작 부분:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

기본적으로 `_CrtDumpMemoryLeaks` 는 **출력** 창의 **디버그** 창에 메모리 누수 보고서를 출력합니다. 라이브러리를 사용할 경우에는 라이브러리에 의해 출력이 다른 위치로 다시 설정될 수도 있습니다.

사용할 수 있습니다 `_CrtSetReportMode` 보고서의 다른 위치로 리디렉션하거나 다시 하는 **출력** 다음과 같이 창:

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>메모리 누수 보고서 해석

앱이 정의 되지 않은 경우 `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) 같은 메모리 누수 보고서가 표시 됩니다.

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

앱에서 정의 하는 경우 `_CRTDBG_MAP_ALLOC`, 메모리 누수 보고서에는 다음과 같습니다.

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

두 번째 보고서 누출된 된 메모리가 처음 할당 된 파일 이름과 줄 번호를 보여 줍니다.

정의 하는 여부 `_CRTDBG_MAP_ALLOC`, 메모리 누수 보고서에 표시 됩니다.

- 메모리 할당 번호 `18` 예제
- 블록 형식이 `normal` 예제에서입니다.
- 16 진수 메모리 위치 `0x00780E80` 예제에서입니다.
- 블록의 크기 `64 bytes` 예제에서입니다.
- 블록 내 데이터의 처음 16바이트(16진수 형식)

메모리 블록 형식 *정상적인*, *클라이언트*, 또는 *CRT*합니다. *표준 블록* 은 프로그램이 할당한 보통 메모리입니다. *클라이언트 블록* 은 MFC 프로그램이 소멸자를 필요로 하는 개체에 대해 사용하는 특별한 메모리 블록 형식입니다. MFC `new` 연산자는 표준 블록 또는 클라이언트 블록 중 생성되는 개체에 적합한 블록을 만듭니다.

*CRT 블록* 은 CRT 라이브러리가 자체 용도에 맞게 할당한 메모리 블록입니다. CRT 라이브러리 CRT 블록은 CRT 라이브러리를 사용 하 여 심각한 문제가 없는 경우 메모리 누수 보고서에 표시 되지 않습니다 있도록 이러한 블록을 할당 취소를 처리 합니다.

그 외에도 메모리 누수 보고서에 표시되지 않는 두 가지 메모리 블록 형식이 있습니다. A *빈 블록* 메모리가 해제 하므로 정의 의해 유출 되지 않습니다. *무시 블록* 메모리가 메모리 누수 보고서에서 제외 하도록 명시적으로 표시 했습니다.

앞의 예제 코드는 표준 CRT를 사용 하 여 할당 된 메모리에 대 한 메모리 누수 식별 `malloc` 함수입니다. 하지만 프로그램이 사용 하 여 메모리를 할당 하는 경우는 C++ `new` 연산자, 표시 될 수 있습니다만 파일 이름과 줄 번호 위치 `operator new` 호출 `_malloc_dbg` 메모리 누수 보고서에. 유용한 메모리 누수 보고서를 만들려면 할당을 수행한 줄을 보고 하려면 다음과 같은 매크로 작성할 수 있습니다.

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

바꾸면 이제 합니다 `new` 연산자를 사용 하 여는 `DBG_NEW` 코드에서 매크로입니다. 디버그 빌드에서 `DBG_NEW` 전역 오버 로드를 사용 하 여 `operator new` 블록 형식, 파일 및 줄 번호에 대 한 추가 매개 변수를 사용 하는 합니다. 오버 로드 `new` 호출 `_malloc_dbg` 추가 정보를 기록 합니다. 메모리 누수 보고서는 누수 된 개체가 할당 된 위치는 파일 이름과 줄 번호를 보여 줍니다. 릴리스 빌드 여전히 사용 하 여 기본 `new`입니다. 기술의 예는 다음과 같습니다.

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

Visual Studio에서이 코드를 실행할 때 디버거, 호출 `_CrtDumpMemoryLeaks` 에서 보고서를 생성 합니다 **출력** 유사한 창:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

이 출력 보고서의 20 번 줄에서 유출된 할당 되었음을 *debug_new.cpp*합니다.

>[!NOTE]
>명명 된 전처리기 매크로 만들면 하는 것이 좋습니다 `new`, 또는 다른 언어 키워드입니다.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>메모리 할당 번호에 중단점을 설정 합니다.

메모리 할당 번호는 누수된 메모리 블록이 할당된 시기를 알려 줍니다. 메모리 할당 번호가 18 인 블록에는 예를 들어, 18 번째로 앱을 실행 하는 동안 할당 된 메모리 블록이입니다. CRT 보고서 실행, CRT 라이브러리와 MFC 등의 다른 라이브러리에서 할당을 포함 하는 동안 모든 메모리 블록 할당을 계산 합니다. 따라서 메모리 할당 블록 번호 18에는 코드에 의해 할당 된 메모리 블록은 18 아마도 하지 않습니다.

할당 번호를 사용하여 메모리 할당에 중단점을 설정할 수 있습니다.

**조사식 창을 사용하여 메모리 할당 중단점을 설정하려면**

1. 앱의 시작 부분에 중단점을 설정 하 고 디버깅을 시작 합니다.

1. 앱의 중단점에서 일시 중지 하는 경우 열을 **조사식** 를 선택 하 여 창 **디버그** > **Windows** > **조사식1** (또는 **조사식 2**하십시오 **조사식 3**, 또는 **조사식 4**).

1. 에 **조사식** 창, 형식 `_crtBreakAlloc` 에 **이름** 열입니다.

   다중 스레드 DLL 버전의 CRT 라이브러리 (/MD 옵션)를 사용 하는 경우 컨텍스트 연산자를 추가 합니다. `{,,ucrtbased.dll}_crtBreakAlloc`

1. **Enter** 키를 누릅니다.

   디버거에서 호출이 실행되고 결과가 **값** 열에 표시됩니다. 메모리를 할당할 때 중단점을 설정하지 않은 경우에는 이 값이 **-1**입니다.

1. 에 **값** 열 값을 중단 하도록 디버거를 만들려는 메모리 할당의 할당 번호로 바꿉니다.

메모리 할당 번호에 중단점을 설정한 후 디버그를 계속 합니다. 메모리 할당 번호를 변경 하지 않도록 동일한 조건에서 실행 해야 합니다. 지정된 된 메모리 할당에서 프로그램이 중단을 사용 하 여는 **호출 스택** 창과 다른 디버거 메모리가 할당 된 조건을 확인 합니다. 그런 다음 개체에 어떻게 되는지 관찰 하는 실행을 계속할 수 있으며 되지 올바르게 할당 취소 이유를 확인할 수 있습니다.

개체에 데이터 중단점을 설정하는 것도 유용합니다. 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md)을 참조하세요.

코드에서 메모리 할당 중단점을 설정할 수도 있습니다. 다음과 같이 설정할 수 있습니다.

```cpp
_crtBreakAlloc = 18;
```

 또는

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>메모리 상태 비교
 주요 지점에서 애플리케이션의 메모리 상태 스냅샷을 보고 메모리 누수를 찾을 수도 있습니다. 응용 프로그램에서 특정 지점의 메모리 상태 스냅숏을 만들려면를 `_CrtMemState` 구조체를 전달 하는 `_CrtMemCheckpoint` 함수입니다.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

`_CrtMemCheckpoint` 함수 구조체를 현재 메모리 상태의 스냅숏으로 채웁니다.

내용을 출력 하는 `_CrtMemState` 구조체 구조체를 전달 하는 `_ CrtMemDumpStatistics` 함수:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` 같은 메모리 상태 덤프를 출력 합니다.

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

코드의 한 섹션에서 메모리 누수가 발생했는지 확인하려면 해당 섹션 앞뒤에서 메모리 상태 스냅샷을 만든 다음 `_ CrtMemDifference` 를 사용하여 두 상태를 비교합니다.

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` 메모리 상태 비교 `s1` 하 고 `s2` 에서 결과 반환 합니다 (`s3`) 간의 차이 나타내는 `s1` 및 `s2`합니다.

배치 하 여 시작 메모리 누수를 찾는 한 가지 기술은 `_CrtMemCheckpoint` 사용 하 여 앱의 시작과 끝에서 호출 `_CrtMemDifference` 결과 비교 하 합니다. 하는 경우 `_CrtMemDifference` 더 추가할 수 있습니다 메모리 누수를 보여 줍니다. `_CrtMemCheckpoint` 누수 원인을 격리 될 때까지 이진 검색을 사용 하 여 프로그램을 나누는 데 호출 합니다.

## <a name="false-positives"></a>가양성(false positive)
 `_CrtDumpMemoryLeaks` 라이브러리 CRT 블록 또는 클라이언트 블록 대신 일반 블록으로 내부 할당을 표시 하는 경우 메모리 누수를 잘못 표시를 제공할 수 있습니다. 이 경우 `_CrtDumpMemoryLeaks` 가 사용자 할당과 내부 라이브러리 할당을 구별할 수 없게 됩니다. `_CrtDumpMemoryLeaks`를 호출한 이후에 라이브러리 할당을 위한 전역 소멸자가 실행되면 모든 내부 라이브러리 할당이 메모리 누수로 보고됩니다. 다양 한 표준 템플릿 라이브러리를 Visual Studio.NET 않을 이전의 `_CrtDumpMemoryLeaks` 이러한 가양성을 보고 합니다.

## <a name="see-also"></a>참고자료
- [CRT 디버그 힙 정보](../debugger/crt-debug-heap-details.md)
- [디버거 보안](../debugger/debugger-security.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
