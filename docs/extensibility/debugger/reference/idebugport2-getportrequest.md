---
title: IDebugPort2::GetPortRequest | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: feaebf01b30876572ec0cbcf2bd33c141978fb26
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343728"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
(있는 경우) 포트를 만들려면 이전에 사용한 포트에 대 한 설명을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>매개 변수
`ppRequest`\
[out] 반환 된 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 포트를 만드는 데 사용 된 요청을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  반환 `E_PORT_NO_REQUEST` 포트를 사용 하 여 만들지 않은 경우는 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 포트 요청 합니다.

## <a name="see-also"></a>참고자료
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)