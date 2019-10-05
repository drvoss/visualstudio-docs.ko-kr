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
ms.openlocfilehash: 7346b6fd8fbd483021437638f9e134ead88a0b93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846325"
---
# <a name="jit-optimization-and-debugging"></a>JIT 최적화 및 디버깅
**최적화는.NET의 작동 방식:** 코드를 디버그 하려는 경우 쉽습니다 경우 코드는 **되지** 최적화 합니다. 코드를 최적화 하는 경우 컴파일러 및 런타임 코드를 변경 합니다 내보낸 CPU를 더 빠르게 실행 하지만 원래 소스 코드에 덜 직접적인 매핑이 때문입니다. 즉, 디버거를 자주 코드 단계별 실행 및 로컬 변수의 값을 알려 수 없는 중단점 예상한 대로 작동 하지 않을 수 있습니다.

일반적으로 릴리스 빌드 구성 최적화 된 코드를 만들고 디버그 빌드 구성 않습니다. `Optimize` MSBuild 속성 컴파일러 코드 최적화에 지시 하는지 여부를 제어 합니다.

.NET 에코 시스템에서 코드는 2 단계 프로세스의 CPU 지침 원본의 옵션이 인: 첫 번째는 C# 컴파일러는 MSIL을 호출 하는 중간 이진 형식으로 입력 한 텍스트를 변환 하 고.dll 파일에 작성이 합니다. 나중에.NET 런타임 CPU 지침에 대 한이 MSIL을 변환합니다. 두 단계는 어느 정도 최적화할 수 있지만 보다 중요 한 최적화를 수행 하는.NET 런타임에서 수행 하는 두 번째 단계입니다.

**'(관리 전용) 모듈을 로드할 때 JIT 최적화' 옵션:** 디버거가 대상 프로세스 내에서 사용 하도록 설정 하는 최적화를 사용 하 여 컴파일되는 DLL을 로드 하는 경우를 제어 하는 옵션을 표시 합니다. 이 옵션을 선택 하지 않으면 (기본 상태),.NET 런타임 CPU 코드를 MSIL 코드 컴파일되면 그대로 남아 있습니다 최적화 기능을 사용 합니다. 옵션을 선택한 경우 디버거는 최적화가 해제 될 요청 합니다.

찾으려고 합니다 **(관리 전용) 모듈을 로드할 때 JIT 최적화** 옵션을 선택 **도구** > **옵션**를 선택한 후는  **일반적인** 페이지의 **디버깅** 노드.

**이 옵션을 선택 해야 경우 있습니다.** Nuget 패키지와 같은 다른 원본에서 Dll을 다운로드 하 고이 DLL의 코드를 디버그 하려는 경우이 옵션을 선택 합니다. 이렇게 하려면 순서로이 DLL에 대 한 기호 (.pdb) 파일을 찾아야 합니다.

관심이 있다면만 로컬로 작성 하는 코드를 디버깅, 그대로이 옵션 선택 하지 않은, 경우에 따라이 옵션을 사용 하면 훨씬 느려집니다 디버깅에 적합 합니다. 저하 시킵니까 이유 두 가지 있습니다.

* 최적화 된 코드를 더 빠르게 실행 됩니다. 많은 코드에 대 한 최적화를 해제 하는 경우 성능에 영향을 추가할 수 있습니다.
* 내 코드만 사용 하도록 설정 하는 경우 디버거도 시도 최적화 된 Dll에 대 한 기호를 로드 합니다. 기호 찾기 시간이 오래 걸릴 수 있습니다.

**이 옵션의 제한 사항:** 이 옵션은 여기서 두 상황 **하지** 작동 합니다.

1. 디버거를 연결 하는 이미 실행 중인 프로세스에는 있는 경우에서이 옵션에는 디버거가 연결 된 시점에 이미 로드 된 모듈에 영향을 주지 해야 합니다.
2. 이 옵션은 된 Dll에 영향을 주지 미리 (또는 사이즈) 네이티브 코드로 컴파일됩니다. 그러나 변수 'COMPlus_ZapDisable'는 '1'로 설정 된 환경으로 프로세스를 시작 하 여 미리 컴파일된 코드의 사용을 비활성화할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [관리되는 실행 프로세스](/dotnet/standard/managed-execution-process)
