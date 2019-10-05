---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e50fe4901ebcbf008bf191226502ccac8ec4cf5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339220"
---
# <a name="machineinfo"></a>MACHINE_INFO
특정 컴퓨터를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagMACHINE_INFO { 
   MACHINE_INFO_FIELDS Fields;
   BSTR                bstrName;
   MACHINE_INFO_FLAGS  Flags;
} MACHINE_INFO;
```

```csharp
public struct MACHINE_INFO { 
   public uint   Fields;
   public string bstrName;
   public uint   Flags;
};
```

## <a name="members"></a>멤버
 `Fields`\
 플래그의 조합을 합니다 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) 초기화 되는 구조체의 필드를 지정 하는 열거형입니다.

 `bstrName`\
 컴퓨터 이름입니다. 호출할 때와 동일한 [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)합니다.

 `Flags`\
 플래그의 조합 된 [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) 컴퓨터 특성을 설명 하는 열거형입니다.

## <a name="remarks"></a>설명
 이 구조에 대 한 호출에서 반환 되는 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) 메서드.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)