---
title: CODE_PATH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 516122ee8aaaa0ed18537369eeeffb05be3ebf1c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327222"
---
# <a name="codepath"></a>CODE_PATH
메서드 또는 함수 호출을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>멤버
`bstrName`\
코드 경로의 이름입니다.

`pCode`\
합니다 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 함수 한 단계씩 코드에서 위치 식별 하는 개체입니다.

## <a name="remarks"></a>설명
이 구조는 함수를 한 단계씩 실행 구현 됩니다. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) 디버깅 중인 프로그램의 현재 위치에서 모든 호출을 반환 합니다. 이 구조는 이러한 한 번 호출을 나타냅니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
