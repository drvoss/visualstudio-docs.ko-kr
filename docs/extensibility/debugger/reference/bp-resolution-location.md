---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed287f2d90e1ee92c7e0fd4ae685fbb9f38854f4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350580"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
중단점 해결 위치의 구조를 지정합니다.

## <a name="syntax"></a>구문

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>멤버
`bpType`\
값을 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) 해석 하는 방법을 지정 하는 열거형을 `bpResLocation` union 또는 `unionmemberX` 멤버.

`bpResLocation.bpresCode`\
[C++ 만] 포함 된 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) 하는 경우 구조체 `bpType`  =  `BPT_CODE`합니다.

`bpResLocation.bpresData`\
[C++ 만] 포함 된 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 하는 경우 구조체 `bpType`  =  `BPT_DATA`합니다.

`bpResLocation.unused`\
[C++ 만] 자리 표시자입니다.

`unionmember1`\
[C# 만] 해석 하는 방법에 대 한 설명을 참조 하세요.

`unionmember2`\
[C# 만] 해석 하는 방법에 대 한 설명을 참조 하세요.

`unionmember3`\
[C# 만] 해석 하는 방법에 대 한 설명을 참조 하세요.

`unionmember4`\
[C# 만] 해석 하는 방법에 대 한 설명을 참조 하세요.

## <a name="remarks"></a>설명
이 구조체의 멤버인 합니다 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 하 고 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조입니다.

 [C# 만] `unionmemberX` 멤버는 다음 표에 따라 해석 됩니다. 왼쪽된 열을 살펴보면를 `bpType` 한 다음 각 기능 확인에 걸쳐 값 `unionmemberX` 마샬링 및 멤버 나타냅니다는 `unionmemberX` 적절 하 게 합니다. C#에서이 구조를 해석 하는 방법에 대 한 예제를 참조 하세요.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (데이터 식)|`string` (함수 이름)|`string` (이미지 이름)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>예제
해석 하는 방법을 보여 주는이 예제는 `BP_RESOLUTION_LOCATION` C#의 구조입니다.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
