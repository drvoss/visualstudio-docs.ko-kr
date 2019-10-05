---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba419d0b10174e375cd15313fbc0770bf9d8cc0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311382"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
디버그 모듈 정보에 대 한 플래그를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>필드
 `MIF_NONE`\
 구조에 필드를 초기화/사용 합니다.

 `MIF_NAME`\
 초기화/사용 된 `m_bstrName` 필드를 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조입니다.

 `MIF_URL`\
 초기화/사용 된 `m_bstrUrl` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_VERSION`\
 초기화/사용 된 `m_bstrVersion` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_DEBUGMESSAGE`\
 초기화/사용 된 `m_bstrDebugMessage` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_LOADADDRESS`\
 초기화/사용 된 `m_addrLoadAddress` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_PREFFEREDADDRESS`\
 초기화/사용 된 `m_addrPreferredLoadAddress` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_SIZE`\
 초기화/사용 된 `m_dwSize` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_LOADORDER`\
 초기화/사용 된 `m_dwLoadOrder` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_TIMESTAMP`\
 초기화/사용 된 `m_TimeStamp` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_URLSYMBOLLOCATION`\
 초기화/사용 된 `m_bstrUrlSymbolLocation` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_FLAGS`\
 초기화/사용 된 `m_dwModuleFlags` 필드에 `MODULE_INFO` 구조입니다.

 `MIF_ALLFIELDS`\
 모든 필드의 초기화/사용 된 `MODULE_INFO` 구조입니다.

## <a name="remarks"></a>설명
 이러한 값을 인수로 전달 됩니다는 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 의 필드를 나타내려면 메서드는 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조는 초기화할 합니다.

 이러한 값에도 사용 됩니다는 `MODULE_INFO` 에 유효 하 고 사용 되는 필드는 구조체.

 이러한 플래그는 비트과 결합 될 수 `OR`입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)