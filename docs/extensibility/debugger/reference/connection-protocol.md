---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f52ef7e723b583d593f6f0d4fc18f5f6909b131
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346528"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
디버그 패키지 (DE) 및 디버그 서버 간의 통신에 사용 되는 프로토콜을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>필드
`CONNECTION_NONE`\
서버에 없는 연결 되었습니다.

`CONNECTION_UNKNOWN`\
연결 된 내용이 있지만 알 수 없는 형식입니다.

`CONNECTION_LOCAL`\
로컬 서버 연결이입니다.

`CONNECTION_PIPE`\
명명 된 파이프를 통해 연결이 됩니다.

`CONNECTION_TCPIP`\
연결에서 TCP/IP를 사용 합니다.

`CONNECTION_HTTP`\
연결 (웹 서버)를 통해 HTTP를 사용합니다.

`CONNECTION_OTHER`\
다른 유형의 연결을 설정한 (이 값은 현재 사용 되지).

## <a name="remarks"></a>설명
이러한 값이 반환 된 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
