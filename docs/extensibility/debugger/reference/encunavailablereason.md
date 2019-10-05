---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7db94a181d87791edb242d69b461f90c42a5e080
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318152"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` 이유를 나타내는입니다 **편집 하며 계속 하기** 를 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>필드
`ENCUN_NONE`\
편집 하며 계속 사용할 수 없는 특정 이유가 없습니다.

`ENCUN_INTEROP`\
편집 하며 계속 사용할 수 없는 경우는 InterOp 호출 중

`ENCUN_SQLCLR`\
편집 하며 계속 하기 중 사용할 수 없는 공용 언어 런타임 (CLR)를 사용 하는 SQL 프로시저 호출을 합니다.

`ENCUN_MINIDUMP`\
편집 하며 계속 사용할 수 없는 경우 미니 덤프를 처리 하는 동안

`ENCUN_EMBEDDED`\
편집 하며 계속 사용할 수 없는 경우 포함 된 코드를 처리 하는 경우

`ENCUN_ATTACH`\
편집 하며 계속 사용할 수 없는 세션에 연결 된 경우 때문에 시작 되지 디버거에 의해 합니다.

`ENCUN_WIN64`\
편집 하며 계속 사용할 수 없는 경우 64 비트 Windows 코드를 처리 하는 동안

## <a name="remarks"></a>설명
이 열거형은 내부 용도로 여 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]입니다. 합니다 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) 하 고 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) 사용자 지정 포트 공급자에 의해 구현 된 메서드는 항상 반환 해야 `E_NOTIMPL`합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.idl

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
