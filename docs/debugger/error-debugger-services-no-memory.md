---
title: 디버거 서비스에 메모리가 부족 합니다. | Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737834"
---
# <a name="debugger-services-running-out-of-memory"></a>메모리가 부족한 디버거 서비스
디버깅 서비스가 메모리 부족으로 인해 디버깅 세션이 종료 되었습니다.

## <a name="to-investigate-this-error-on-windows"></a>Windows에서이 오류를 조사 하려면
- **진단 도구** 창에서 프로세스 메모리 그래프를 확인 하 여 대상 응용 프로그램의 메모리가 크게 증가 하 고 있는지 확인할 수 있습니다. 그렇다면 **메모리 사용량 도구를** 사용 하 여 근본적인 문제를 진단 하려면 [메모리 사용 분석](../profiling/memory-usage.md)을 참조 하세요.

- 대상 응용 프로그램에서 많은 양의 메모리를 사용 하 고 있지 않은 경우 **작업 관리자** 창을 사용 하 여 Visual Studio (devenv.exe), 작업자 프로세스 (msvsmon.exe) 또는 VS Code (vsdbg .exe/vsdbg-ui)의 메모리 사용을 확인 하 여이가 인지 확인 합니다. 디버거 문제입니다. 메모리가 부족 한 프로세스를 실행 하는 경우에는 실행 중인 Visual Studio 확장 수를 줄이는 것이 좋습니다.

## <a name="see-also"></a>참조
- [블로그 게시물: 디버그 하는 동안 CPU 및 메모리 분석](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [메모리 관리 정보](/windows/win32/memory/about-memory-management)
