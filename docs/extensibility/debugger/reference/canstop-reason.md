---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18861d7aa19281528e9a100f57399451194598a9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327245"
---
# <a name="canstopreason"></a>CANSTOP_REASON
프로그램 실행의 특정 지점에 도달한 후 실행을 중지할 수 있습니다 하는 경우를 결정 하는 데 사용 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>필드
`CANSTOP_ENTRYPOINT`\
지정 된 프로그램의 진입점을 지정합니다.

`CANSTOP_STEPIN`\
함수를 한 단계씩 실행을 지정 합니다.

## <a name="remarks"></a>설명
인수로 전달 된 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 프로그램의 진입점에 도달한 후 또는 함수나 메서드를 한 단계씩 실행 한 후 중지 하 되는 경우 세션 디버그 관리자 SDM (과)를 확인 하는 방법입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
