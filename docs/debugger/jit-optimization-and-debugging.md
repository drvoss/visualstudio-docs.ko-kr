---
title: JIT 최적화 및 디버깅 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae11860aaa64448cd4d23b5602cf4c2da1575ce3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916209"
---
# <a name="jit-optimization-and-debugging"></a>JIT 최적화 및 디버깅
코드를 디버그 하려는 경우 코드를 최적화 **하지** 않으면 더 쉽게 수행할 수 있습니다. 코드가 최적화 되 면 컴파일러와 런타임이 내보낸 CPU 코드를 변경 하 여 더 빠르게 실행 되지만 원래 소스 코드에 대 한 직접적인 매핑이 줄어듭니다. 매핑이 덜 직접적인 경우 디버거는 지역 변수의 값을 알 수 없는 경우가 많으며 코드 단계별 실행 및 중단점이 정상적으로 작동 하지 않을 수 있습니다.

> [!NOTE]
> JIT (Just-in-time) 디버깅에 대 한 자세한 내용은 [이 설명서](../debugger/debug-using-the-just-in-time-debugger.md)를 참조 하세요.

## <a name="how-optimizations-work-in-net"></a>.NET에서 최적화가 작동 하는 방식 
일반적으로 릴리스 빌드 구성은 최적화 된 코드를 만들며 디버그 빌드 구성은 그렇지 않습니다. `Optimize` MSBuild 속성은 컴파일러가 코드를 최적화 하도록 지시 되었는지 여부를 제어 합니다.

.NET 에코 시스템에서 코드는 2 단계 프로세스의 소스에서 CPU 명령으로 전환 됩니다. 먼저 C# 컴파일러가 입력 한 텍스트를 msil 이라는 중간 이진 형식으로 변환 하 고 msil을 .dll 파일에 씁니다. 나중에 .NET 런타임에서이 MSIL을 CPU 명령으로 변환 합니다. 두 단계 모두 일정 수준까지 최적화할 수 있지만 .NET 런타임에서 수행 하는 두 번째 단계는 더 중요 한 최적화를 수행 합니다.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>' 모듈 로드 시 JIT 최적화를 표시 하지 않음 (관리 전용) ' 옵션
디버거는 최적화를 사용 하 여 컴파일된 DLL이 대상 프로세스 내에서 로드 될 때 발생 하는 작업을 제어 하는 옵션을 노출 합니다. 이 옵션을 선택 하지 않으면 (기본 상태) .NET 런타임에서 MSIL 코드를 CPU 코드로 컴파일할 때 최적화를 사용 하도록 설정 된 상태로 유지 됩니다. 이 옵션을 선택 하면 디버거가 최적화를 사용 하지 않도록 요청 합니다.

**모듈을 로드할 때 JIT 최적화 적용 안 함 (관리 전용)** 옵션을 찾으려면 **도구** > **옵션**을 선택한 다음 **디버깅** 노드 아래에서 **일반** 페이지를 선택 합니다.

![JIT 최적화를 표시 하지 않습니다.](../debugger/media/suppress-jit-tool-options.png "JIT 최적화를 표시 하지 않습니다.")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>' JIT 최적화 표시 안 함 ' 옵션을 언제 선택 해야 하나요?
Nuget 패키지와 같은 다른 소스에서 Dll을 다운로드 하 고이 DLL의 코드를 디버깅 하려는 경우이 옵션을 선택 합니다. 비 표시 작업이 작동 하려면이 DLL에 대 한 기호 (.pdb) 파일도 찾아야 합니다.

로컬로 빌드하는 코드를 디버깅 하려는 경우에만이 옵션을 선택 하지 않은 상태로 두는 것이 가장 좋습니다 .이 옵션을 사용 하도록 설정 하면 디버깅이 크게 느려질 수 있습니다. 이 속도가 느려지는 이유는 다음 두 가지입니다.

* 최적화 된 코드는 더 빠르게 실행 됩니다. 많은 코드에 대 한 최적화를 해제 하는 경우 성능 영향이 추가 될 수 있습니다.
* 내 코드만 사용 하도록 설정 된 경우 디버거는 최적화 된 Dll에 대 한 기호 로드를 시도 하지 않습니다. 기호 찾기에는 시간이 오래 걸릴 수 있습니다.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>' JIT 최적화 적용 안 함 ' 옵션의 제한 사항 
이 옵션을 설정 해도 작동 **하지 않는** 두 가지 경우가 있습니다.

1. 디버거를 이미 실행 중인 프로세스에 연결 하는 경우에는 디버거가 연결 될 때 이미 로드 된 모듈에는이 옵션이 적용 되지 않습니다.
2. 이 옵션은 네이티브 코드에 미리 컴파일된 Dll (하루가 지난)에는 영향을 주지 않습니다. 그러나 환경 변수 **' COMPlus_ReadyToRun '** 을 **' 0 '** 으로 설정 하 여 프로세스를 시작 하 여 미리 컴파일된 코드를 사용 하지 않도록 설정할 수 있습니다. 이렇게 하면 .NET Core 런타임에 미리 컴파일된 이미지를 사용 하지 않도록 설정 하 여 런타임을 강제로 JIT 컴파일 프레임 워크 코드에 적용 합니다. 

    > [!IMPORTANT]
    > .NET Framework 또는 이전 버전의 .NET Core (2.x 이상)를 대상으로 하는 경우 환경 변수 ' COMPlus_ZapDisable '도 추가 하 고 ' 1 '로 설정 합니다.

    **Visual Studio에서 .NET Core 프로젝트에 대 한 환경 변수를 설정 하려면 다음을 수행 합니다.**
    1. **솔루션 탐색기**에서 프로젝트 파일을 **마우스 오른쪽 단추로 클릭** 하 고 **속성**을 선택 합니다.
    2. **디버그** 탭으로 이동 하 여 **환경 변수**아래에서 **추가** 단추를 클릭 합니다.
    3. 이름 (키)을 **COMPlus_ReadyToRun** 설정 하 고 값을 **0**으로 설정 합니다.

    ![환경 변수 COMPlus_ReadyToRun 설정](../debugger/media/environment-variables-debug-menu.png "환경 변수 COMPlus_ReadyToRun 설정")

## <a name="see-also"></a>참조
- [Dotnet Framework 소스를 디버깅 하는 방법](../debugger/how-to-debug-dotnet-framework-source.md)
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [관리되는 실행 프로세스](/dotnet/standard/managed-execution-process)
