---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ded3d31f9be2d0a02a238ead4bc989cc21b4922a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351819"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
보류 중인 중단점 조건 스타일을 지정 하 고 바인딩된 중단점.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>필드
`BP_COND_NONE`\
중단점의 위치에 도달 하면 중단점을 발생 시킵니다. 중단점 조건 지정 없습니다.

`BP_COND_WHEN_TRUE`\
중단점이 설정 된 조건식을 연결 하는 경우로 중단점이 발생 `true`합니다.

`BP_COND_WHEN_CHANGED`\
발생 조건 식의 값 중단점과 연결 된 경우에 중단점 이전 해당 평가에서 변경 되었습니다.

## <a name="remarks"></a>설명
에 사용 되는 합니다 `styleCondition` 의 멤버는 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 구조입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
