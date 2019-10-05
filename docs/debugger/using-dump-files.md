---
title: 디버거에서 덤프 파일 사용 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f0b7edf8ef2670b70dbee25b70cac7b0597490b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676366"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Visual Studio 디버거에서 덤프 파일

<a name="BKMK_What_is_a_dump_file_"></a> A *덤프 파일* 시간에서 지점에서 앱에 대해 로드 된 모듈을 확인 하 고 실행 중이 던 프로세스를 보여 주는 스냅숏입니다. 힙 정보를 사용 하 여 덤프 또한 앱의 메모리 스냅숏을 이때 합니다.

Visual Studio에서 힙을 사용 하 여 덤프 파일을 열고 디버그 세션의 중단점에서 중지 같습니다. 실행을 계속할 수 있지만 덤프 시 스택, 스레드 및 응용 프로그램의 변수 값을 검사할 수 있습니다.

덤프는 개발자에 액세스할 수 없는 컴퓨터에서 문제를 디버깅 하려면 주로 사용 됩니다. 작동 중단을 재현를 자신의 컴퓨터에 중단 수 없는 경우 고객의 컴퓨터에서 덤프 파일을 사용할 수 있습니다. 테스터는 크래시를 저장 하거나 중단 자세한 테스트에 사용할 데이터 덤프를 만들 수도 있습니다.

Visual Studio 디버거는 관리 코드 또는 네이티브 코드에 대한 덤프 파일을 저장할 수 있습니다. Visual Studio에서 만들었거나 파일을 저장 하는 다른 앱에서 덤프를 디버깅할 수는 *미니 덤프* 형식입니다.

## <a name="BKMK_Requirements_and_limitations"></a> 요구 사항 및 제한 사항

- 64 비트 컴퓨터에서 덤프를 디버깅 하려면 Visual Studio 64 비트 컴퓨터에서 실행 되어야 합니다.

- Visual Studio에서는 ARM 디바이스에서 네이티브 애플리케이션의 덤프 파일을 디버깅할 수 있습니다. 네이티브 디버거에서 하지만 ARM 장치에서 관리 되는 응용 프로그램의 덤프를 디버그할 수도 있습니다.

- 디버그 [커널 모드](/windows-hardware/drivers/debugger/kernel-mode-dump-files) 덤프 파일 또는 사용 하 여를 [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) 에서 Windows 용 디버깅 도구를 다운로드 디버깅 Visual Studio에서 확장을 [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk)합니다.

- Visual Studio는 이전에 저장 된 덤프 파일을 디버깅할 수 없습니다 [전체 사용자 모드 덤프](/windows/desktop/wer/collecting-user-mode-dumps) 형식입니다. 전체 사용자 모드 덤프는 힙 사용 하 여 덤프와 동일 합니다.

- 최적화된 코드의 덤프 파일 디버깅은 혼란을 줄 수 있습니다. 예를 들어 함수의 컴파일러 인라인 처리로 예기치 않은 호출 스택이 발생할 수 있으며 다른 최적화로 변수의 수명이 변경될 수 있습니다.

## <a name="BKMK_Dump_files__with_or_without_heaps"></a> 힙을 포함하거나 포함하지 않는 덤프 파일

덤프 파일 수 또는 힙 정보가 없을 수 있습니다.

- **힙 사용 하 여 파일을 덤프** 덤프 시 변수의 값을 포함 하 여 앱의 메모리 스냅숏을 포함 합니다. Visual Studio는 또한 디버깅을 훨씬 쉽게 만들 수 있는 힙 덤프 파일에서 로드 된 네이티브 모듈의 이진 파일을 저장 합니다. 찾을 수 없는 앱 이진 하는 경우에 visual Studio는 힙 사용 하 여 덤프 파일에서 기호를 로드할 수 있습니다.

- **힙이 없는 파일을 덤프** 힙을 사용 하 여 덤프 보다 훨씬 작은 있지만 디버거 기호 정보를 찾으려면 응용 프로그램 이진 파일을 로드 해야 합니다. 로드 된 이진 파일에 덤프를 만드는 동안 실행 중인 것과 정확히 일치 해야 합니다. 힙이 없는 덤프 스택 변수의 값을 저장합니다.

## <a name="BKMK_Create_a_dump_file"></a> 덤프 파일 만들기

Visual Studio에서 프로세스를 디버깅 하는 동안 디버거가 예외 나 중단점에서 중지 되었을 때를 덤프를 저장할 수 있습니다.

