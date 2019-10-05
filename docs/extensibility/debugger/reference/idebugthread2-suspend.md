---
title: IDebugThread2::Suspend | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc3abcc00d99e82a4af2e3886310772e47127274
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320005"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
스레드를 일시 중단합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>매개 변수
`pdwSuspendCount`\
[out] 일시 중단 작업 후 일시 중단 횟수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드를 호출할 때마다 0 위에서 일시 중단 횟수를 증가 시킵니다. 이 일시 중단 횟수가 표시 됩니다는 **스레드** 디버그 창입니다.

 이 메서드를 호출할 때마다, 이후의 호출 있어야 합니다 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드.

## <a name="see-also"></a>참고자료
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)