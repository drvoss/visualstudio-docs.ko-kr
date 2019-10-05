---
title: GetTaskSchedulersForDebugger 메서드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8d038c8c67731fe1bff9ec705b5ddf416807a57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353715"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 메서드
모든 배열을 검색 <xref:System.Threading.Tasks.TaskScheduler> 현재 활성화 되어 있는 개체입니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib (에서 *mscorlib.dll*)

 .NET Framework에서이 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>반환 값
 모든 배열의 <xref:System.Threading.Tasks.TaskScheduler> 이 현재 활성 상태인 개체 <xref:System.AppDomain>합니다.

## <a name="remarks"></a>설명
 이 메서드는 스레드로부터 안전 하지 및 다른 인스턴스의 동시 사용 하면 안 <xref:System.Threading.Tasks.TaskScheduler>합니다. 디버거가 다른 모든 스레드가 일시 중단 하는 경우에 디버거에서이 메서드를 호출 합니다.

## <a name="see-also"></a>참고자료
- [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)