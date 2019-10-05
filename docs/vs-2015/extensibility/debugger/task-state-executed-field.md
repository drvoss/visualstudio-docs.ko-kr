---
title: TASK_STATE_EXECUTED 필드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6dcfb6c7b4b79d1abd2b393e32b9795f613c205a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162220"
---
# <a name="taskstateexecuted-field"></a>TASK_STATE_EXECUTED 필드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

작업이 실행되고 있지만 완료되지 않았습니다.  
  
 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **어셈블리:** mscorlib (mscorlib.dll)  
  
 .NET Framework에서이 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## <a name="remarks"></a>설명  
 경우는 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 이 값을 포함 하는 필드를 <xref:System.Threading.Tasks.Task.Status%2A> 속성에서 반환 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
