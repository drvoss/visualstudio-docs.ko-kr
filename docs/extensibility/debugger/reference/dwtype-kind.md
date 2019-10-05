---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12fe23d53939303be6b7e6a20ff12d2524d71593
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318133"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
형식의 해석 하는 방법을 지정는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다.

## <a name="syntax"></a>구문

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>필드
`TYPE_KIND_METADATA`\
합니다 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) union으로 해석할지를 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 구조입니다.

`TYPE_KIND_PDB`\
합니다 `TYPE_INFO` union으로 해석할지를 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 구조입니다.

`TYPE_KIND_BUILT`\
합니다 `TYPE_INFO` union으로 해석할지를 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 구조입니다.

## <a name="remarks"></a>설명
이 열거형의 값이 나타나는 `dwKind` 필드를 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 구조체이 고 해석 하는 방법을 결정 하는 데 사용 되는 `type` 공용 구조체 멤버입니다. 합니다 `TYPE_INFO` 구조에 대 한 호출에서 반환 되는 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
