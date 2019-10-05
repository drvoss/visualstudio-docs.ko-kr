---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c27ac3239fd6621a824f626a141a357241b03b1f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310567"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
디버그 엔진 (DE) 실행을 다시 시작할 때 디버깅 중인 프로그램에이 예외를 전달 하는 옵션을 지원 여부를 결정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>반환 값
 반환 `S_OK` (프로그램에 예외가 전달 수 있음) 또는 `S_FALSE` (예외 전달할 수 없습니다).

## <a name="remarks"></a>설명
 DE 디버기를 전달 하기 위한 기본 작업이 있어야 합니다. IDE 나타날 수는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트 및 호출 합니다 [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드를 호출 하지 않고는 `CanPassToDebuggee` 메서드. 따라서는 DE 여부 예외를 전달 하기 위한 기본 사례가 있어야 합니다.

## <a name="see-also"></a>참고자료
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)