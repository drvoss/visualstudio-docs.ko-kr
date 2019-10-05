---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1b219973e0fced92a588a87ed472cf7a57d312d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337267"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
디버그 엔진 (DE)를 중지 하려고 하는 이유는 이유를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>매개 변수
`pcr`\
[out] 값을 반환 합니다 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 이 이벤트에 대 한 이유를 설명 하는 열거형입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 하기 전에이 메서드는 일반적으로 호출 합니다 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 메서드 호출자에 게는 0이 아닌 값을 전달할지 여부를 확인할 수 있습니다 (`TRUE`)에 `IDebugCanStopEvent2::CanStop` 메서드.

 중지 이유 일 수 있습니다 `CANSTOP_ENTRYPOINT`는 DE 즉 진입점에 도달 했습니다 또는 `CANSTOP_STEPIN`, 함수 한 단계씩에 DE 의미 합니다.

## <a name="see-also"></a>참고자료
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)