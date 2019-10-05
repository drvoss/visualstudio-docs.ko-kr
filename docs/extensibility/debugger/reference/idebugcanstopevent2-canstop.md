---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab59cf5d077c4e397373c4c86b864ed17749fc19
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351264"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
현재 코드 위치에서 중지 하거나 계속 실행 여부는 디버그 엔진 (DE)에 알립니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>매개 변수
`fCanStop`\
[in] 0이 아닌 (`TRUE`)는 DE; 현재 코드 위치에서 중지 해야 하는 경우 0이 고, 그렇지 (`FALSE`).

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 이벤트의 수신기가 일반적으로 호출 합니다 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 는 DE 중지 하려는 이유를 확인 하는 방법 및 호출을 `IDebugCanStopEvent2::CanStop` 적절 한 응답을 사용 하 여 메서드.

 DE 중지 되 면 중지 이유를 설명 하는 이벤트를 보냅니다. 전송 된 사용자 또는 신호 중단 나타내는 두 이벤트는 일반적으로 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 인터페이스와 나타내는 중단점 이벤트를 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 인터페이스입니다.

## <a name="see-also"></a>참고자료
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)