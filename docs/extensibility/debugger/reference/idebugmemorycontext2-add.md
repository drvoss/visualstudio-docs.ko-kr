---
title: IDebugMemoryContext2::Add | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c1cafbf22e51f867948491e2925c085bd387ea84
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347083"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
현재 컨텍스트에 지정된 된 값을 추가 하 고 새 컨텍스트를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>매개 변수
`dwCount`\
[in] 현재 컨텍스트에 추가할 값입니다.

`ppMemCxt`\
[out] 반환 된 새 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 메모리 컨텍스트 주소를 이므로 새 상황에 맞는 인터페이스를 필요로 하는 새 주소 생성 주소 값을 추가 합니다.

 항상이 메서드는 만들어진 주소 외부 메모리 공간이이 컨텍스트와 연결 된 경우에 새 컨텍스트를을 생성 해야 합니다. 새 컨텍스트에 없는 메모리를 할당할 수 있습니다 하거나이 유일한 예외는 `ppMemCxt` null 값인 경우 (즉, 오류).

## <a name="see-also"></a>참고자료
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)