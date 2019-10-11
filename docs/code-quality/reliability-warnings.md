---
title: 안정성 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252591"
---
# <a name="reliability-warnings"></a>안정성 경고

안정성 경고는 올바른 메모리 및 스레드 사용량과 같은 라이브러리 및 응용 프로그램 안정성을 지원 합니다. 안정성 규칙은 다음과 같습니다.

|규칙|설명|
|----------|-----------------|
|[CA2000: @ No__t 범위를 벗어나기 전에 개체를 삭제 하십시오.-0|개체의 종료자가 실행되지 못하도록 하는 예외 이벤트가 발생할 수 있기 때문에 개체에 대한 모든 참조가 범위를 벗어나기 전에 개체를 명시적으로 삭제해야 합니다.|
|[CA2001: 문제가 있는 메서드를 호출 하지 않습니다 @ no__t-0|멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다.|
|[CA2002: 약한 id를 가진 개체를 잠그지 않음 @ no__t-0|응용 프로그램 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다. 약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 응용 프로그램 도메인의 스레드에 의해 차단될 수 있습니다.|
|[CA2003: 파이버를 스레드로 처리 하지 않음 @ no__t-0|관리 되는 스레드가 Win32 스레드로 처리 되 고 있습니다.|
|[CA2004: GC에 대 한 호출을 제거 합니다. KeepAlive @ no__t-0|SafeHandle 사용으로 변환 하는 경우 GC에 대 한 모든 호출을 제거 합니다. KeepAlive (개체). 이 경우 클래스는 GC를 호출할 필요가 없습니다. KeepAlive는 종료 자가 없지만 SafeHandle을 사용 하 여이에 대 한 OS 핸들을 마무리 한다고 가정 합니다.|
|[CA2006: SafeHandle을 사용 하 여 네이티브 리소스 캡슐화 @ no__t-0|관리 코드에 IntPtr을 사용하는 것은 잠재적인 보안 및 안정성 문제를 나타냅니다. IntPtr을 사용할 때마다 SafeHandle 또는 유사한 기술을 대신 사용해야 하는지 여부를 결정하도록 검토해야 합니다.|
|[CA2007: 작업을 직접 기다리지 않음 @ no__t-0|비동기 메서드는 <xref:System.Threading.Tasks.Task>를 직접 [기다립니다.](/dotnet/csharp/language-reference/keywords/await)|
