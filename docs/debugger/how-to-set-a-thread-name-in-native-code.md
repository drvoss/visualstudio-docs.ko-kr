---
title: '방법: 네이티브 코드에서 스레드 이름 설정 | Microsoft Docs'
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
ms.openlocfilehash: a89dce28f33bef0ffdb13d6254b2ac6b86ac25db
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589030"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>방법: 네이티브 코드에 스레드 이름 설정
스레드 명명 기능은 Visual Studio의 모든 버전에서 사용할 수 있습니다. 스레드 이름 지정은 실행 중인 프로세스를 디버그할 때 **스레드** 창에서 관심 있는 스레드를 식별 하는 데 유용 합니다. Recognizably로 명명 된 스레드는 충돌 덤프 검사를 통해 사후 사후 디버깅을 수행 하 고 다양 한 도구를 사용 하 여 성능 캡처를 분석할 때 유용할 수 있습니다.

## <a name="ways-to-set-a-thread-name"></a>스레드 이름을 설정 하는 방법

스레드 이름을 설정 하는 방법에는 두 가지가 있습니다. 첫 번째는 [Setthreaddescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) 함수를 통해입니다. 두 번째는 Visual Studio 디버거가 프로세스에 연결 되어 있는 동안 특정 예외를 throw 하는 것입니다. 각 접근 방식에는 이점 및 주의 사항이 있습니다. @No__t_0 사용은 Windows 10, 버전 1607 또는 Windows Server 2016부터 지원 됩니다.

원하는 경우 _두_ 방법을 함께 사용할 수 있습니다. 이러한 방식은 서로 독립적 이기 때문입니다.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>@No__t_0를 사용 하 여 스레드 이름 설정

혜택:
* 디버거는 SetThreadDescription이 호출 될 때 프로세스가 프로세스에 연결 되었는지 여부에 관계 없이 Visual Studio에서 디버그할 때 표시 됩니다.
* Visual Studio에서 크래시 덤프를 로드 하 여 사후 사후 디버깅을 수행할 때 스레드 이름이 표시 됩니다.
* [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) 디버거와 [Windows performance analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) performance analyzer와 같은 다른 도구를 사용 하는 경우에도 스레드 이름이 표시 됩니다.

주의 사항:
* 스레드 이름은 Visual Studio 2017 버전 15.6 이상 버전 에서만 볼 수 있습니다.
* 크래시 덤프 파일을 사후에 디버깅 하는 경우 Windows 10 버전 1607, Windows Server 2016 이상 버전의 windows에서 크래시를 만든 경우에만 스레드 이름이 표시 됩니다.

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

프로그램에서 스레드 이름을 설정 하는 또 다른 방법은 특수 하 게 구성 된 예외를 throw 하 여 원하는 스레드 이름을 Visual Studio 디버거에 전달 하는 것입니다.

혜택:
* 모든 버전의 Visual Studio에서 작동 합니다.

주의 사항:
* 는 예외 기반 메서드가 사용 될 때 디버거가 연결 된 경우에만 작동 합니다.
* 이 메서드를 사용 하 여 설정 된 스레드 이름은 덤프 또는 성능 분석 도구에서 사용할 수 없습니다.

*예제:*

아래에 표시 된 `SetThreadName` 함수는이 예외 기반 접근 방법을 보여 줍니다. @No__t_1 호출이 완료 된 후 `threadName` 매개 변수에 대 한 메모리가 해제 될 수 있도록 스레드 이름이 스레드에 자동으로 복사 됩니다.

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

## <a name="see-also"></a>관련 항목:
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [방법: 관리 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-managed-code.md)
