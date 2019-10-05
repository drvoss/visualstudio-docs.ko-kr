---
title: 메모리에서 실행 되는 서비스 디버거 | Microsoft Docs
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
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854020"
---
# <a name="debugger-services-running-out-of-memory"></a>메모리에서 실행 되는 서비스 디버거
디버깅 서비스 메모리가 부족 하는 디버깅 세션의 종료를 발생 합니다.

## <a name="to-investigate-this-error-on-windows"></a>Windows에서이 오류를 조사 하려면
- 프로세스 메모리 그래프에서 확인할 수 있습니다 합니다 **진단 도구** 창 대상 응용 프로그램 메모리의 큰 증가 발생 하는 경우를 확인 합니다. 그렇다면 사용 합니다 **메모리 사용량** 새로운 진단 도구는 기본 문제를 참조 하십시오 [메모리 사용량 분석](../profiling/memory-usage.md)합니다.

- 사용 하 여 대상 응용 프로그램 메모리를 많이 사용 없으면 합니다 **작업 관리자** VS Code (vsdbg.exe/vsdbg-ui.exe) 또는 Visual Studio (devenv.exe) 작업자 프로세스 (msvsmon.exe)의 메모리 사용량을 확인 창 디버거 문제 인지 확인 합니다. 메모리 부족 프로세스 devenv.exe를 실행 하는 Visual Studio 확장의 수를 줄이면 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
- [블로그 게시물: 디버깅 하는 동안 CPU와 메모리 분석](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [메모리 관리에 대 한](/windows/win32/memory/about-memory-management)