사용 하 여 [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md) 사용 하도록 설정 Visual Studio 외부에서 충돌된 한 프로세스에 Visual Studio 디버거를 디버거에서 덤프 파일을 저장 합니다. 참조 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)합니다.

**덤프 파일을 저장하려면**

1. 디버깅 하는 동안 오류 또는 중단점에서 중지 된 동안 선택 **디버깅할** > **이름으로 덤프 저장**합니다.

1. 에 **다른 이름으로 덤프 저장** 대화 상자의 **형식으로 저장**를 선택 **미니 덤프** 또는 **힙 사용 미니 덤프** (기본값).

1. 경로 이동 하 고 덤프 파일에 대 한 이름을 선택 하 고 선택한 **저장할**합니다.

>[!NOTE]
>Windows 미니 덤프 형식을 지 원하는 프로그램으로 덤프 파일을 만들 수 있습니다. 예를 들어 [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default)에 있는 **Procdump** 명령줄 유틸리티는 트리거에 따라서나 요청 시에 프로세스 크래시 덤프 파일을 만들 수 있습니다. 참조 [요구 사항 및 제한 사항](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) 다른 도구를 사용 하 여 덤프 파일을 만들도록 하는 방법에 대 한 정보에 대 한 합니다.

## <a name="BKMK_Open_a_dump_file"></a> 덤프 파일 열기

1. Visual Studio에서 선택 **파일** > **Open** > **파일**합니다.

1. **파일 열기** 대화 상자에서 덤프 파일을 찾아 선택합니다. 덤프 파일의 확장명은 일반적으로 *.dmp*입니다. **확인**을 선택합니다.

   합니다 **미니 덤프 파일 요약** 창 표시 요약 및 모듈에 대 한 정보를 덤프 파일 및 작업 수행할 수 있습니다.

   ![미니 덤프 요약 페이지](../debugger/media/dbg_dump_summarypage.png "미니 덤프 요약 페이지")

1. 아래 **작업**:
   - 기호 로드 위치를 설정 하려면 **기호 경로 설정**합니다.
   - 디버깅을 시작 하려면 선택 **만 관리를 사용 하 여 디버그**, **네이티브 전용 디버그**합니다 **혼합을 사용 하 여 디버그**, 또는 **관리 되는 메모리를 사용 하 여 디버그**합니다.

## <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> .Exe,.pdb 및 소스 파일 찾기

사용 하 여 디버깅 기능에 덤프 파일에 전체 Visual Studio 필요 합니다.

- 합니다 *.exe* 덤프를 생성 된 파일과 덤프 프로세스는 다른 바이너리 (Dll 등).
- *.exe* 및 기타 이진 파일에 대한 기호( *.pdb*) 파일
- *.exe* 하 고 *.pdb* 파일 버전 및에서 파일의 빌드와 정확히 일치 하는 덤프 생성 합니다.
- 관련 모듈에 대 한 원본 파일입니다. 소스 파일을 찾을 수 없는 경우 모듈의 디스어셈블리를 사용할 수 있습니다.

덤프를 힙 데이터가 있으면 Visual Studio에서 일부 모듈에 대 한 누락 된 이진 파일을 사용 하 여 처리할 수 있지만 유효한 호출 스택을 생성 하는 데 충분 한 모듈에 대 한 이진 파일이 있어야 합니다.

### <a name="search-paths-for-exe-files"></a>.Exe 파일의 경로 검색

Visual Studio에 대 한 이러한 위치를 자동으로 검색 *.exe* 덤프 파일에 포함 되지 않은 파일:

1. 덤프 파일을 포함 하는 폴더입니다.
2. 덤프 파일 지정 모듈 경로 덤프를 수집 하는 컴퓨터의 모듈 경로 합니다.
3. 에 지정 된 기호 경로 **도구가** (또는 **디버그**) > **옵션** > **디버깅**  >  **기호**합니다. 열 수도 있습니다는 **기호** 에서 페이지를 **작업** 창의 합니다 **덤프 파일 요약** 창. 이 페이지에서 검색할 위치를 더 추가할 수 있습니다.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>아니요 이진, 로드 된 기호 없음, 또는 소스 없음 페이지를 사용 합니다.

Visual Studio 파일을 찾을 수 없는 경우 덤프의 모듈을 디버그 해야 하는 것을 표시는 **이진 파일 없음**를 **기호를 찾을 수 없음**, 또는 **소스 없음** 페이지입니다. 이러한 페이지 해당 문제의 원인에 대 한 자세한 정보를 제공 하 고 파일을 찾을 수 있는 작업 링크를 제공 합니다. [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="see-also"></a>참고자료

- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)