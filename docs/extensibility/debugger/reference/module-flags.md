---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b8080710b3225f025c329e0c5cb42331e1a059f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346800"
---
# <a name="moduleflags"></a>MODULE_FLAGS
모듈에 설명 하는 데 사용 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>필드
 `MODULE_FLAG_NONE`\
 모듈이 없는 지정합니다.

 `MODULE_FLAG_SYSTEM`\
 시스템 모듈을 지정합니다.

 `MODULE_FLAG_SYMBOLS`\
 기호 모듈을 지정합니다.

 `MODULE_FLAG_64BIT`\
 64 비트 모듈을 지정합니다.

 `MODULE_FLAG_OPTIMIZED`\
 최적화 된 모듈을 지정 합니다. 이 상태에 반영 되는 **모듈** 창입니다.

 `MODULE_FLAG_UNOPTIMIZED`\
 최적화 되지 않은 모듈을 지정 합니다. 이 상태에 반영 되는 **모듈** 창입니다. 기본 상태입니다.

## <a name="remarks"></a>설명
 에 사용 되는 합니다 `m_dwModuleFlags` 의 멤버는 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조입니다.

 이러한 플래그는 비트과 결합 될 수 `OR`입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)