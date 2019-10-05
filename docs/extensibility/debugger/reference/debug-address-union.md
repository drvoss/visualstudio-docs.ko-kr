---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3dbd114fb06bfd688c720744dbbad69bd0dae6aa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346278"
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
주소의 다양 한 종류를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>멤버
`dwKind`\
값을 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형, 공용 구조체를 해석 하는 방법을 지정 합니다.

`addr.addrNative`\
[C++ 만] 포함 된 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_NATIVE =.

`addr.addrThisRel`\
[C++ 만] 포함 된[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_UNMANAGED_THIS_RELATIVE =.

`addr.addUPhysical`\
[C++ 만] 포함 된[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_UNMANAGED_PHYSICAL =.

`addr.addrMethod`\
[C++ 만] 포함 된[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_METHOD =.

`addr.addrField`\
[C++ 만] 포함 된[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_FIELD =.

`addr.addrLocal`\
[C++ 만] 포함 된[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_LOCAL =.

`addr.addrParam`\
[C++ 만] 포함 된[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_PARAM =.

`addr.addrArrayElem`\
[C++ 만] 포함 된[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_ARRAYELEM =.

`addr.addrRetVal`\
[C++ 만] 포함 된[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 하는 경우 구조체 `dwKind` ADDRESS_KIND_RETVAL =.

`addr.unused`\
[C++ 만] 패딩 합니다.

`addr`\
[C++ 만] 공용 구조체의 이름입니다.

`unionmember`\
[C# 만] 이 값을 기반으로 적절 한 구조 형식으로 마샬링할 수 해야 `dwKind`합니다. 간의 연결에 대 한 주의 참조 하세요. `dwKind` 및 공용 구조체의 해석 합니다.

## <a name="remarks"></a>설명
이 구조체의 일부인를 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조체이 고 다양 한 다른 유형의 주소 중 하나를 나타냅니다 (합니다 `DEBUG_ADDRESS` 구조에 대 한 호출에 의해 채워진 합니다 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드).

 [C# 만] 다음 표에서 해석 하는 방법을 보여 줍니다는 `unionmember` 주소의 각 종류에 대 한 멤버입니다. 한 가지 주소에 대 한이 작업을 수행 하는 방법을 보여 줍니다.

|`dwKind`|`unionmember` 로 해석|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>예제
이 예제에는 일종의 주소를 해석 하는 방법을 보여 줍니다 (`METADATA_ADDRESS_ARRAYELEM`)의 `DEBUG_ADDRESS_UNION` C#의 구조입니다. 나머지 요소는 동일한 방식으로 해석할 수 있습니다.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
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
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
