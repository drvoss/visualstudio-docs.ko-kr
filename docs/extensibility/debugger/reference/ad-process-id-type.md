---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9df097037a84af9da63f0a98ee6cfa3b28cfcdd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351386"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
프로세스 ID를 해석 하는 방법을 지정 합니다 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조입니다.

## <a name="syntax"></a>구문

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>필드
`AD_PROCESS_ID_SYSTEM`\
프로세스 ID 시스템 식별자입니다. 사용 합니다 `ProcessId.dwProcessId` 필드를 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조입니다.

`AD_PROCESS_ID_GUID`\
프로세스 ID는 GUID입니다. 사용 합니다 `ProcessId.guidProcessId` 필드는 `AD_PROCESS_ID` 구조입니다.

## <a name="remarks"></a>설명
에 사용 되는 합니다 `ProcessIdType` 의 멤버는 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조에 포함 된 프로세스 ID의 형식을 식별 하는 구조입니다. 해석 하는 방법을 결정 합니다 `ProcessId` 구조의 공용 구조체입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
