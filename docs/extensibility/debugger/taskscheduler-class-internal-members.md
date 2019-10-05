---
title: TaskScheduler 클래스-내부 멤버 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 865e12819a5e7325886c0f7f5d8425a6b3d2e393
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331327"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler 클래스-내부 멤버
이 문서에서는 설명의 internal 멤버를 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 도움이 되는 클래스 사용자 지정 디버거를 구현 합니다. 이 클래스에 대 한 일반 정보에 대 한 참조를 <xref:System.Threading.Tasks.TaskScheduler> 참조 문서입니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib (에서 *mscorlib.dll*)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|이름|설명|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|모든 예약 된 작업의 배열을 검색합니다.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|모든 배열을 검색 <xref:System.Threading.Tasks.TaskScheduler> 현재 활성화 되어 있는 개체입니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고자료
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [.NET Framework에 대 한 병렬 확장 기능 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)