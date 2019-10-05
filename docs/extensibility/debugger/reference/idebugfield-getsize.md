---
title: IDebugField::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db4ef8a41ec6759194cc35203b6458c7688f4322
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333197"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
이 메서드는 바이트에 있는 필드의 크기를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>매개 변수
`pdwSize`\
[out] 크기를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 모든 필드 형식이 있고 모든 형식 크기입니다. 예를 들어 바이트 형식의 필드에 1 바이트의 크기.

## <a name="see-also"></a>참고자료
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)