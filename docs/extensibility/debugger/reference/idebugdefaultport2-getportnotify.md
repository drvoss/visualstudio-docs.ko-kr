---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd85f76ab0c882656ca79fe02296f30bdb83f523
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351770"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
이 메서드를 가져옵니다는 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 이 포트에 대 한 인터페이스입니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>매개 변수
`ppPortNotify`\
[out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 일반적으로 `QueryInterface` 구현 하는 개체에서 메서드를 호출 합니다 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 얻기 위해 인터페이스는 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 인터페이스입니다. 그러나 다른 개체에서 원하는 인터페이스를 구현 하는 경우가 있습니다. 이 메서드는 이러한 상황을 숨깁니다를 반환 합니다 `IDebugPortNotify2` 가장 적합 한 개체의 인터페이스입니다.

## <a name="see-also"></a>참고자료
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)