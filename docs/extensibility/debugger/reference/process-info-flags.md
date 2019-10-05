---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0694d83409a492a1d950a17ac5e2298ba9b8578
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309396"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

설명 또는 프로세스의 속성을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
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

## <a name="fields"></a>필드

`PIFLAG_SYSTEM_PROCESS`\
프로세스가 시스템 프로세스 임을 나타냅니다.

`PIFLAG_DEBUGGER_ATTACHED`\
프로세스는 디버거에서 디버깅 되 고 있는지를 나타냅니다. 것을 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 디버거, 또는 일부 다른 디버거, 예를 들어, WinDbg를 수 있습니다.

`PIFLAG_PROCESS_STOPPED`\
프로세스 중지 되었음을 나타냅니다. 경우에만 유효한 `PIFLAG_DEBUGGER_ATTACHED` 도 지정 합니다. Visual Studio 2005 이상 사용할 수 있습니다.

`PIFLAG_PROCESS_RUNNING`\
프로세스가 실행 중임을 나타냅니다. 경우에만 유효한 `PIFLAG_DEBUGGER_ATTACHED` 도 지정 합니다. Visual Studio 2005 이상 사용할 수 있습니다.

## <a name="remarks"></a>설명

에 사용 되는 합니다 `Flags` 의 멤버는 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조입니다.

이러한 플래그는 비트과 결합 될 수 `OR`입니다.

## <a name="requirements"></a>요구 사항

헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료

- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)