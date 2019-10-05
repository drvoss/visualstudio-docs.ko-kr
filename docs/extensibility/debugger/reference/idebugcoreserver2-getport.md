---
title: IDebugCoreServer2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59f4507f631887f8ffda37abec8b597087a0e57f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317809"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
특정 포트를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>매개 변수
`guidPort`\
[in] 검색할 포트의 GUID입니다.

`ppPort`\
[out] 반환 된 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 원하는 포트를 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_PORTSUPPLIER_NO_PORT` 주어진된 식별자를 사용 하 여 포트가 없는 경우.

## <a name="see-also"></a>참고자료
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)