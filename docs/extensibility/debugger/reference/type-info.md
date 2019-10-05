---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86212a5ef6f417dae2ae345b1367e041c3cf9095
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316124"
---
# <a name="typeinfo"></a>TYPE_INFO
이 구조는 다양 한 종류의 필드의 형식에 대 한 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>멤버
 `dwKind`\
 값을 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 합집합을 해석 하는 방법을 결정 하는 열거형입니다.

 `type.typeMeta`\
 [C++ 만] 포함 된 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 경우 구조체 `dwKind` 는 `TYPE_KIND_METADATA`합니다.

 `type.typePdb`\
 [C++ 만] 포함 된 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 경우 구조체 `dwKind` 는 `TYPE_KIND_PDB`합니다.

 `type.typeBuilt`\
 [C++ 만] 포함 된 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 경우 구조체 `dwKind` 는 `TYPE_KIND_BUILT`합니다.

 `type.unused`\
 사용 되지 않는 안쪽 여백입니다.

 `type`\
 공용 구조체의 이름입니다.

 `unionmember`\
 [C# 만] 적절 한 구조 형식에이에 따라 마샬링 `dwKind`합니다.

## <a name="remarks"></a>설명
 이 구조에 전달 되는 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 메서드 위치에서 채워집니다. 구조체의 내용을 해석 되는 방식을 기반으로 합니다 `dwKind` 필드입니다.

> [!NOTE]
> [C++ 만] 경우 `dwKind` equals `TYPE_KIND_BUILT`, 기본 릴리스해야 하는 것 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 제거 하는 경우 개체는 `TYPE_INFO` 구조입니다. 이를 위해 `typeInfo.type.typeBuilt.pUnderlyingField->Release()`를 호출합니다.

 [C# 만] 다음 표에서 해석 하는 방법을 보여 줍니다는 `unionmember` 각 종류의 형식에 대 한 멤버입니다. 형식의 한 종류에 대 한이 작업을 수행 하는 방법을 보여 줍니다.

|`dwKind`|`unionmember` 로 해석|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>예제
 해석 하는 방법을 보여 주는이 예제는 `unionmember` 의 멤버는 `TYPE_INFO` C#의 구조입니다. 이 예제에서는 하나의 형식만 해석 (`TYPE_KIND_METADATA`) 하지만 다른 동일한 방식으로 해석 됩니다.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)