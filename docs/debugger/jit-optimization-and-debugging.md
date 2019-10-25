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
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731617"
---
# <a name="jit-optimization-and-debugging"></a>JIT 최적화 및 디버깅
**.Net에서 최적화가 작동 하는 방식:** 코드를 디버그 하려는 경우 코드를 최적화 **하지** 않으면 더 쉽게 수행할 수 있습니다. 이는 코드를 최적화할 때 컴파일러와 런타임이 내보낸 CPU 코드를 변경 하 여 더 빠르게 실행 되지만 원래 소스 코드에 대 한 직접적인 매핑을 포함 하기 때문입니다. 즉, 디버거가 지역 변수의 값을 확인할 수 없는 경우가 많으며 코드 단계별 실행 및 중단점이 정상적으로 작동 하지 않을 수 있습니다.

일반적으로 릴리스 빌드 구성은 최적화 된 코드를 만들며 디버그 빌드 구성은 그렇지 않습니다. @No__t_0 MSBuild 속성은 컴파일러가 코드를 최적화 하도록 지시 되었는지 여부를 제어 합니다.

.NET 에코 시스템에서 코드는 2 단계 프로세스의 소스에서 CPU 명령으로 전환 됩니다. 먼저 C# 컴파일러가 입력 한 텍스트를 MSIL 이라는 중간 이진 형식으로 변환 하 고이를 .dll 파일에 씁니다. 나중에 .NET 런타임에서이 MSIL을 CPU 명령으로 변환 합니다. 두 단계 모두 일정 수준까지 최적화할 수 있지만 .NET 런타임에서 수행 하는 두 번째 단계는 더 중요 한 최적화를 수행 합니다.

**' 모듈 로드 시 JIT 최적화를 표시 하지 않습니다 (관리 전용) ' 옵션:** 디버거는 최적화를 사용 하 여 컴파일된 DLL이 대상 프로세스 내에서 로드 될 때 발생 하는 작업을 제어 하는 옵션을 노출 합니다. 이 옵션을 선택 하지 않으면 (기본 상태) .NET 런타임에서 MSIL 코드를 CPU 코드로 컴파일할 때 최적화를 사용 하도록 설정 된 상태로 유지 됩니다. 이 옵션을 선택 하면 디버거가 최적화를 사용 하지 않도록 요청 합니다.

**모듈을 로드할 때 JIT 최적화 적용 안 함 (관리 전용)** 옵션을 찾으려면 **도구**  > **옵션**을 선택한 다음 **디버깅** 노드 아래에서 **일반** 페이지를 선택 합니다.

**이 옵션을 선택 해야 하는 경우는 다음과 같습니다.** Nuget 패키지와 같은 다른 소스에서 Dll을 다운로드 하 고이 DLL의 코드를 디버깅 하려는 경우이 옵션을 선택 합니다. 이 작업을 수행 하려면이 DLL에 대 한 기호 (.pdb) 파일도 찾아야 합니다.

로컬로 빌드하는 코드를 디버깅 하려는 경우에만이 옵션을 선택 하지 않은 상태로 두는 것이 가장 좋습니다 .이 옵션을 사용 하도록 설정 하면 디버깅이 크게 느려질 수 있습니다. 이 속도는 다음과 같은 두 가지 이유로 인해 발생 합니다.

* 최적화 된 코드는 더 빠르게 실행 됩니다. 많은 코드에 대 한 최적화를 해제 하는 경우 성능 영향이 추가 될 수 있습니다.
* 내 코드만 사용 하도록 설정 된 경우 디버거는 최적화 된 Dll에 대 한 기호를 시도 하거나 로드 하지 않습니다. 기호 찾기에는 시간이 오래 걸릴 수 있습니다.

**이 옵션의 제한 사항:** 이 옵션은 다음과 같은 두 가지 경우에 작동 **하지** 않습니다.

1. 디버거를 이미 실행 중인 프로세스에 연결 하는 경우에는 디버거가 연결 될 때 이미 로드 된 모듈에는이 옵션이 적용 되지 않습니다.
2. 이 옵션은 네이티브 코드에 미리 컴파일된 Dll (하루가 지난)에는 영향을 주지 않습니다. 그러나 ' COMPlus_ZapDisable ' 환경 변수를 ' 1 '로 설정 하 여 프로세스를 시작 하면 미리 컴파일된 코드를 사용 하지 않도록 설정할 수 있습니다.

## <a name="see-also"></a>참조
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [관리되는 실행 프로세스](/dotnet/standard/managed-execution-process)
