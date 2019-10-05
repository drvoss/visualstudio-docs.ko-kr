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
ms.openlocfilehash: 009422eaf9ac81af6e8f9d48732655b2528c85a0
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976142"
---
# <a name="reliability-warnings"></a>안정성 경고

안정성 경고 올바른 메모리 및 스레드 사용과 같은 라이브러리 및 응용 프로그램 안정성을 지원합니다. 안정성 규칙은 다음과 같습니다.

|규칙|설명|
|----------|-----------------|
|[CA2000: 범위를 벗어나기 전에 개체를 삭제 합니다.](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|개체의 종료자가 실행되지 못하도록 하는 예외 이벤트가 발생할 수 있기 때문에 개체에 대한 모든 참조가 범위를 벗어나기 전에 개체를 명시적으로 삭제해야 합니다.|
|[CA2001: 문제가 있는 메서드를 호출 하지 마십시오.](../code-quality/ca2001-avoid-calling-problematic-methods.md)|멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다.|
|[CA2002: 약한 id 가진 개체를 잠그지 마십시오.](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|애플리케이션 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다. 약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 애플리케이션 도메인의 스레드에 의해 차단될 수 있습니다.|
|[CA2003: 파이버를 스레드로 취급 하지 마십시오](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|관리 되는 스레드가 Win32 스레드라고 취급 됩니다.|
|[CA2004: GC에 대 한 호출을 제거 합니다. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|SafeHandle 사용 하도록 변환 하는 경우 GC에 대 한 모든 호출을 제거 합니다. KeepAlive (개체)입니다. 이 경우 클래스 GC를 호출할 필요가 없습니다. KeepAlive를 종료 자가 없는 있지만 OS를 마무리 하려면 SafeHandle 사용을 가정 하에 대 한 처리 합니다.|
|[CA2006: 네이티브 리소스를 캡슐화 하기 위해 SafeHandle 사용](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|관리 코드에 IntPtr을 사용하는 것은 잠재적인 보안 및 안정성 문제를 나타냅니다. IntPtr을 사용할 때마다 SafeHandle 또는 유사한 기술을 대신 사용해야 하는지 여부를 결정하도록 검토해야 합니다.|
|[CA2007: 직접 작업을 기다리지 않습니다](../code-quality/ca2007-do-not-directly-await-task.md)|비동기 메서드이기 [기다리는](/dotnet/csharp/language-reference/keywords/await) 는 <xref:System.Threading.Tasks.Task> 직접.|