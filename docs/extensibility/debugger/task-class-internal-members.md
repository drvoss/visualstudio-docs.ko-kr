---
title: Task 클래스-내부 멤버 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bfa171655afd808de4bd86fe0fbdb99531d2ab2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348423"
---
# <a name="task-class---internal-members"></a>Task 클래스-내부 멤버
이 문서에서는 설명의 internal 멤버를 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 도움이 되는 클래스 사용자 지정 디버거를 구현 합니다. 이 클래스에 대 한 일반 정보에 대 한 참조를 <xref:System.Threading.Tasks.Task> 참조 문서입니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib (에서 *mscorlib.dll*)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|이름|설명|
|----------|-----------------|
|[SetNotificationForWaitCompletion 메서드](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|설정 하거나 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 상태 비트를 지웁니다.|
|[NotifyDebuggerOfWaitCompletion 메서드](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|디버거에서 중단점 대상으로 사용 된 자리 표시자 메서드.|

### <a name="fields"></a>필드

|이름|설명|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|실행할 코드를 나타내는 대리자를 <xref:System.Threading.Tasks.Task> 개체입니다.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|추가 속성을 저장 합니다 <xref:System.Threading.Tasks.Task> 개체입니다.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|에 대 한 지원 필드를 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 부모 속성입니다.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|현재 상태에 대 한 정보를 저장 합니다 <xref:System.Threading.Tasks.Task> 개체입니다.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|작업에 의해 사용 될 데이터를 표시 하는 개체입니다.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|에 대 한 지원 필드를 <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> 속성입니다.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|에 대 한 다음 사용할 수 있는 식별자를 <xref:System.Threading.Tasks.Task> 개체입니다.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|실행 중인 상태에 도달 하기 전에 작업을 취소 한다는 또는 작업의 취소를 확인 하 고 예외 없이 완료를 나타냅니다.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|작업이 실행 중임을 나타냅니다.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|처리 되지 않은 예외로 인해 작업이 완료 되었음을 나타냅니다.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|작업 실행을 성공적으로 완료 되었음을 나타냅니다.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|작업 대리자를 실행 했습니다. 암시적으로 연결 된 자식 작업이 완료 되기를 기다리고 있음을 나타냅니다.|

## <a name="remarks"></a>설명
 입구 표시 하므로 다음 내부 메서드는 디버거 엔진에 유용한 <xref:System.Threading.Tasks.Task> 코드 실행 합니다.

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>참고자료
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [.NET Framework에 대 한 병렬 확장 기능 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)