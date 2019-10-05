---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205059"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

설명 또는 프로세스의 속성을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>멤버  
 PIFLAG_SYSTEM_PROCESS  
 프로세스가 시스템 프로세스 임을 나타냅니다.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 프로세스는 디버거에서 디버깅 되 고 있는지를 나타냅니다. 것을 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 디버거, 또는 일부 다른 디버거, 예를 들어, WinDbg를 수 있습니다.  
  
 PIFLAG_PROCESS_STOPPED  
 프로세스 중지 되었음을 나타냅니다. 경우에만 유효한 `PIFLAG_DEBUGGER_ATTACHED` 도 지정 합니다. 사용할 수 있는 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 이상.  
  
 PIFLAG_PROCESS_RUNNING  
 프로세스가 실행 중임을 나타냅니다. 경우에만 유효한 `PIFLAG_DEBUGGER_ATTACHED` 도 지정 합니다. 사용할 수 있는 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 이상.  
  
## <a name="remarks"></a>설명  
 에 사용 되는 합니다 `Flags` 의 멤버는 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조입니다.  
  
 이러한 플래그는 비트과 결합 될 수 `OR`입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
