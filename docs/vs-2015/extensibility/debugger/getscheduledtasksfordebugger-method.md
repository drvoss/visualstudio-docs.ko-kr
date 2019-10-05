---
title: GetScheduledTasksForDebugger 메서드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4ac6fa753be7672f1e698bda231bd11217c10d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152728"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger 메서드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

모든 예약 된 작업의 배열을 검색합니다.  
  
 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **어셈블리:** mscorlib (mscorlib.dll)  
  
 .NET Framework에서이 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>반환 값  
 모든 예약 된 작업의 배열입니다. 각 작업 실행 되거나 실행이 완료 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 스레드로부터 안전 하지 않습니다 및 다른 인스턴스의 동시 사용 하지 않아야 <xref:System.Threading.Tasks.TaskScheduler> 디버거가 다른 모든 스레드가 일시 중단 하는 경우에 디버거를 호출 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)
