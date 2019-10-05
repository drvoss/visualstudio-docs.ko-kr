---
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5932535810f28e6f5da96ab69457f7364563d622
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325338"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
이 메서드는 세션에서 프로세스를 디버깅 이제는 프로세스에 알립니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>매개 변수
`pSession`\
[in] 이 프로세스에 연결 세션을 고유 하 게 식별 하는 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 인터페이스에 전달 된 `pSession` 쿠키를 고유 하 게이 프로세스에 연결 하 여 세션 디버그 관리자를 식별 하는 값으로 서만 처리할지 제공 된 인터페이스의 메서드는 작동 합니다.

## <a name="see-also"></a>참고자료
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)