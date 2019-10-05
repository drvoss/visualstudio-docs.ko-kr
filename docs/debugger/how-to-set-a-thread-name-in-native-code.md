---
title: '방법: 네이티브 코드에 스레드 이름 설정 | Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d37a028fb5af099484d81374e52cfd12af727f94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847540"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>방법: 네이티브 코드에 스레드 이름 설정
스레드 명명 기능은 Visual Studio의 모든 버전에서 사용할 수 있습니다. 스레드 명명 하는 것은 관심 있는 스레드를 식별 하는 데 유용 합니다 **스레드** 실행 중인 프로세스를 디버깅 하는 경우 창입니다. 스레드 recognizably 라는 것도 유용할 수 있습니다 사후 다양 한 도구를 사용 하 여 캡처한 성능 분석 및 크래시 덤프 검사를 통해 디버깅을 수행 하는 경우.

## <a name="ways-to-set-a-thread-name"></a>스레드 이름을 설정 하는 방법

스레드 이름을 설정 하는 방법은 두 가지가 있습니다. 첫 번째 방법은 합니다 [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) 함수입니다. Visual Studio 디버거를 프로세스에 연결 된 경우 특정 예외를 throw 하 여 두 번째는 합니다. 각 방법에는 혜택 및 제한 사항에 있습니다.

주목할 만한 가치가 _둘 다_ 메커니즘 작동 되는 서로 독립적 이므로 원하는 경우 방법을 함께 사용할 수 있습니다.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>사용 하 여 스레드 이름 설정 `SetThreadDescription`

혜택:
* 스레드 이름을 SetThreadDescription 호출 되는 시간에 프로세스에 디버거가 연결 된 여부에 관계 없이 Visual Studio에서 디버깅 하는 경우 표시 됩니다.
* 스레드 이름을 사후 Visual Studio에서 크래시 덤프를 로드 하 여 디버깅을 수행할 때 표시 됩니다.
* 스레드 이름을 같은 다른 도구를 사용 하는 경우에 표시 됩니다는 [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) 디버거 하며 [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) 성능 분석기입니다.

주의 사항:
* 스레드 이름을 Visual Studio 2017 버전 15.6 이상 버전에서 표시 됩니다.
* 사후 크래시를 디버그 덤프 파일, 스레드 이름의 Windows 10 버전 1607 Windows Server 2016 또는 Windows의 이후 버전에서 충돌을 만든 경우에 표시 됩니다.

*예제:*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>예외를 throw 하 여 스레드 이름 설정

프로그램에서 스레드 이름을 설정 하는 또 다른 방법은 특별히 구성 된 예외를 throw 하 여 Visual Studio 디버거에서 원하는 스레드 이름을 전달 하는 합니다.

혜택:
* Visual Studio의 모든 버전에서 작동합니다.

주의 사항:
* 디버거가 예외 기반 메서드를 사용 하는 시간에 연결 하는 경우에 작동 합니다.
* 이 메서드를 사용 하 여 설정 된 스레드 이름은 덤프 또는 성능 분석 도구에서 사용할 수 없습니다.

*예제:*

`SetThreadName` 아래 표시 된 함수에이 예외 기반 접근 방식을 보여 줍니다. 스레드 이름이 스레드에 자동으로 복사 되므로 있도록에 대 한 메모리를 `threadName` 매개 변수는 이후에 릴리스될 수는 `SetThreadName` 호출이 완료 되 합니다.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>참고 항목
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [방법: 관리 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-managed-code.md)
